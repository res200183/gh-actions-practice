🚀 GitHub Actions Practice (Steps)

This repository is a hands-on practice of GitHub Actions at a DevOps level.

---

📌 Goal

Learn and understand:

- What a Step is
- Difference between "run" and "uses"
- Execution order
- Passing data between steps ("outputs")
- Conditional execution ("if")

---

⚙️ Structure

- Workflow → full pipeline
- Job → group of steps
- Step → single action (atomic unit)

---

🔧 Example Workflow

name: My First Pipeline

on:
  push:

jobs:
  test-job:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate value
        id: gen
        run: echo "num=5" >> $GITHUB_OUTPUT

      - name: Use value
        run: echo "Value is ${{ steps.gen.outputs.num }}"

      - name: Conditional step
        if: steps.gen.outputs.num == '5'
        run: echo "Condition matched"

---

🧠 Key Concepts

1. Step

The smallest execution unit in a pipeline.

---

2. run vs uses

- "run" → executes shell commands
- "uses" → uses prebuilt actions

---

3. Outputs

Passing data between steps:

echo "key=value" >> $GITHUB_OUTPUT

Usage:

${{ steps.step_id.outputs.key }}

---

4. Conditions (if)

if: steps.gen.outputs.num == '5'

- true → step runs
- false → step is skipped

---

5. Execution Order

Steps run:
➡️ strictly from top to bottom

---

6. Errors

- If a step fails → the job fails
- Can ignore errors:

continue-on-error: true

---

🔥 Practice Covered

You implemented:

- Code checkout
- Running commands
- Passing data between steps
- Conditional logic

---

💡 Takeaway

A Step is:

- the atomic unit of CI/CD
- the building block of pipelines
- how logic is constructed

---

📚 Next Steps

- AWS deployment via CLI
- Full CI/CD (build → test → deploy)
- Secrets management
- Docker + GitHub Actions

---

🏁 Result

Now you can:

- read logs
- debug pipelines
- build basic CI/CD logic

👉 This is already Junior DevOps level
