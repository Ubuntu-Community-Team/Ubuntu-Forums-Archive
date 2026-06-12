---
title: "Background processes"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by kurian on 2008-03-11
hi,

i need to run a mp3 player in the background and i need to run a script which goes on checks the state of some pins in my arm microcontroller and then if a pins goes high i need to pause the mplayer which runs in the background how could i do that ....how can i control the processes running in background

regards,

---

### Post by Cypher on 2008-03-11
One way to control an application running in the background is to send it various signals with the KILL command. Type the following
```

kill -l

```
This lists the signals that you can send and you'll see things like SIGUSR1 and SIGUSR2 or SIGSTOP and others. So in your application you'd TRAP on these signals and do the appropriate thing. Kill just needs the PID of the process to send the signal. 

The issue, of course, is if you are using a generic MP3 player, then you'd have to modify the code to add the necessary code to TRAP these signals and appropriatley pause and presumably resume when you get a different signal.

---

### Post by kurian on 2008-03-11
is der any easy methods for doing the same.....

---

### Post by Cypher on 2008-03-11
Nothing easier quickly comes to mind...sorry..

---

### Post by sisco311 on 2008-03-11
you can run mplayer with the -input option:

1.) create a fifo:
```
mkfifo /tmp/mp_fifo
```2.) start mplayer
```
 mplayer -input file=/tmp/mp_fifo /path/to/the/file.avi
```3.) to pause mplayer 
```
echo pause > /tmp/mp_fifo
``````
mplayer -input cmdlist
```will print a list of commands

the syntax is: echo *command_name* > /path/to/fifo/file

---

### Post by Cypher on 2008-03-12
**sisco311**, that's very cool!

---

