---
title: "powermac burgundy sound card"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by coverup on 2006-07-24
Hello everyone,

I posted a while back on this to 0 replies so I will try again now that it's changed slightly since I upgraded to Dapper.

The microphone/line input on my PowerMac G3 (with a PowerMac Burgundy sound card) does not work.  I have tried selecting it in alsamixer and all of that.  The capture tab has nothing under it - before it wouldn't even let me choose the capture tab though.  Sound output works beautifully.

I know the soundcard is fine because I tested it on the Mac OS before switching to Ubuntu.  Are there any available kernel patches to fix this, or does anyone know anything about this?

Anyone with any info at all, please reply - it's very important that I get the inputs to work for a project that I am working on.  Thanks in advance for your help!

Kevin

---

### Post by ristosu on 2008-03-14
I can confirm that the situation is exactly the same on an iMac G3 rev D (with burgundy sound chip and built-in mic),

---

### Post by oswaldkelso on 2008-03-14
> **ristosu said:**
> I can confirm that the situation is exactly the same on an iMac G3 rev D (with burgundy sound chip and built-in mic),

This thread points to the problem with an at your own risk fix? by the seems of it. Note  though the poster does not confirm his machine. 

[http://ubuntuforums.org/showthread.php?t=143538&highlight=burgandy+sound](http://ubuntuforums.org/showthread.php?t=143538&highlight=burgandy+sound)

---

### Post by stream303 on 2008-03-15
Does reconfiguring alsa make it work?
```

sudo dpkg-reconfigure alsa-base
```

---

