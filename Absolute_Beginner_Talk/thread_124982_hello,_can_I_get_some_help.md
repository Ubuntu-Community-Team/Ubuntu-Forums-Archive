---
title: "hello, can I get some help?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Uber N00b on 2006-02-02
I am really new to linux and my friend reffered me to kubuntu.  right now I have a LiveCD and ran it, after everything loaded it says
Ubuntu@ubuntu:~$
can someone lead me from here?


Thanks to any one for the help!

---

### Post by Digitallysick on 2006-02-02
did you try typing startx

it should have loaded automaticly, you might have to configure it, why type of video card do you have

---

### Post by Estariel on 2006-02-02
It is not supposed to do that! It should drop you right into a nice comfortable graphical environment.

What computer are you running this on? (especially the graphics board would be interesting!)

Thanks!

---

### Post by freemanda3 on 2006-02-02
i agree with everyone else who posted before me. you should have finished with a nice graphical user interface(gui), but it sounds like the install either didn't detect your video card properly or there was a choice you made during the install and you ended up with a shell login. as far as the ubuntu@ubuntu:~$ goes the first ubuntu is the person logged in and the second is the name of the computer. the ~sign is saying you are in the home folder and the $ sign is the user prompt.

hope this helps or rather answer your question :)

---

### Post by Uber N00b on 2006-02-02
when i typed in startx it says
```
XIO: Fatal IO error 140 (connection reset by peer) on X server ":0.0"
     after 0 requests (0 known processed) with 0 events remaining
```
My graphics card is ATI Radeon X800XL, could this be a problem?

---

### Post by towsonu2003 on 2006-02-02
```
sudo dpkg-reconfigure xserver-xorg
```hopefully it will not ask for a password... I dont know what password to give :-k 
from there, try to give the best answers you can give to the configuration wizard. for stuff you don't know, leave the default answers. than startx again. if it drops you to the command line (ubuntu@ubuntu~), ```
cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW
cat /var/log/Xorg.0.log | grep ??
``` and paste the output of each, which should help those with experience with X failures (dropping to command lines). These commands look into the log file mentioned and spits the lines that have EE (error), WW (warning) and ?? (unknown) character in them out to the output. 

PS. I am not sure how you can copy paste the error messages from that command line to here...
PS2. Ati is supposed to work...
PS3. unplug everything except the mouse, keyboard, and monitor from the computer - may be a hardware conflict?

---

### Post by Uber N00b on 2006-02-02
thanks for helping everyone, but towsonu2003, when i entered
sudo dpkg-reconfigure xserver-xorg
I did everything it told me to do, yet still when
ubuntu@ubuntu:~$
came back up, I typed in startx and it came up with the same error.

---

