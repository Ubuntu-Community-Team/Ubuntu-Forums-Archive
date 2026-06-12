---
title: "howto terminal instruct computer to kill process[appl/name] after close/logout.[skype"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by okkie on 2007-09-08
the answers i got tell me how to end a process after application was used,that is abnormal .i want computer to close skype/ekiga process when i log out and restart it on login.now keeps on opening new processes.can i sudo or something this right?
thanks

---

### Post by Beggar on 2007-09-08
Alright so I spent a few minutes reading over this post and I think I have figured out the question that you are trying to ask. In the future, a little proofreading goes a long way towards getting people to help you. 

Anyways, to kill a process from the terminal you have two choices

```
sudo killall <process name>
```

alternately you can use kill but you will need to look up the pid (Process ID) of the process, use the first command will search through all the running processes for the one you want to kill and spit out some info about it, including the pid. Then just enter the pid into the second command.

```

ps -e | grep <process name>
kill -9 <pid>

```

---

### Post by diatribe on 2007-09-08
when you say log out do you mean log out of X? because it should close any processes you were running when you log out anyway unless it is running as a daemon

---

### Post by okkie on 2007-09-09
i have been told before to give proper details when asking help and also to proof read.thanks for your trouble.i stand corrected.i just came back from my son skyping on windows.when he closes skype it leaves a small green icon on the left of the bottom tray indicating skype is on standby.so no need for stopping any process.skype ubuntu does not leave a 'standby' icon or if it does i do not know where.this will also solve my problem.however not seeing it phisically i click on the skype icon to start a conversation and skype opens a new process with error line 'skype is running'now i have to go system administration system monitor and kill the process or reboot.i think i must also mention that all applications i use have icons on the top tray including skype incase that might cause a problem.getting back to my oridinal question i was just looking for a script that will permanently close the process after i have finished skyping and have closed skype.eg like firefox and others.chances are good i do not understand how the various processes work .i am trying to get there.thanks to all the posts on the forums i almost have a perfectly running machine and thanks for your time.

---

### Post by okkie on 2007-12-16
problem is still not solved and not getting further attention so consider thread closed

---

