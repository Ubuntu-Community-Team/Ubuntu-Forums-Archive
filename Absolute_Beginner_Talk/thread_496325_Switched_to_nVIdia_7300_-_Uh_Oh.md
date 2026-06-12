---
title: "Switched to nVIdia 7300 - Uh Oh?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-07-09
Hey folks,

I just put in my new video card - nVidia 7300 and now I can't get to the GUI in Ubuntu (6.06).  

I am currently downloading Feisty 7.04 to make a Live CD.  

How should I proceed?  The main reason I bought the new video card was because I wanted Ubuntu to look better (I had crap before, because of my computer, not Ubuntu).  But now I can't get anything.

What did I do wrong?  And what do I do now?

Thanks,
awiggin

---

### Post by koshari on 2007-07-09
to begin with your xorg.conf file is prolly configured for the previous vid card , run dpkg reconfigure (the full line is listed in the comments at the top of the /etc/X11/xorg.conf file. and answer the questions, 

this will save an amended xorg.conf file, then try booting the xserver with startx

---

### Post by awiggin on 2007-07-09
Thanks.

I hate to be a total noob, but I need some clarification.  

How do I do that stuff if I can't hardly get into ubuntu?  Do I just type that stuff from the DOS-like screen?  And once I am done editing my xorg.conf , how do I save it and get out to re-boot?

Hopefully you can tell from my questions that I don't have hardly any idea what I am doing.

Thanks,
awiggin

---

### Post by teet on 2007-07-09
> **awiggin said:**
> Thanks.

I hate to be a total noob, but I need some clarification.  

How do I do that stuff if I can't hardly get into ubuntu?  Do I just type that stuff from the DOS-like screen?  And once I am done editing my xorg.conf , how do I save it and get out to re-boot?

Hopefully you can tell from my questions that I don't have hardly any idea what I am doing.

Thanks,
awiggin

Yeah, just log in to the "DOS like screen"

At the command prompt type: 

sudo dpkg-reconfigure xserver-xorg

It will load up an old school, text-based, blue screen wizard thing and ask you a ton of questions.  You'll want to be sure to select 'nv' as your video driver.  You can install the "real" nvidia drivers once you get back into a graphical environment.  

After you get done with that, reboot your machine and cross your fingers!

-teet

---

### Post by awiggin on 2007-07-09
Sweet.  I will try that and report back here.

Thanks.

---

### Post by awiggin on 2007-07-09
OK.  I'm in.

This is already much better.  I am in and able to use my GUI.  Now, how do I get the "real" nVidia drivers?

Thanks,
awiggin

---

### Post by meborc on 2007-07-09
try this - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

be sure to follow the instructions spesific to your ubuntu version (eg dapper)

EDIT: or did you mean the drivers from nvidia homepage by the "real"? :)

---

