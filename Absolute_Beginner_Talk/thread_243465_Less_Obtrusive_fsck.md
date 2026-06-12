---
title: "Less Obtrusive fsck"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by kiplingw on 2006-08-25
So there I was, booting my laptop and about to make a presentation, when fsck decided that it just had ensure that that day would be the thirtieth boot. I understand that fsck is important and healthy for the system, so I don't want to remove it, but only change its behaviour.

Is it possible to have fsck *ask* on the thirtieth boot if it is ok for it to do its thing? If the user answers no, then it will continue to ask each boot until it has finally completed successfully a file system check.

Kip

---

### Post by cantormath on 2006-08-25
> **kiplingw said:**
> So there I was, booting my laptop and about to make a presentation, when fsck decided that it just had ensure that that day would be the thirtieth boot. I understand that fsck is important and healthy for the system, so I don't want to remove it, but only change its behaviour.

Is it possible to have fsck *ask* on the thirtieth boot if it is ok for it to do its thing? If the user answers no, then it will continue to ask each boot until it has finally completed successfully a file system check.

Kip

I thought you could hit ctrl+c to end it, but I dont remember and Im about 25 reboots away....

---

### Post by kiplingw on 2006-08-25
If you ctrl-c, it just breaks to console. That is scary because most of your drivers / services, including X, never got a chance to initialize.

Kip

---

### Post by TFX360 on 2006-08-25
kiplingw,


Try changing the last number on the volume's line in /etc/fstab to 0.


And ofcourse fsck your drive when you feel like it...

Even better but do not know if supported is 

[http://www.netadmintools.com/html/tune2fs.man.html]("http://www.netadmintools.com/html/tune2fs.man.html")


Kind regards,


TFX

---

### Post by kiplingw on 2006-08-25
I am just worried that it might actually need to do something important. If I set it to zero, will fsck still run at boot if the system does not shutdown properly (battery dies)? Could having it off allow for damage to the file system?

Kip

---

### Post by ROFRSOC on 2006-08-25
Hey Kip, how's it going? LOL.

---

### Post by TFX360 on 2006-08-25
I think you should see a crash differently than a standard check.

---

### Post by Anduu on 2006-08-25
Yes it would see a crash differently and check anyway.

As you said it ***is*** an important procedure...I myself have had fsck find errors even tho I had no crashes or wierd things going on.

Next time you have a presentation coming up you can ahead of time use...

```
sudo shutdown -rF now
```

This will force a check on all disks and I think reset the counter.

---

### Post by Frank Golden on 2006-08-25
> **Anduu said:**
> Yes it would see a crash differently and check anyway.

As you said it ***is*** an important procedure...I myself have had fsck find errors even tho I had no crashes or wierd things going on.

Next time you have a presentation coming up you can ahead of time use...

```
sudo shutdown -rF now
```

This will force a check on all disks and I think reset the counter.
Thank's for the tip. I always wondered how to force check and reset counter.
This comes in handy because everytime I do a major upgrade/change to my install, I make a partimage image of it. Of course I only do this after I
prove that the changes/updates work. I have done this where the counter was at 29 apparently. When I next used the image to restore a damaged install.
The next boot would do a disk check. A minor annoyance, I know. Now I can force check before I use partimage to create image and have an image that has the counter reset.

 If I were doing a presentation though
I think I would startup well before my presentation. Just in case I
had other issues.:)

---

