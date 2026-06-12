---
title: "Launcher for command silently exits"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by steenbras on 2007-12-12
I'm struggling to get a command to stay running from the launcher. I want to open an ssh tunnel to a server, and have it run in the background (i.e. not in a terminal).

Here's the command I want to run:
```

ssh -l username -L 7777:targetmachine.com:22 gateway.com cat -
```

The cat - is a non-finishing command which should keep the ssh process running. But it will only stay open if I configure the launcher to be an application terminal - it exits after prompting me for a password if I run it as a terminal.

I've tried specifying the command explicitly as above, and as a bash script containing the following
```
#!/bin/bash
ssh -l username -L 7777:targetmachine.com:22 gateway.com cat -
```

Neither will work for an application type launcher.

Suggestions, please?

---

### Post by jw5801 on 2007-12-12
Try putting an ampersand after the command. This causes the command to run in the background if executed in a terminal.

```
#!/bin/bash
ssh -l username -L 7777:targetmachine.com:22 gateway.com cat - &
```

You can then close the terminal with a simple "exit" and continue on your merry way with the process running. If you don't close the terminal gracefully (ie. by clicking the x in the top right hand corner rather than typing exit or hitting ctrl+d), however, the background process will also be killed.

---

### Post by steenbras on 2007-12-13
Thanks, jw5801, but what I'm after is for the ssh process to run outside of a terminal, and to stay running.

I can get it running in a terminal window no problem. But if I set the launcher properties to run as an application it prompts me for the password to the gateway machine, then exits.

---

### Post by anewguy on 2007-12-13
Cron??????

---

### Post by steenbras on 2007-12-13
The problem with a cron job is the need to provide a password. I don't like doing that on a command line since a ps will reveal my password.

---

### Post by rax_m on 2007-12-13
Hi, 

Try adding the nohup command to the beginning of the command like so :

```

nohup ssh -l username -L 7777:targetmachine.com:22 gateway.com cat - &

```

If I remember, it will create a nohup.out file with the output of the command.

---

### Post by Joeb454 on 2007-12-13
I thought the command for doing something like that was ```
screen
```

Not sure of the syntax myself because I've never used it, but a couple of people here at uni use it (I've seen them logged into the server sometimes when I ssh in :p)

---

