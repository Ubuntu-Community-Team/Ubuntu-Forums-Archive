---
title: "another newbie question about terminal"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-05-23
if you run a command for something followed by something that it doesn't accept (like "cowsay" and then a blank), then that bit of text showing the host and your current location disappears, and the response to whatever you type is just a line feed.  is it that the program is running in the terminal?

Is there any elegant way of "getting back to normal" short of closing the terminal window?

thanks

---

### Post by ruy_lopez on 2007-05-23
Ctrl c is the interrupt key combination, for when a process takes over your terminal.

---

### Post by ruy_lopez on 2007-05-23
I should add, if "Ctrl c" doesn't work, you can just close the terminal. Most executables are associated with their controlling terminal. So if you just close the terminal and open up a new one, the process should be gone. (in 99% of cases)

---

### Post by xtang on 2007-05-23
k thanks

---

### Post by hartz on 2007-05-24
I have been reading and re-reading your question.

I think I can maybe add something of value.

Lets say you run a command in the terminal.

You get a "prompt", you enter the command and press enter.
You will get a prompt again when the command finishes.

However, maybe you run, say for example
```
sudo synaptic
```

Now you will not get the prompt back until you press Ctrl-C to terminate synaptic, or exit from synaptic.

However, you can press Ctrl-Z.
This will do two things: It will "freeze" the synaptic application, and it will present you with a new prompt in the terminal.
You should run the command "bg" right-away as Synaptic might be communicating on the network or whatever, so leaving it in a frozen state is not ideal.  Running "bg" will allow it to continue running in the background.  bg by default applies to the most recent command that you "stopped" (pleaced in frozen state using Ctrl-Z).

There is one other way to place commands into the background, but it is not useful in conjunction with sudo.

If you enter a command such as "oowriter" or "gedit myfile", you can append an ampersand (&) to the end of the command.  This will start the command process in the background automatically and present a new prompt without waiting for the command to finish.

These two things, bg and using & to run commands in the background, are often referred to as "job control".

The "jobs" command will tell you what commands are running and/or stopped in the background.

When a background command finishes, you will get a message about that the next time a command prompt is displayed.

One other thing which is sometimes usefull is the fg command.

You could for example run a command, then use Ctrl-Z and bg, run a few other commands, and then to allow that background job to once again get access to the terminal, you can use "fg".  This is usefull if you for example accidentally use sudo somecommand & ... Sudo wants to prompt for a password, but the & has placed it in the background, so now it is waiting for a password in the background.  In order to interact with it once more, issue "fg".

And that is job control - Q.E.D.

---

