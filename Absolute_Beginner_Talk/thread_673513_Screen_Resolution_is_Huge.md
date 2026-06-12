---
title: "Screen Resolution is Huge"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-20
Hi there,

I've been having quite a few problems with a new computer I recently bought - including kernel errors ([thread here]("http://ubuntuforums.org/showthread.php?t=672184")).

For some reason now, every time I boot my resolution is HUGE probably at around 170%.

If I go into system>preferences>screen resolution or system>admin>screens and graphics it currently says;

Resolution: 1400 x 1050
Refresh Rate: 50 hz

It's obviously not that resolution, and I'd like it to be 1024 x 768 with the refresh at around 67 hz.

If I try to change it, it remains exactly the same - but still asks if I want to keep this resolution or revert to original.

It's been suggested in the thread I linked to that maybe my motherboard is on its way out (already!) - is this likely?

---

### Post by spiderbatdad on 2008-01-20
i think you can edit /etc/usplash.conf and it will stay.```
gksu gedit /etc/usplash.conf
```change x, y, to 1024, 768 and save

---

### Post by banewman on 2008-01-20
Sounds like a hardware issue - can you put in a different video card to check if that is the issue for this?

---

### Post by Kilz on 2008-01-20
Have you tried replacing the video card drivers? What video card do you have?

---

### Post by Squizz on 2008-01-20
> **spiderbatdad said:**
> i think you can edit /etc/usplash.conf and it will stay.```
gksu gedit /etc/usplash.conf
```change x, y, to 1024, 768 and save

Didn't work sorry :(

[quote=Kilz] 	
Have you tried replacing the video card drivers? What video card do you have?
[/quote]

I'll check at the post when I reboot in a sec, dont remember off the top of my head - I am using the nVidea restricted drivers though.

[quote=banewman] 	
Sounds like a hardware issue - can you put in a different video card to check if that is the issue for this?[/quote]

Not right now I can't.  Possibly tomorrow, but the gfx card has been working fine (and with my old computer) until now.  I will however try taking it out and putting it back in again....

---

### Post by Squizz on 2008-01-20
I just removed and replace my gfx card - which is a GeForce 6600 256mb one.

I was greeted after Grub by

```

Duplicate or bad block in use

/dev/sda1/:Multiply-claimed block(s) in inode 7: 32 98 
/dev/sda1/:Multiply-claimed block(s) in inode 3786524: 7649313
...... lots more of the same message with a different number at the end

fsck died with an exit status 4

```

The I did fsck manually, and after repairing lots of things, Ubuntu booted - only this time I'm in 640x480 graphics mode and it doesn't give me any other options when I try to change that.

Can anyone shed any light on the situation?

---

### Post by spiderbatdad on 2008-01-20
have you tried the package displayconf-gtk in synaptic? It puts a graphical screen configuration tool in System>>Administration>>Screens and Graphics. Otherwise maybe xorg.conf needs editing.

---

### Post by Squizz on 2008-01-20
I've just booted into the live cd and it's working just fine.

If I copy my xorg.conf file from this boot and put it where my normal boot one is, should that help?

---

### Post by Kilz on 2008-01-20
You might consider using the video driver from nvidia, or [using envy to install it.]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Squizz on 2008-01-20
Fixed it.

In order to do so, I booted into the liveCD (as the graphics deteriorated to the point that I couldn't navigate anymore) so my boot was unusable.

Navigated to /media/disk/etc/X11/

sudo rename xorg.conf xorg.old
sudo nano xorg1.conf
save as xorg99.conf
sudo rename xorg99.conf xorg.conf

Rebooted and all was well once more :)

---

