---
title: "Major breakdown with X"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by ndefontenay on 2007-02-11
Good evening,

I've been toying around a bit with Linux and I guess I've been a bit far with X.
I've installed Automatix2 and installed the Windows fonts.

The problem occured after I rebooted it.

X would'nt start. I remained with a command line.
When I run the command X to start an Xserver session, all I got was a grey screen with a cross as a mouse pointer and nothing else.

I went to the logs ans saw that some fonts were missing.

All I figured out I could do to "fix" it has been to re install Linux.

My question is as follow: Is there anything I could have done to repair some missing fonts?

What should have I done?

I was thinking about re installing X only using apt-get but I didn't know the package name... In fact that might sound a bit stupid, I'm not sure if I can actually repair only X..

The truth is, sure Linux never fail. I might loose the X server but linux core is still here with its command line... But it serves no purpose to me as a user ><

I felt terribly lost in front of that problem : (

---

### Post by arochester on 2007-02-11
If you have just upgraded to the new kernel and lost X you are not alone and not to blame. The recover X you should input from the command line prompt> sudo dpkg-reconfigure xserver-xorg
This will bring up a text based wizard. If you do not know the answer to any questions then go with the suggested default answer. If at first you don't succeed try again and specify vesa. This should bring back some functionality. Use Automatix to remove the fonts and then reinstall them.

---

### Post by codejunkie on 2007-02-11
> **arochester said:**
> If you have just upgraded to the new kernel and lost X you are not alone and not to blame. The recover X you should input from the command line promptThis will bring up a text based wizard. If you do not know the answer to any questions then go with the suggested default answer. If at first you don't succeed try again and specify vesa. This should bring back some functionality. Use Automatix to remove the fonts and then reinstall them.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```will also recover the x server in most cases, it will auto configure it to the default settings that the Ubuntu installer uses, so if it works fine with the live cd this should fix it unless there is some packages broken.

---

### Post by ndefontenay on 2007-02-11
Thanks a lot for the answers guys.
I'll keep a not of this thread somewhere for the hard days!

---

