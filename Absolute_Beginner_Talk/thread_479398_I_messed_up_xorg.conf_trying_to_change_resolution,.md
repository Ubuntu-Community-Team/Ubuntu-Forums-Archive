---
title: "I messed up xorg.conf trying to change resolution, now Gnome won't load!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-20
To paraphrase Mark Twain, there are fools, damn fools, and samuraiCat.

Last night, after days of research, I installed a dual boot with XP and Ubuntu. I used the liveCD to create my partitions, and it worked perfectly.

Then, I got stupid.

I wanted to change my resolution and refresh rate to 1024x786 at 60hz. Instead of using Envy or "sudo nvidia-settings", I decided to use "sudo dpkg-reconfigure xserver-xorg," and I deleted all the other settings except 1024x786 and changed the refresh rate. I saved, rebooted...and was told that I killed the Gnome. When I rebooted the first time, I got a nasty blue square that told me that I had hosed xorg.conf. Now all I have is a command prompt. 

Is there a way to fix this from that prompt, or do I have to reinstall from the liveCD? If I do have to reinstall, will I be able to keep all the partitions that I already put on, or will I have to wipe the whole damn thing?

Thanks in advance.

---

### Post by LaRoza on 2007-06-20
Just use your backup copy of xorg.conf before you edited...

If not possible, just use the Live CD to fix it. I always use Slax for this, Ubuntu seems to have trouble.

Use Ubuntu LiveCD and copy the settings from the Live cd onto the xorg.conf on you hard disk. 

Next time, make a backup copy of the file, it makes it much easier.

---

### Post by yagood on 2007-06-20
You could try running dpkg-reconfigure again from the command line to create new xorg.conf.

---

### Post by samuraiCat on 2007-06-20
> **yagood said:**
> You could try running dpkg-reconfigure again from the command line to create new xorg.conf.


So, I would type "sudo dpkg-reconfigure xserver-xorg" at the prompt, correct? Then what? Thanks, btw.

---

### Post by yagood on 2007-06-20
> **samuraiCat said:**
> So, I would type "sudo dpkg-reconfigure xserver-xorg" at the prompt, correct? Then what? Thanks, btw.

Oh, I see that dpkg-reconfigure got you in trouble in the first place... so most probably you entered something wrong while configuring.

Could you check what error message is displayed in this "nasty blue square"? It should ask you for viewing log or something like that, answer yes and check the output for errors.

---

### Post by samuraiCat on 2007-06-20
> **LaRoza said:**
> Just use your backup copy of xorg.conf before you edited...

If not possible, just use the Live CD to fix it. I always use Slax for this, Ubuntu seems to have trouble.

Use Ubuntu LiveCD and copy the settings from the Live cd onto the xorg.conf on you hard disk. 

Next time, make a backup copy of the file, it makes it much easier.

Yeah, um, did you read the part about me gettin' stupid? I didn't back it up. How exactly do I copy those settings? Thanks.

---

### Post by yagood on 2007-06-20
> **samuraiCat said:**
> Yeah, um, did you read the part about me gettin' stupid? I didn't back it up. How exactly do I copy those settings? Thanks.

dpkg-reconfigure should create a copy automatically, check in /etc/X11/ directory for files with name like xorg.conf.<TIMESTAMP>.

---

### Post by samuraiCat on 2007-06-20
> **yagood said:**
> Oh, I see that dpkg-reconfigure got you in trouble in the first place... so most probably you entered something wrong while configuring.

Could you check what error message is displayed in this "nasty blue square"? It should ask you for viewing log or something like that, answer yes and check the output for errors.

I would post that info, but I'm not at home right now. It was all about xorg.conf, though. If I use the dpkg-reonfigure at that prompt, will it restore everything in the xorg file?

---

### Post by LaRoza on 2007-06-20
For future reference.

```

$ cp /etc/X11/xorg.conf /etc/X11/xorg.bk

```

Then you can edit xorg.conf, if you need to restore, just delete the botched file, common error, and rename xorg.bk to xorg.conf.

---

### Post by yagood on 2007-06-20
> **samuraiCat said:**
> I would post that info, but I'm not at home right now. It was all about xorg.conf, though. If I use the dpkg-reonfigure at that prompt, will it restore everything in the xorg file?

You should have a backup copy created for you by dpkg-reconfigure automatically before saving the settings, so you should be able to simply delete "messed up" xorg.conf and rename one of the backups to xorg.conf.

---

### Post by samuraiCat on 2007-06-20
> **yagood said:**
> dpkg-reconfigure should create a copy automatically, check in /etc/X11/ directory for files with name like xorg.conf.<TIMESTAMP>.


I'm really sorry about being this annoyingly ignorant, but how do I check that from the command prompt, and then what do I do with it?

---

### Post by samuraiCat on 2007-06-20
> **LaRoza said:**
> For future reference.

```

$ cp /etc/X11/xorg.conf /etc/X11/xorg.bk

```

Then you can edit xorg.conf, if you need to restore, just delete the botched file, common error, and rename xorg.bk to xorg.conf.


Thanks! Seeing as how this may happen again, I'll need that!

---

### Post by yagood on 2007-06-20
> **samuraiCat said:**
> I'm really sorry about being this annoyingly ignorant, but how do I check that from the command prompt, and then what do I do with it?

First of all, look at the name of this forum. It says "Absolute Beginner Talk", right? So no one has to apologize for anything here!

Type:

```

ls /etc/X11/

```

This will list files in that directory. Look for any files named xorg.conf.something. If you find one, type:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.messedup
sudo mv /etc/X11/xorg.conf.something /etc/X11/xorg.conf

```

Then reboot.

---

### Post by samuraiCat on 2007-06-20
> **yagood said:**
> First of all, look at the name of this forum. It says "Absolute Beginner Talk", right? So no one has to apologize for anything here!

Type:

```

ls /etc/X11/

```

This will list files in that directory. Look for any files named xorg.conf.something. If you find one, type:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.messedup
sudo mv /etc/X11/xorg.conf.something /etc/X11/xorg.conf

```

Then reboot.

Wow, that sounds a lot better than reinstalling. Thanks!

Edited to add: By the way, I think part of my problem was that I tried to type into the terminal from some notes. I have a feeling I typed it incorrectly. I'll cut and paste this time.

---

### Post by LaRoza on 2007-06-20
A common mistake is not capitalizing the X in X11, Linux is case sensitive. I have done that several times.

---

### Post by kerry_s on 2007-06-20
What you need to do is install a terminal file manager, so you feel more comfortable.

sudo apt-get install mc

when you get stuck at the command line just type> mc or sudo mc <if you need to do something as root like edit the xorg.conf.
it will save you alot of typing.

---

