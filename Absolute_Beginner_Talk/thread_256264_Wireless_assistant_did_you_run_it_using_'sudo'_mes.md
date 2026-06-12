---
title: "Wireless assistant did you run it using 'sudo'? message"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by *Zebedee* on 2006-09-12
Hi all,

I have been trying to connect to my router using wireless assistant but a message keeps asking me 'did you run it using sudo?'. The answer being 'no' I just clicked on wireless assistant.

I typed sudo from terminal, message shown above still displayed?
Should I have typed sudo wireless assistant?? I would be very greatful if somebody could point me in the right direction?

Wireless assistant sees the router with 6 star link quality.
Configuration automatic dchp connection failed
Manual configuration, when trying to connect, message file,/etc/resolv.config could not be opened for writing, appears in error box :confused: 
I assume something to do with sudo, as wireless assistant warned me that all may not be well with my (sudo status) ??

All suggestions greatfully recieved, many thanks in advance.
Regards, Zebedee

---

### Post by RobsterUK on 2006-09-12
If you want to do any administrative functions in Ubuntu you need to prefix the command with sudo in Terminal eg:
```
sudo command
```
when using sudo you will be prompted for your user password

I'm not sure what the command is for wireless assistant but thats the gist of it.

---

### Post by ruedu on 2006-09-12
What is wireless assistant?  I'm looking for something that is better than the gnome-network-manager thing.  I could try it and let you know what it takes to make work.

---

### Post by max.diems on 2006-09-12
The command you want is ```
gksudo wlassistant
```

---

### Post by max.diems on 2006-09-12
The command you want is ```
sudo wlassistant
``` TYPE IN TERMIAL/KONSOLE!

---

### Post by *Zebedee* on 2006-09-12
Thankyou max.diems... sweet, error msge gone... the game continues! :D 

Re what is wireless assistant, found it under Applications, Add / Remove.

Regards, Zebedee :-D

---

