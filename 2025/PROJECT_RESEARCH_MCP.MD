# Ultra-Think MCP Server Task for Claude

You are an advanced Claude Code agent tasked with writing a comprehensive **MCP (Model Context Protocol) server app** that manages a **Git-based notes repository**. The server must perform the following tasks efficiently and robustly:

## 🏗️ Functionality Requirements

1️⃣ **Check for Remote Updates**  
- The MCP server must connect to the `GITHUB_REPO` configured via environment variables.  
- It should check if there are any new updates to pull from the remote repo and perform the pull operation if needed.  

2️⃣ **Push Local Updates**  
- After modifications are made in the local `./repos/notes` directory (this includes notes, projects, and research), the MCP server must add, commit (with a unique UUID and structured message), and push these changes to the remote GitHub repo.

3️⃣ **Structured Research Workflow**  
When a project or topic requires research or planning:
- Create a new folder in `./repos/notes/projects/YYYYMMDD_HHMM_<topic>`.
- In this folder, create a **markdown file** (`YYYYMMDD_HHMM_<topic>.md`) that contains:
  - General research on the topic, written by you as the agent.
  - A multi-step plan with detailed prompts for implementing the topic or idea.
  - Include **specific code examples and architectures** as Markdown code blocks.
  - Add clear **metadata**: tags, `updated_at`, author, status, etc.
- Use the MCP server to push these files to the repo with a structured commit message.

4️⃣ **Notes Management**  
- When adding or updating a note, interpret the provided text and write a new markdown note inside `./repos/notes/notes/YYYYMMDD_HHMM_<topic>.md`.  
- Include structured metadata (tags, `updated_at`, etc.) and commit/push the changes.

5️⃣ **Research Folder for Focused Topics**  
- For a deep-dive research task, create a new folder in `./repos/notes/research/YYYYMMDD_HHMM_<topic>`.
- Generate a markdown file with all the research information you can find or synthesize.
- Push the changes via Git with structured metadata.

6️⃣ **Git Push After Each Action**  
- After every discrete action (adding a note, creating a research file, generating project plans), immediately push all changes to the remote GitHub repo.

## 🧪 Testing Framework  
Before implementing any logic, you must:
- Create a **comprehensive automated test framework** for the MCP server.
- Ensure the tests verify functionality for:
  - Git pull operations.
  - File creation and correct formatting.
  - Commit structure validation (UUIDs, metadata).
  - Push operations and Git integrity.
- The framework should run automatically **before every action** the server performs.
- Tests should cover edge cases and simulate potential errors.

## 📚 Documentation & Workflow Instructions  
- Write **comprehensive documentation** that explains:
  - How the MCP server works.
  - The intended user workflow:
    - How to create research folders and generate structured research plans.
    - How to add or update notes.
    - How to push changes.
    - The purpose and structure of each folder (`projects`, `research`, `notes`).
  - Describe the intended **commit structure** with UUIDs and useful metadata.
  - Include examples of commit messages and file structures.
  - Emphasize how the agent should minimize direct code changes by using prompts and documentation.

## 🌐 Persistent, Automatic Workflow (Critical)  
This entire system must be designed as a **permanent new workflow/feature** of Claude Code.  
- **I do not want to explain, reconfigure, or manually trigger this process every time.**  
- Once built, this MCP server and its automated workflow should run **automatically** whenever a project, research, or note task arises, without requiring me to repeat the workflow.  
- It should integrate seamlessly into Claude Code’s standard functionality, acting as a built-in capability.  
- The system must **retain the original configuration (GITHUB_REPO, folder structures, etc.)** and assume these defaults unless explicitly changed later.  

## 🎯 Output Expectations  
- Produce a complete **Python file** (`mcp_server.py`) containing the MCP server logic.  
- Create a **test suite** (`test_mcp_server.py`) to validate its functionality.  
- Generate a **README.md** with detailed instructions, workflow, examples, and explanations.  
- Use **Python GitPython** for Git operations.  
- All files must be ready for use in the specified directory structure.  

### 🌈 Important Instructions  
- Ensure **consistency in file and folder naming** using `YYYYMMDD_HHMM_<topic>`.  
- Include **comprehensive metadata** in all markdown files.  
- Avoid modifying the MCP server’s core unless absolutely necessary—prefer using clear documentation and prompts.  
- Run the test suite every time you make changes to ensure stability.  
- **Make this a fully automated, persistent feature of Claude Code itself.**

**Input Variables:**  
- `GITHUB_REPO` – URL of the remote Git repository (environment variable).  
- `GIT_USERNAME`, `GIT_API` – GitHub authentication credentials.

### 🧠 Additional Guidance  
- Focus on modular, maintainable code.  
- Use clear and concise function names.  
- Document every function with purpose and expected behavior.  
- Provide sample outputs and workflows in the README.

Your task is to deliver a robust, production-ready MCP server with a complete workflow, testing infrastructure, and **zero manual reconfiguration after initial setup**.
