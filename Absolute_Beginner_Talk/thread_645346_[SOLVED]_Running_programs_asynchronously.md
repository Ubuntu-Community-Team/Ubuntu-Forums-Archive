---
title: "[SOLVED] Running programs asynchronously?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by AaronLS on 2007-12-19
Since I've figured out how to use X Windows, I've been annoyed by the fact that my ssh terminal blocks when I run a X Window app.  I.E. if I run gedit, when I go back to my terminal, I can not close the command prompt until I close gedit.  It hasn't really been a problem since I can open tabs in gnome-terminal.  I just wondered if there was a way to spawn the window or program without waiting for the program to close so that my terminal is freed up.

I just set a F.E.A.R. dedicated game server, and when I run start.sh, it does the same thing, even though it is not a x windows app.  How does this effect something where I might run something from a script?  I.E. if I put a script in init.d to start my F.E.A.R. server up on bootup, is the script going to hang and cause any weirdness since it would run the server, but the command to run the server would not return immidietely?

Thanks.

---

### Post by Severun on 2007-12-20
The problem is that when you ssh to the remote machine you start a shell.  Then when you run gedit, it is a child process under the shell you started with ssh.  You should exit the ssh or close the terminal, but any child process started under the parent shell would also exit.

You can also use the command nohup.  This will cause  a process to continue running even if the parent shell that started it or your ssh connection dies.

Something like 

nohup gedit &

Will cause gedit to start up but continue to run even if the shell that starts it goes away.  The ampersand "&" puts it in the background so you get a prompt back after you start gedit.

---

### Post by AaronLS on 2007-12-21
Thanks.  Let me make sure I understand the "terminal"ogy (haha, I made a geeky pun, terminal/terminology).

Your first example is just closing the ssh client or terminal.  In this case, the shell will continue to run, and thus the child processes will continue to run, correct?

In the second example, you use nohup and & to run the app in the background.  I read up on that command and it all makes sense.

> **Severun said:**
> This will cause  a process to continue running even if the parent shell that started it or your ssh connection dies.

This makes me wonder what happens to programs I have running if I just kill my SSH connection by closing the client(it always prompts me something like, "You are currently connected, are you sure you want to exit").  Will the shell eventually die, killing my programs?  Should I be issuing a logout command instead of just closing my terminal?

How does this relate to the separate tabs in gnome-terminal?  Is each tab considered a "shell" such that closing a tab will close the program I have running under it?  Or is there one shell shared between the tabs?

I understand my best bet is to use the nohup to start the processes in the background, but it would be nice to have a more detailed understanding.

---

