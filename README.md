# NGSS Skills & Question Generation Pipeline

This project implements an automated workflow that converts NGSS-aligned instructional text into structured skills and assessment questions using AWS Bedrock models. The system produces schema-validated JSON outputs that can be used in curriculum platforms, RAG systems, or AI-powered learning tools.

---

## Overview

The pipeline transforms raw NGSS text into two structured artifacts:

* **Skills JSON** – Extracted, standardized skills aligned to NGSS
* **Questions JSON** – Assessment questions generated from those skills

The workflow is modular and enforces strict JSON schema validation to ensure consistent downstream integration.

---

## Architecture

### 1. Input NGSS Text

* Accepts raw NGSS-aligned instructional text
* Can be triggered manually or via schedule

### 2. Skill Generation

* AWS Bedrock chat model extracts skills
* JSON Schema Parser validates structured output
* Produces standardized skills JSON

### 3. Question Generation

* Second Bedrock model generates assessment questions from skills
* Questions JSON Parser enforces schema compliance
* Maintains alignment between skills and generated items

### 4. JSON Conversion

* Converts model output into strict JSON format

### 5. File Output

* Writes validated JSON files to disk
* Output is ready for:

  * Retrieval-Augmented Generation (RAG)
  * Curriculum management systems
  * Content pipelines
  * Educational AI tools

<img width="1696" height="745" alt="image" src="https://github.com/user-attachments/assets/2b25e038-1ee7-4f39-b06f-57bad0bcd139" />

---

## Key Features

* Modular LLM-based generation (Skills → Questions)
* Schema-enforced structured outputs
* Automated execution via schedule or manual trigger
* AWS Bedrock integration
* Scalable curriculum content generation

---

## Tech Stack

* AWS Bedrock (LLM inference)
* JSON Schema validation
* Workflow automation engine
* Local file storage (JSON outputs)

---

## Use Case

Designed for AI-powered curriculum systems that require:

* Structured NGSS skill extraction
* Automatically generated aligned assessments
* Machine-readable content for downstream AI applications

---

## Example Output Structure

```json
{
  "standard": "MS-PS1-1",
  "skills": [
    {
      "skill_id": "S1",
      "description": "Develop and use models to describe atomic composition."
    }
  ],
  "questions": [
    {
      "question_id": "Q1",
      "skill_id": "S1",
      "type": "multiple_choice",
      "prompt": "Which statement best describes atomic structure?",
      "options": ["A", "B", "C", "D"],
      "answer": "A"
    }
  ]
}
```

---

## Future Improvements

* Add automated evaluation of question quality
* Implement feedback loop for iterative refinement
* Support additional standards beyond NGSS
* Integrate directly with vector databases for RAG

