---
title: "Black screen and loading mouse"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by LouisChappell on 2008-01-06
Hi, basically I'm getting a black screen with a loading icon fora mouse. I have tried > sudo dpkg-reconfigure xserver-xorg but it stops after desired default color depth in bits and says > xserver-xorg postinst warning: overwriting possibly-customised configuration file; bqackup in /etc/X11/xorg.conf .20080106221345

I have kind of asked a while ago but I'm going back to uni tomorrow where I don't have the internet and I have exams on next week for which I have some REALLY important files on on the ubuntu partition. I need these before the exam, they're pdf. If I can't unlock the GUI i have a usb, i can get to the terminal with ctrl+alt+F1.

I'm in a mad panic so PLEASE could someone help me out?

---

### Post by Daveth on 2008-01-06
it sounds like your X-server has fallen over.
Try

```
sudo /etc/init.d/gdm start
```

should not cause harm even if I'm wrong! Assumes you are running a gnome desktop, of course.

---

### Post by LouisChappell on 2008-01-06
I typed that in and it said 
> *Starting GNOME Display Manager...                                                 [OK]
but then took me back to > louis@ubuntu:#$ have you any other ideas? they'd all be appreciated.

EDIT: New problem now. i just reinstalled everyting ignore this thread.

---

### Post by aonegodman on 2008-01-07
:confused:  How do you execute these commands when you are having to run off of the LiveCD in a Live Session and want them to have an effect on your regular boot HD user files????  I mean how will any changes be made and be permanent upon trying to reboot  from your regular install?

Thanks!  :D

---

### Post by Daveth on 2008-01-08
um, looks like it cannot display that then, so a graphics driver issue perhaps? Or a screen resolution thing? Bit perplexed...

I'm not sure the live cd is being used is it- just a command prompt on a hard drive install, surely. A live cd would be 1 short cut to get the files off, though not a solution. Need more forum help here.....

---

### Post by LouisChappell on 2008-01-13
it's ok now, this issue is no longer a problem to me, thanks for the help though.
> EDIT: New problem now. i just reinstalled everyting ignore this thread.
my new problem is i think my laptops dead, wouldn't recognise HDD's any more, think it's the mobo. going to send it back and hope for the best cheers.

---

