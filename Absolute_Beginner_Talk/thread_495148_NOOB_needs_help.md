---
title: "NOOB needs help"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by myolbug on 2007-07-07
I have an older computer that has an SiS630/730 vid card.  I googled changing my screen res and I reset it but to the wrong parameters.  Now, after Ubuntu 6.06 boots, the monitor is black.  How do I change it during boot?

The monitor is a Princeton VF723 and it should be at Horizontal res. 30-70 and vertical 50-120, and the size should be 1024X768@85Hz.  I changed the H to 30-120 and V to 50-150.  

Can anyone give me the steps that I need to take to correct my obvious flub?  I am using W2K right now, so if I can print it that would be great.  

I have tried Google, but I can't seem to find the right steps.

Thanks,

Randy

---

### Post by taurus on 2007-07-07
Boot into recovery mode from GRUB menu and modify /etc/X11/xorg.conf.

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.  

Then, reboot and see what happens.

```
shutdown -r now
```

---

### Post by myolbug on 2007-07-07
I did as you said, but nothing happened.  Perhaps I did it wrong?  I booted in recovery, let it run all of the scripts, then at the root I wrote the above, but the resulting screen was blank.  Even after saving, I didn't see anything.

Any other suggestions?  I feel that I have screwed the proverbial pooch.

---

### Post by oilchangeguy on 2007-07-07
if you've just installed 6.06, you have nothing to lose by simply reinstalling it.

---

### Post by myolbug on 2007-07-07
> **oilchangeguy said:**
> if you've just installed 6.06, you have nothing to lose by simply reinstalling it.


I can't.  This was loaded by my bro, who is out of the country right now.  I wanted to see if I can find out what I did wrong, and fix it myself.  I have a lot of important things on my Linux side and I don't want to risk losing it.

If my bro were in the country he could help me, but alas...

---

### Post by ugm6hr on 2007-07-07
> **myolbug said:**
> I can't.  This was loaded by my bro, who is out of the country right now.  I wanted to see if I can find out what I did wrong, and fix it myself.  I have a lot of important things on my Linux side and I don't want to risk losing it.

If my bro were in the country he could help me, but alas...

If the Ubuntu LiveCD (or any other LiveCD) works, you could boot from the LiveCD, mount the hard drive, and edit / change back xorg.conf

If it doesn't work - it will at least allow you to backup your "home" directory to do a fresh reinstall.

---

### Post by myolbug on 2007-07-07
Ahh, yet another barrier.  I don't have the disk.  Are there any other ways that I can fix this?  I know that when I first got the computer back from him, he had the resolution set for his LCD high res monitor, and he had me go in through the boot process and make changes.  How do I do this, if what I have been told wasn't it?  I remember going through the autodetect, but it was using commands, not through the OS.

---

### Post by oilchangeguy on 2007-07-07
the computer you're now using, does it have a cd burner? if so create a live cd. see this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by annda on 2007-07-07
> **myolbug said:**
> I did as you said, but nothing happened.  Perhaps I did it wrong?  I booted in recovery, let it run all of the scripts, then at the root I wrote the above, but the resulting screen was blank.  Even after saving, I didn't see anything.

Any other suggestions?  I feel that I have screwed the proverbial pooch.

please make sure you type everything correctly. spaces and capital letters are important.
```

nano -Bw /etc/X11/xorg.conf
```

this will give you the contents of the file you have to modify. HorizSync and VertRefresh are your lines.

---

### Post by myolbug on 2007-07-07
Okay, here is the thing.  I carefully typed in the command, as is written, after I got the root prompt, after it ran scripts.  The file is empty.  I printed the directions up and made sure that they match.  it gives me the file name at the top of the screen of /etc/X11/xorg.config.  When I hit control o it asks me to save to the above file name and then says that no such file exists.  It also says that the file has been modified, yet it doesn't give me anything to modify.  What am I doing wrong?

---

### Post by taurus on 2007-07-07
If you look at it carefully, you got the name wrong.  It's

```
nano -Bw **[COLOR="Blue"]/etc/X11/xorg.conf[/COLOR]**
```
not /etc/X11/_xorg.config_.

---

### Post by myolbug on 2007-07-07
Well, I got it figured out.  I went to recovery, and at the root prompt, I typed in dpkg-reconfigure xserver-xorg.  This took me to the window that allowed me to correct the proper settings.  Thanks to all, I really appreciate your help.  Oilchangeguy, it was your link that led me to finding the answer.  Again, thanks to all:p

---

