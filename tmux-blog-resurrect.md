---

### **Tmux-Resurrect – Keep Your Sessions Alive**

#### **Introduction: Up and Running with Tmux-Resurrect**

When working in tmux, it’s common to have multiple windows and panes open, each running different tasks. What happens when your system unexpectedly shuts down or your tmux session crashes? Recreating all those windows, panes, and running commands can be a hassle. This is where **tmux-resurrect** comes in.

**Tmux-resurrect** saves the exact state of your tmux sessions—down to the window layout, running programs, and directories—allowing you to restore everything exactly as it was after a restart or crash.

In this post, we’ll explore how tmux-resurrect works, how to install it, and when to use it versus tmuxinator.

---

### **What is Tmux-Resurrect?**

**Tmux-resurrect** is a plugin for tmux that allows you to save and restore your entire tmux session. Whether you experience a system crash or reboot, tmux-resurrect ensures that your sessions—including windows, panes, commands, and working directories—are preserved and restored with ease.

#### **Why Use Tmux-Resurrect?**

- **Preserve your workflow**: Instead of manually reopening windows, panes, and running commands after a restart, tmux-resurrect brings everything back as it was.
- **Recover from crashes**: When tmux crashes or your terminal closes unexpectedly, tmux-resurrect can restore your previous setup effortlessly.
- **Save time**: It saves you from the tedious process of manually recreating your environment.

---

### **Setting Up Tmux-Resurrect**

Installing tmux-resurrect is simple and can be done using the **Tmux Plugin Manager (TPM)**.

#### **Step 1: Install Tmux Plugin Manager (TPM)**

If you don’t already have TPM installed, you can install it by adding the following to your `~/.tmux.conf`:

```bash
set -g @plugin 'tmux-plugins/tpm'
```

Then run the following commands in tmux:

```bash
# Press prefix + I to install TPM
tmux source-file ~/.tmux.conf
```

#### **Step 2: Install Tmux-Resurrect**

With TPM installed, you can now add tmux-resurrect by updating your `~/.tmux.conf` again:

```bash
set -g @plugin 'tmux-plugins/tmux-resurrect'
```

To install the plugin, run:

```bash
# Press prefix + I to install tmux-resurrect
```

#### **Step 3: Save and Restore Sessions**

Once installed, you can easily save and restore your tmux sessions.

- **Save a session manually**:
  ```bash
  prefix + Ctrl-s
  ```

- **Restore a session**:
  ```bash
  prefix + Ctrl-r
  ```

Now, whenever you save a session with `prefix + Ctrl-s`, tmux-resurrect records the layout, panes, windows, and even the running commands. After a reboot or crash, you can restore everything exactly as it was using `prefix + Ctrl-r`.

---

### **Functionality of Tmux-Resurrect**

Tmux-resurrect excels at preserving your entire tmux environment. Here’s what it saves and restores:

- **Window layout**: It records how your panes and windows are laid out (vertical, horizontal splits, etc.).
- **Running programs**: Tmux-resurrect keeps track of what programs are running in each pane (e.g., `vim`, `htop`, `rails server`, etc.).
- **Working directories**: Each pane’s working directory is remembered and restored.
- **Shell history**: It restores the history of commands that were previously entered into each pane.

#### **Working with Tmux-Continuum**

If you want an automated way to save your sessions periodically, **tmux-continuum** is a companion plugin that extends tmux-resurrect’s functionality. Tmux-continuum automatically saves your tmux sessions at regular intervals, ensuring your work is always backed up.

#### **Installing Tmux-Continuum**

To install tmux-continuum, add the following to your `~/.tmux.conf`:

```bash
set -g @plugin 'tmux-plugins/tmux-continuum'
```

Then run:

```bash
# Press prefix + I to install tmux-continuum
```

Once installed, tmux-continuum will automatically save your tmux sessions without you needing to manually trigger a save. You can adjust the save intervals or trigger automatic restores with additional configuration.

---

### **Tmuxinator vs Tmux-Resurrect: Key Differences**

At this point, you might be wondering when to use **tmux-resurrect** versus **tmuxinator**. While both are excellent tools for managing tmux sessions, they serve very different purposes:

- **Tmux-resurrect** is ideal for recovering your current session after an unexpected system crash or reboot. It restores your **existing** setup as it was when you saved it.
  
- **Tmuxinator**, on the other hand, is built for automating the **initial setup** of tmux sessions based on predefined configurations. You can use it to quickly start project-specific environments with customized layouts, panes, and commands, but it won’t save running programs or session states.

#### **Key Differences at a Glance**:

| Feature              | Tmuxinator                                        | Tmux-resurrect                                  |
|----------------------|--------------------------------------------------|------------------------------------------------|
| **Purpose**           | Automate setup of new tmux sessions              | Save and restore tmux session states           |
| **Use Case**          | Starting predefined environments for projects    | Restoring current session state after crashes  |
| **What it Saves**     | Window layouts, panes, commands to run           | Window layouts, panes, running programs        |
| **Best for**          | Automating repetitive project setups             | Recovering work after interruptions            |

**Example**: If you’re working on a coding project, you might use **tmuxinator** to open your development environment with multiple windows (editor, server, logs). But if you need to reboot your system during the day, **tmux-resurrect** will ensure your exact working state is saved and restored.

---

### **Real-World Example: Using Tmux-Resurrect**

Let’s say you’re working on a server configuration, with multiple panes open:
1. **Pane 1**: Running `vim` to edit a configuration file.
2. **Pane 2**: Monitoring server logs using `tail -f`.
3. **Pane 3**: Running `htop` to monitor system performance.

If you reboot your system, all this will be lost unless you manually save the state. With tmux-resurrect, pressing `prefix + Ctrl-s` saves everything. After rebooting, you simply run `prefix + Ctrl-r`, and all three panes are restored—right down to `vim` being open in Pane 1, your logs still running in Pane 2, and `htop` open in Pane 3.

---

### **Recap: Why Use Tmux-Resurrect?**

- **Tmux-resurrect** is the ultimate tool for saving and restoring tmux sessions. It gives you peace of mind that no matter what happens—whether it’s a system crash, terminal closure, or accidental reboot—your tmux environment can be restored quickly and easily.
- Combine **tmux-resurrect** with **tmux-continuum** for automated, periodic backups of your tmux session.

Whether you’re a sysadmin juggling multiple terminal windows or a developer working on complex projects, tmux-resurrect ensures you don’t lose your progress.

---

That wraps up our exploration of **tmux-resurrect**. In the next post, we’ll look at even more advanced tmux plugins and tools to help you boost your productivity.

---
