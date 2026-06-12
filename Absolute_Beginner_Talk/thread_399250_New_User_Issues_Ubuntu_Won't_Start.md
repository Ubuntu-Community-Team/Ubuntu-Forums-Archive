---
title: "New User Issues: Ubuntu Won't Start"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Fillibuster on 2007-04-02
So I just installed Ubuntu today and a friend of mine helped me get it up and running and I was able to install Beryl.  I was messing around in Beryl's settings and everything locked up.  I was forced to power the computer off with the button, and when I restarted Ubuntu it let me enter my username and password but never actually started up.  It got stuck at the blank screen after the startup programs loaded on that bar thing.

---

### Post by justleen on 2007-04-02
assuming you have created a autostart for beryl:

press CTRL-ALT-F2, that should get you in a terminal.

Login here, and type ```
 sudo /etc/init.d/gdm stop 
```
this stops the current X session.
then remove the beryl start up
```
 ls /home/YOURUSERNAME/.config/autostart/ 
```
it will out the name of the autostart , for example beryl

```
 rm /home/YOURUSERNAME/.config/autostart/beryl 
```

change the last word to reflect the output of the ls command

---

### Post by Fillibuster on 2007-04-02
Alright, I'll give it a try, thanks for the response.

---

### Post by Fillibuster on 2007-04-02
Ok, so since I'm new to this...
I removed the beryl-manager and emerald autostarts.  Now how do I reboot the computer of this command line?

---

### Post by wj32 on 2007-04-02
Not really answering your question, but...

The next time something locks up, trying pressing these keys (in order):

Before each step, wait until disk activity has finished. Then continue.

Alt+SysRq+K
Alt+SysRq+R
Alt+SysRq+E
Alt+SysRq+I
Alt+SysRq+U
Alt+SysRq+B

---

### Post by Fillibuster on 2007-04-02
Thanks for that too.  I'm keeping a list of notes going so that I will know how to resolve some of these issues in the future.  Thanks for the responses guys, I'm learning with each of them...

---

### Post by justleen on 2007-04-02
you dont have to reboot, really
sudo /etc/init.d/gdm start

(just so you know, ```
 sudo reboot  
``` works...which is a shortcut for ```
 shutdown now -r 
```

---

### Post by Fillibuster on 2007-04-02
Cool, thanks.  I'll add it to my sheet of notes, lol

---

