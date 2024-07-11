# Git-Guide-Project
A repo with instructions on how to use GitHub and GitLab that can be improved upon by the community.

This currently only contains one guide, setting up keys and connecting them to the remote hosts.

## Bootcampers Guide to Setting Up SSH Agent and Generating SSH Keys for GitHub and GitLab

This BOOTCAMPERS GUIDE will help you set up an SSH agent and generate SSH keys for use with GitHub and GitLab. The guide will provide step-by-step instructions for both Windows and Linux/Unix systems. It is assumed you have no prior knowledge of the subject.

## Table of Contents
- [Windows Setup](#windows-setup)
  - [Starting SSH Agent (Windows)](#starting-ssh-agent-windows)
  - [Generating SSH Keys (Windows)](#generating-ssh-keys-windows)
  - [Adding SSH Keys to GitHub and GitLab (Windows)](#adding-ssh-keys-to-github-and-gitlab-windows)
- [Linux/Unix Setup](#linuxunix-setup)
  - [Starting SSH Agent (Linux/Unix)](#starting-ssh-agent-linuxunix)
  - [Generating SSH Keys (Linux/Unix)](#generating-ssh-keys-linuxunix)
  - [Adding SSH Keys to GitHub and GitLab (Linux/Unix)](#adding-ssh-keys-to-github-and-gitlab-linuxunix)


# Introduction

    **Explanation:** SSH (Secure Shell) keys allow you to securely connect to your GitHub and GitLab accounts without repeatedly entering your username and password. We'll use the Git Bash terminal on Windows and the terminal on Linux/Unix systems.

# Windows Setup

## Starting SSH Agent (Windows)

1. **Open Git Bash Terminal:**
   - Open VS Code.
   - Press [Ctrl + `] (backtick) to open the integrated terminal. You can also access the terminal from the header menu in VS Code.
   - Type `bash` and press `Enter` to switch to Git Bash if it is not already selected. You can also create a new bash terminal by clicking the plus sign in the upper-right corner of the terminal menu.

2. **Start the SSH agent:**
   ```bash 
   eval $(ssh-agent -s)


    **Explanation:** - These two lines set the necessary environment variables and start the SSH agent.

## Generating SSH Keys (Windows)

1. **Generate a new SSH key:**
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
    ```
   - **Explanation**: This command generates a new SSH key using the Ed25519 algorithm, which is more secure and faster. Replace - "your_email@example.com" with your email address and do not use quotation marks. 


    Save the key and set a passphrase:

    When prompted to "Enter a file in which to save the key," **press Enter to accept the default location**.
    When prompted to "Enter passphrase," type a secure passphrase. You can leave it empty, but it is recommended to use a passphrase for added security.

    **STUDENT NOTE:**
    It is okay to create SSH keys without passwords, but it is **NOT** best practice, especially when dealing with sensitive information. For simplicity while learning, it is recommended to start without a passphrase. However, different organizations will require you to periodically create new SSH keys when you work with their data in the future.

## Locating Your SSH Keys and Folder (Windows)

    After generating your SSH keys, you can find them in the default directory where SSH keys are stored.

1. **Open Git Bash Terminal:**
   - Open VS Code.
   - Press `Ctrl+` ` (backtick) to open the integrated terminal.
   - Type `bash` and press `Enter` to switch to Git Bash if it is not already selected.

2. **Navigate to the `.ssh` directory:**
   ```bash
   cd ~/.ssh
   ```
   - **Explanation:** This command **change**s the current **directory** to the .ssh directory, which is where your SSH keys are stored.

3. List the files in the .ssh directory:
    ```bash
        ls
    ```
    - **Explaination:** This command lists all the files in the .ssh directory. You should see your SSH key files, such as **id_ed25519** and **id_ed25519.pub**.

4. Read the contents of the .pub file to find your public SSH key from the pair.  The command below will tell you what is inside of the id_25519.pub file. 
   
   ```bash
    cat id_ed25529.pub
    ```

    If you want to view the files you have created in a Windows explorer window, in your Git Bash Terminal, type the following command:

    ```bash
    explorer.exe .
    ```

   - **Explanation:** This command opens the current directory (which should be .ssh) in File Explorer, allowing you to view your SSH key files in a graphical interface.


## Adding SSH Keys to GitHub and GitLab (Windows)

    Once you've generated your SSH keys, you need to add them to your GitHub and GitLab accounts to enable secure access.

1. **Copy your SSH key to the clipboard:**

   ```bash
   cat ~/.ssh/id_ed25519.pub | clip
    ```

   - **Explanation:** This command displays your public key and copies it to the clipboard.


2. **Add your SSH key to GitHub:**

    - Go to GitHub and log in.
    - Navigate to Settings by clicking on your profile picture in the upper right corner and selecting Settings.
    - In the left sidebar, click on SSH and GPG keys.
    - Click the New SSH key button.
    - Paste your key into the "Key" field and give it a descriptive title.
    - Click Add SSH key.
  

3. **Add your SSH key to GitLab:**

    - Go to GitLab and log in.
    - Navigate to your profile settings by clicking on your profile picture in the upper right corner and selecting Settings.
    - In the left sidebar, click on SSH Keys.
    - Paste your key into the "Key" field and give it a descriptive title.
    - Click Add key.
  
# Linux/Unix Setup

## Starting SSH Agent (Linux/Unix)

1. **Open Terminal:**
   
   - Open your terminal application.

2. **Start the SSH agent:**
   
   ```bash
   eval "$(ssh-agent -s)"
   ```

   - **Explanation:** This command starts the SSH agent and sets the necessary environment variables.

## Generating SSH Keys (Linux/Unix)
   
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   - **Explanation:** This command generates a new SSH key using the Ed25519 algorithm, which is more secure and faster. Replace `"your_email@example.com"` with your email address.
  

## Save the key and set a passphrase (Linux/Unix)
   
   - When prompted to "Enter a file in which to save the key," press `Enter` to accept the default location.
   - When prompted to "Enter passphrase," type a secure passphrase. You can leave it empty, but it is recommended to use a passphrase for added security.
   - **STUDENT NOTE:**
    It is okay to create SSH keys without passwords, but it is **NOT** best practice, especially when dealing with sensitive information. For simplicity while learning, it is recommended to start without a passphrase. However, different organizations will require you to periodically create new SSH keys when you work with their data in the future.
  

## Add your SSH key to the SSH agent (Linux/Unix)
   
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

   - **Explanation:** This command adds the SSH private key to the SSH agent so that it can manage your keys.
  

## Adding SSH Keys to GitHub and GitLab (Linux/Unix)

1. **Copy your SSH key to the clipboard:**
   
   ```bash
   cat ~/.ssh/id_ed25519.pub | xclip -sel clip
   ```

   - **Explanation:** This command displays your public key and copies it to the clipboard using `xclip`.
  

2. **Add your SSH key to GitHub:**
   
   - Go to [GitHub](https://github.com) and log in.
   - Navigate to **Settings** by clicking on your profile picture in the upper right corner and selecting **Settings**.
   - In the left sidebar, click on **SSH and GPG keys**.
   - Click the **New SSH key** button.
   - Paste your key into the "Key" field and give it a descriptive title.
   - Click **Add SSH key**.


3. **Add your SSH key to GitLab:**
   - Go to [GitLab](https://gitlab.com) and log in.
   - Navigate to your profile settings by clicking on your profile picture in the upper right corner and selecting **Settings**.
   - In the left sidebar, click on **SSH Keys**.
   - Paste your key into the "Key" field and give it a descriptive title.
   - Click **Add key**.


# STUDENT NOTE:
It is okay to create SSH keys without passwords, but it is **NOT** best practice, especially when dealing with sensitive information. For simplicity while learning, it is recommended to start without a passphrase. However, different organizations will require you to periodically create new SSH keys when you work with their data in the future.
