---
title: "Ignore recovery partition"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-09
I just finished a 7.1 install, but for some reason, gnome is mounting my ntfs recovery partition and putting an icon on the desktop. This is a small thing, and probably really easy to fix, but I can't seem to find any answers.

How do I keep linux from mounting this partition?

---

### Post by shareMenaPeace on 2008-01-09
Does anyone know is it safe to delete this partition?

btw. this bothers me too, so i disabled the desktop :)

terminal

gconf-editor -> apps -> nautilus -> preferences -> show desktop uncheck 

:popcorn:

---

### Post by hyper_ch on 2008-01-09
```

sudo nano /etc/fstab

```

And remove the recovery partition.

---

### Post by shareMenaPeace on 2008-01-09
Hyper, what would be the best way to delete this partition entirely?

Gparted?

thx

---

### Post by shareMenaPeace on 2008-01-09
Anyone can say if its save to delete this recovery partition?
When i watch it with gparted i see flags hidden and lba ....


thx

---

### Post by hyper_ch on 2008-01-09
that would not delete that partition but it would not mount it in Ubuntu.

---

### Post by shareMenaPeace on 2008-01-09
Why would i need this? It is liek 7gb huge ... and if its anything importend i can download every system tool from asus website again ... for installing vista i have a boot disc and patch disc.... i dont think this got touched ...

What i internal plan is to might update the bios, as it is VERY limited no advanced tab and such oddness....


hmmm

---

### Post by shareMenaPeace on 2008-01-09
attache dis a screenshot of the contents

---

### Post by indytim on 2008-01-09
A lot of the pc manufacturer's have taken to utilize a recovery partition in lieu of actual install disk for Windows (i.e. Dell).  If you trash your Window ops system, the recovery partition content will be utilized to re-build your Windows ops.  

If you are convinced that you will never need to re-install your windows ops, then go ahead and delete the partition through GParted Live.

My recommendation is to leave well enough alone until you're firmly ready to say adios to Windows.

IndyTim

---

### Post by Paqman on 2008-01-09
> **shareMenaPeace said:**
> what would be the best way to delete this partition entirely?


Gparted can do that, but not if the partition is mounted at the time.

---

### Post by Paqman on 2008-01-09
If you want to leave it intact, but have it not mounted then you'll need to comment out the entry for that drive in your /etc/fstab file.

Make a backup of your fstab (just in case):
```

sudo cp /etc/fstab /etc/fstab_backup

```

Open fstab
```

sudo nano /etc/fstab

```

Find the line which corresponds to your recovery partition and comment it out by putting # at the start of the line. Then Ctrl-X >Y >Enter.

That partition won't be mounted at boot any more after this.

---

### Post by hyper_ch on 2008-01-09
I mean it's only 7GB so is it actually worth deleting that partition and free the space?

---

### Post by shareMenaPeace on 2008-01-09
Ok thanx to you both, 
well im going to ask asus directly if i can get rid of this :D

I even will complain as i had trouble installing windows xp (ok very odd version though).
Maybe i even try to get money for the vista version which was pre installed :D

Cheers

:popcorn:

---

### Post by imaginal on 2008-01-09
This worked, but I can still see it in nautilis and have absolutely no reason to. Any way to just let it be ignored?

---

### Post by hyper_ch on 2008-01-09
what do you still see in nautilius?

---

### Post by shareMenaPeace on 2008-01-09
> **hyper_ch said:**
> I mean it's only 7GB so is it actually worth deleting that partition and free the space?

Yes it is, im on a notebook, ok i got 160 gb overall but to have liek 3 or maybe soon 4 os i need this space urgent.

vista or xp
linux
vm
OSX?

---

### Post by hyper_ch on 2008-01-09
> **shareMenaPeace said:**
> Maybe i even try to get money for the vista version which was pre installed :D

You'll have to not disagree to the EULA right after you bought the computer... so if it's a few days back now I don't think you can get money back.

---

### Post by imaginal on 2008-01-09
I still see the partition in nautilis. Can I hide it from myself? ^_^ I may need it someday if I sell the computer, but I certainly have no use for it now.

---

### Post by hyper_ch on 2008-01-09
did you alter the fstab?

---

### Post by imaginal on 2008-01-09
Yes. The desktop icon was gone, but I could sill see it in the left panel.

---

### Post by hyper_ch on 2008-01-09
well, fstab will only work after reboot or after remoutn of all partitions.

---

### Post by imaginal on 2008-01-09
I have some screenshots. It is just... everywhere. :-k

To clarify, it is not currently mounted. fstab editing went perfect.

---

### Post by rkd on 2008-01-09
I don't know whether it works or is safe, but this package's author claims it will hide individual partitions:

[http://ubuntu-tweak.com/about](http://ubuntu-tweak.com/about)

I know nothing about it -- I just found it in a quick web search for Nautilus hide partition

---

