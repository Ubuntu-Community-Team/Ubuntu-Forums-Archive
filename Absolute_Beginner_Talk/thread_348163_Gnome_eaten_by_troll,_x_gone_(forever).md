---
title: "Gnome eaten by troll, x gone (forever?)"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-28
Something has really blow up.

I am using the live CD (dapper) to get to the 'net.

Gnome or X is gone ... gone ... gone

Other posters have said:

startx

and

sudo /etc/init.d/gdm start

but neither are working. I can't access my /dev/hda from the live-cd desktop. It says it's not mounted and can't be mounted.

I badly want to fix the gui, but haven't a clue. And even though I've used Ubuntu for a year now, I'm as much a newbie as when I began, because I'm not a software programmer, so have to follow others instructions.

As I have a year's worth of work on the hard disk, if I must reinstall Dapper, how can I keep my data safe? I have only dialup and nobody with an alternative install cd around me. All the other people I know use misscrowsoft and aren't interested in installing software to write an .iso.

---

### Post by taurus on 2007-01-28
Didn't your Gnome disappear right after you were playing around with the alsa source?

If you want to mount your Ubuntu from the LiveCD, run

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
```
And if you get an error from the last command, post the output of this command then.

```
sudo fdisk -l
```

p.s.  Any burner software in Windows can burn an ISO image file.  Don't need to install any extra stuff just to burn it.

---

### Post by Mark_in_Hollywood on 2007-01-28
OK, those instructions worked like a charm. The hdd is registered and I can access the stored info, do you know a way that I can write protect it so that if I can do a clean install, I can prevent it from being overwritten?

Better still care to have another crack at fixing the X/Gnome?

---

### Post by goatflyer on 2007-01-28
Or, if you want to try and fix your x server:

On the grub boot menu, choose  the 'recovery' start up.  You will login to a text shell.

Then

sudo dpkg-reconfigure xserver-xorg

answer all the questions with the automatic and default choices.

You should get your x back.

If not, please pose the x error here

---

### Post by Mark_in_Hollywood on 2007-01-28
sudo dpkg-reconfigure xserver-xorg

returned:

"conflicting actions --control and --remove"

---

### Post by goatflyer on 2007-01-28
> **Mark_in_Hollywood said:**
> sudo dpkg-reconfigure xserver-xorg

returned:

"conflicting actions --control and --remove"

Was that after all the questions?  Or right at the beginning?

If you managed to get it to go through all the setup-questions, it will have created a new  /etc/X11/xorg.conf based on your answers.

btw in that directory /etc/X11/ you can find all your previous xorg.conf backup files.  To use one of them, just


cd /etc/X11
sudo cp xorg.conf.nnnnnn xorg.conf

where nnnnn is the number of the backup you want to use.

---

