---
title: "A couple Mounting questions"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-05
Got linux and xp dualbooting now with no problems.  Grub is good, k7 kernal is functioning *swimmingly*, no real problems with anything really.  However, the windows partition is sitting on my desktop and that bugs the heck out of me.  Would unmounting it remove it from here?  If i do unmount it, would there be any negative effects from this?  Like for example any problems booting into windows from the grub?  Also, when mounting my fat32 partition intended for sharing, how would i go about putting it in my home folder?  I like the desktop clean is why i ask.

---

### Post by linbetwin on 2005-11-05
You can mount it to a directory other than /media or you can unmount it. You won't have any problems.

---

### Post by shof2k on 2005-11-05
If you want the desktop clean but still have access to your drives, do the following.  

1) From the menu bar select 'Applications', 'System Tools', 'Configuration editor'
2) Inside the configuration editor navigate to 'apps', 'nautilus','desktop'
3) In the right hand pane, uncheck the option marked 'Volumes visable'

With your shared partition, it's best to put a link in your home folder pointing to it.  Open a terminal and type.
sudo ln -s {path to shared partition} /home/{username}

Hope that helps.

---

### Post by Zunflappie on 2005-11-21
I have some questions either.

I have, in history, mounted my hda1 to /media/documenten.
Now, i want to DISMOUNT (or unmount?) that hda1.

And than re-mount to a other place.
But, i am not allowed to.
Where can i make myself a really hardcore-admin? (like ' sudo' )?

Please explaine simple: i am new to linux ubuntu.

---

### Post by steve.horsley on 2005-11-21
[QUOTE=Zunflappie]I have some questions either.

I have, in history, mounted my hda1 to /media/documenten.
Now, i want to DISMOUNT (or unmount?) that hda1.

And than re-mount to a other place.
But, i am not allowed to.
Where can i make myself a really hardcore-admin? (like ' sudo' )?

Please explaine simple: i am new to linux ubuntu.[/QUOTE]

to dismount a drive, the command us umount:
**sudo umount /media/documenten**

Once it is dismounted, you should be able to mount it somewhere else.

If you get tired of typing sudo in front of everything, you can use the command **sudo bash** to get a root shell. Use **exit** to leave.

---

### Post by Zunflappie on 2005-11-26
Oke... next thing.

The used hdd by Ubuntu... i want to read it in Windows.
How do I do that?
In Windows it isnt possible.... (or i have to make that drive al logical-hdd... but it that correct?)

WITHOUT DAMAGING SOMETHING ofcourse! ;)

Eddy

---

### Post by ShakingSpirit on 2005-11-26
There's a tool called Explore2fs which is an easy way to move files around between windows and linux. It's not practical for day-to-day use of your linux partition, and wont 'mount' the drive under windows, but is much quicker and easier than the alternatives :)

---

### Post by megamania on 2005-11-26
[QUOTE=Zunflappie]Oke... next thing.
The used hdd by Ubuntu... i want to read it in Windows.
How do I do that?
In Windows it isnt possible.... (or i have to make that drive al logical-hdd... but it that correct?)
[/QUOTE]

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

[http://ext2fsd.sourceforge.net/index.htm](http://ext2fsd.sourceforge.net/index.htm)

check these out! windows drivers for ext2/ext3 filesystems. ;-)

---

