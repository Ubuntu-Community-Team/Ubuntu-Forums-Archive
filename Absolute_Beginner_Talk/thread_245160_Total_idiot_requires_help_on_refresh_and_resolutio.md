---
title: "Total idiot requires help on refresh and resolution"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by westie on 2006-08-27
Hi Guys,
I am a complete and utter linux noob, mainly because windows vista scares me.  I have a similar problem to others it seems, my defualt monitor resolution is 1024*768 @ 60 Hz.  I have been reading threads on here all day to try and get this put upto 1280*1024 @ 85 Hz, but everytime I do something and reboot it comes up with some error that x server can't start.  I managed to change the resolotion once but not the horrible refresh rate.

So bacially how can I change the refresh rate and the resolution to the required one, secondly please chat to me like a 5 year old with learning difficulties as I have no idea of linux.

---

### Post by aysiu on 2006-08-27
"everytime I do something"? What exactly have you tried so far?

And what are the make and model of your monitor?

---

### Post by Anonii on 2006-08-27
> **westie said:**
> Hi Guys,
I am a complete and utter linux noob, mainly because windows vista scares me.  I have a similar problem to others it seems, my defualt monitor resolution is 1024*768 @ 60 Hz.  I have been reading threads on here all day to try and get this put upto 1280*1024 @ 85 Hz, but everytime I do something and reboot it comes up with some error that x server can't start.  I managed to change the resolotion once but not the horrible refresh rate.

So bacially how can I change the refresh rate and the resolution to the required one, secondly please chat to me like a 5 year old with learning difficulties as I have no idea of linux.


Try this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

the second paragraph fixed it for me. But well, I could only use 640x480, and 60hz...

---

### Post by westie on 2006-08-27
Hey,
I tried following a couple of thread from here like

[http://www.ubuntuforums.org/showthread.php?t=222034&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=222034&highlight=nvidia)

[http://www.ubuntuforums.org/showthread.php?t=240764&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=240764&highlight=nvidia)

etc

one from the eyecandy part in the ubuntu faq.

I have a Nvidia GeForce 6200, the monitor is a Compaq V1100, and its the 64bit version of Ubuntu.  Will have a read of the How to :) ty

---

### Post by westie on 2006-08-27
on a side note nvidia doesn't appear in the list when i use

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by westie on 2006-08-27
ok i went to use that add remove programs and i installed nvidia-glx, on reboot this buggered up my x server (blue screen) so i ran this command

sudo dpkg-reconfigure -phigh xserver-xorg

and selected 1280*1024 so the res now works, but the refresh rate is still 60 Hz....

---

### Post by westie on 2006-08-27
Finally after a day I got it working!

[HTML]http://doc.gwos.org/index.php/ChangeResolution[/HTML]

---

