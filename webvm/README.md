# WebVM Terminal - Browser-Based Virtual Machine

A complete virtual machine running entirely in your browser using WebAssembly! Features user authentication, Python runtime, full filesystem, and text editor - all with classic terminal aesthetics.

## 🔐 **NEW: User Accounts & Authentication**

- **Create Account**: Sign up with username and password
- **Secure Login**: Simple hash-based authentication
- **Per-User Sessions**: Each user has their own isolated filesystem
- **Auto-Save**: Files automatically persist to your account
- **Session Restore**: Pick up exactly where you left off
- **Logout**: Clean session management

## 🎨 **Classic Terminal Theme**

- Pure black background (#000000)
- Classic green text (#00ff00)
- Retro terminal aesthetics
- Clean, minimalist interface
- Just like the real thing!

## 🚀 Features

### ✏️ **Built-in Text Editor**
- Full-screen code editor with line numbers
- Keyboard shortcuts:
  - `Ctrl+S` - Save file
  - `Ctrl+X` - Exit (prompts to save if modified)
  - `Ctrl+H` - Show help
- Real-time line/column position
- Auto-creates new files if they don't exist
- Terminal-themed UI

### 📁 **File System Operations**
- `ls [dir]` - List directory contents
- `cd <dir>` - Change directory
- `pwd` - Print working directory
- `cat <file>` - Display file contents
- `edit <file>` - Open file in built-in editor
- `touch <file>` - Create empty file
- `mkdir <dir>` - Create directory
- `rm <path>` - Remove file or directory
- `cp <src> <dst>` - Copy file or directory
- `mv <src> <dst>` - Move/rename file or directory

### 🔍 **Search & Display**
- `grep <pattern> <path> [-r]` - Search for pattern in files
- `tree [dir]` - Display directory tree structure

### 🐍 **Python Runtime**
- `python <file>` - Execute Python files
- `python` - Interactive Python REPL
- `pip install <package>` - Install Python packages from PyPI
- Full Python 3.10+ environment running in WASM

### 🌐 **Network Features**
- `wget <url> [filename]` - Download files from the internet

### 👤 **Authentication Commands**
- `whoami` - Display current username
- `logout` - Sign out (auto-saves your session)

### 📝 **Other Commands**
- `echo <text>` - Print text (supports `>` and `>>` redirection)
- `history` - Show command history
- `clear` - Clear terminal
- `help` - Show comprehensive help

## 🎯 Quick Start

1. Open `index.html` in your browser
2. **Create an account** or login
3. Wait for Pyodide to load (~10 seconds)
4. Start typing commands!

### First Time Setup:
```bash
# 1. Open the page
# 2. Click "SIGN UP"
# 3. Enter username (min 3 chars) and password (min 4 chars)
# 4. Click "LOGIN" with your credentials
# 5. Welcome to your personal terminal!
```

### Try these commands:
```bash
# See who you are
whoami

# List files
ls

# Edit a Python file
edit hello.py

# Run the file
python hello.py

# View directory tree
tree

# Search for text
grep print . -r

# Download a file from the internet
wget https://raw.githubusercontent.com/python/cpython/main/README.rst

# When you're done
logout
```

## 🛠️ Technical Architecture

### Stack
- **Terminal**: xterm.js - Professional terminal emulator
- **Python Runtime**: Pyodide - CPython compiled to WebAssembly
- **Filesystem**: Emscripten's MEMFS - Memory-backed POSIX filesystem
- **Storage**: localStorage for user accounts and sessions
- **Isolation**: Complete sandbox - zero access to host system

### Authentication
- Simple client-side hash for password storage
- User data stored in browser localStorage
- Each user gets isolated filesystem
- Sessions auto-save on logout and page unload

### How It Works

1. **User Login**: Authenticate and load user's saved session
2. **WebAssembly Execution**: Python runs via Pyodide
3. **Virtual Filesystem**: Completely isolated, memory-backed filesystem
4. **Per-User Persistence**: Each account has separate file storage
5. **Auto-Save**: Changes automatically saved to localStorage

## 📚 User Account System

### Account Management
- Minimum username length: 3 characters
- Minimum password length: 4 characters
- Passwords are hashed before storage
- Each user has completely isolated filesystem
- No server required - all client-side

### Session Persistence
Your files are automatically saved:
- When you run Python files
- When you edit and save files
- When you logout
- When you close the browser tab

Next time you login, everything is exactly as you left it!

## 🎨 Terminal Theme

Classic hacker terminal aesthetic:
- Black background
- Bright green text
- Monospace font (Courier New)
- Minimal UI elements
- Clean borders
- Retro feel

## 🌟 Use Cases

- **Learning Python** - Practice in a safe, isolated environment
- **Code Experimentation** - Test ideas without affecting your system
- **Teaching** - Demonstrate programming concepts
- **Portable Development** - Code anywhere, no installation needed
- **Multi-User Systems** - Each person has their own account
- **File Management Practice** - Learn Unix commands safely

## 🔒 Security & Privacy

- ✅ Complete isolation from host filesystem
- ✅ Runs in browser WASM sandbox
- ✅ No server-side execution
- ✅ All data stored locally in your browser
- ✅ Each user's files are separate
- ✅ Safe to run untrusted code (in the VM context)
- ⚠️ Passwords stored in localStorage (client-side only)

## 📦 File Size

- HTML: ~60KB (uncompressed)
- Dependencies (CDN):
  - xterm.js: ~200KB
  - Pyodide: ~6MB (cached after first load)

## 🎓 Example Workflows

### Create Your First Program
```bash
# Login to your account
# Then:

edit calculator.py
# (Write your code in the editor)
# Press Ctrl+S to save
# Press Ctrl+X to exit

python calculator.py
```

### Multi-User Collaboration
```bash
# User 1 creates account "alice"
# User 2 creates account "bob"
# Each has completely separate filesystem
# Perfect for teaching or shared computers
```

### Data Processing
```bash
# Download data
wget https://example.com/data.csv

# Process it
edit process.py
python process.py

# Results are saved to your account!
```

## 🎮 Commands Reference

### Authentication
```bash
whoami              # Show current user
logout              # Sign out (saves session)
```

### File Operations
```bash
ls [dir]           # List directory
cd <dir>           # Change directory
pwd                # Print working directory
cat <file>         # Display file
edit <file>        # Edit file
touch <file>       # Create file
mkdir <dir>        # Create directory
rm <path>          # Remove file/dir
cp <src> <dst>     # Copy
mv <src> <dst>     # Move/rename
```

### Python
```bash
python <file>      # Run Python file
python             # Start REPL
pip install <pkg>  # Install package
```

### Utilities
```bash
grep <pattern> <path> [-r]  # Search files
tree [dir]                  # Show tree
history                     # Command history
wget <url> [file]          # Download
echo <text>                # Print (supports >)
clear                      # Clear screen
help                       # Show help
```

## 🚧 Future Enhancements

- Syntax highlighting in editor
- Shared folders between users
- Export/import sessions
- File upload from host
- Tab completion
- Command history with arrow keys
- More language runtimes

## 🙏 Credits

Built with:
- [xterm.js](https://xtermjs.org/) - Terminal emulator
- [Pyodide](https://pyodide.org/) - Python in WebAssembly
- Classic terminal aesthetics ❤️

---

**Your personal terminal, in your browser!** 🖥️

Create an account and start coding!
