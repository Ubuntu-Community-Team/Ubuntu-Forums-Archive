---
title: "root@ubuntu~# question"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-06-29
If anyone outthere has been following my threads, I have a lot of people trying to help, but either I'm not explaining it right or this system I have is completed messed up..........

This time ::::::
I rebooted , hit escape, and got the restore kernel lines, clicked on one , and it went through a list of commands and explainations, ending up the PCMCIA file failing, 

 finally at the end I got cardmgr (3506):no sockets found           failed

and then setting up general console font
root@ubuntu~#

a new command line: any suggestions?

have tried the sudo dpkg-reconfigure xserver-xorg several times, but not getting anywhere, even after double checking the directions from forum helpers.....the x driver auto selects vesa and from there I hit enter all through to the end and go back to the command line of user@ubuntu~$

any ideas are welcome

I do have a disc labeled "motherboard support CD". I tried to put it in the drive but the system ignores the cd and proceeds into trying to set up ubuntu.  normally i get the fatal error and returns me to user@ubuntu~$ command line and from there start over....

---

### Post by taurus on 2006-06-29
At the prompt, type
```

startx

```

---

### Post by rmaier on 2006-06-29
thanks for the answer back....i did type in startx and got the familiar

(EE) xf86Openserial: cannot open device  /dev/wacom
no such file or directory :
error opening /dev/wacom : success
no core pointer

fatal server error 
failed to initialize core devices
X10: fatal 10 error 104 on X server
then back to root command line

---

### Post by uzi09 on 2006-06-29
sorry, for those of us who haven't been following your threads (sorry :)), i'm assuming you're having problems loading up the gui for ubuntu.

did the live cd happen to work for you?

---

### Post by rmaier on 2006-06-29
no, I thought if I could put either ubuntu  live or  install cd in, it would start up from the cd, but the system goes right to trying to set up ubuntu, I get the PCMCIA fail error only on the line by line, then it goes to the errors about the x server and to the command line where I tried to do the reconfigure  xserver-xorg.....thanks for the reply ....any help is much appreciated

---

### Post by uzi09 on 2006-07-01
hmm, i'm not sure what you mean by "the system goes right to trying to set up ubuntu" on either live/install cd.

i'm not too familiar with the latest releases since when i installed dapper, it was still in its beta version. if it's anything like breezy/beta install of dapper, even for the live cd, you'll see a menu similar to the install. if you read carefully, you should see that the list has an option to just have some sort of a default boot.

try to give it another try, in the mean time, i'll try to see what options are available on the live cd and let you know what to try out.

also, can you let us know which ubuntu you're installing? is it breezy, or dapper??

it sounds like a hardware support issue -- basically, if the live cd doesn't work, the install won't work either :S

if you're using breezy, try dapper instead.

---

### Post by rmaier on 2006-07-02
thanks, i got it working by going into Bios and setting it to load directly from the CD, inserted the install ubuntu 5.10 cd and am back running...thanks to the forum writer who suggested this to me.....and to everyone who sent me suggestions....

---

