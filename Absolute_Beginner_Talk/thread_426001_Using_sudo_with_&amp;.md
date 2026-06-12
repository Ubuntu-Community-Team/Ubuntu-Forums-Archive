---
title: "Using sudo with &amp;"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-28
I use the '& ' behind a command to be able use other commands in the same shell.  When I use 'sudo command &' it does not give me the opportunity to type in the password.  It skips the password and takes me to a prompt.  How can I use sudo and & at the same time?

Thank you.

---

### Post by Najand on 2007-04-28
You cannot do that, because when you type & it goes to the background and you won't be able to type your password... Use gksu instead of sudo when you want to use &.
```

$ gksu COMMAND &

```

---

### Post by Skrynesaver on 2007-04-28
First off you have a number of sudo jobs *backgrounded* run "jobs" and see how many jobs are running in the background.  To bring these forward enter "fg" then CTRL-C to interrupt them until you have a clean shell.
Now, run the command without the & as this is backgrounding the whole task.
Enter your password.
Hit CTRL-Z to suspend the job
Now enter "bg" this will cause the suspended job to resume processing in the background.
Now have a look at [http://gd.tuwien.ac.at/linuxcommand.org/lts0080.html](http://gd.tuwien.ac.at/linuxcommand.org/lts0080.html) this covers job control in a bit more depth

---

