---
title: "Adding an Additional Hard Drive"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by soburriw on 2007-01-01
I replaced my primary system, a Fedora Core X workstation, with an Ubuntu 6.10 workstation. The existing drives (/dev/hda and /dev/hdb mounted on "/" and "/home" respectively), were removed from the old system, and added to the new. Basically to preserve my existing data, and add capacity to the new machine. So, I created a /media/data folder, and modified the /etc/fstab file with the following:

/dev/hdb1       /media/data     ext3    defaults 0     0

So far so good... this gets me access to my "/home" directory... from the old machine.

The problem that I'm running in to, is that the drive is automatically mounted, and shows up on the desktop with the label "/home". I tried to rename it, no luck. I tried umounting the disk, and then renaming the label... still no luck. I'm hoping it's something really simple I overlooked. I don't won't to have to reformat the dev, losing my data, just to give it a new label.

Thanks in advance for your help!,
Bill Burriss
[email]bill@burriss.com[/email]

---

### Post by Azakus on 2007-01-01
Did you try changing the ownership of the drive to your username? Otherwise, the drive is really mounted as read only to all but root then. Try this in the console:
```
sudo chown -R replacethiswithyourusername /media/data
```

---

### Post by soburriw on 2007-01-03
Azakus, thanks for your reply. I tried that, and it still didn't work. However, I did stumble across a fix at the following web site: 

[SpiralBound]("http://spiralbound.net/2006/11/28/working-with-disk-labels-in-rhel/")

The fix basically took two steps. Open a terminal, as root, and type the following (substituting your own device to relabel... of course.);

```
e2label /dev/hdb1 data
```

Then edit the /etc/fstab file, and modify the mount line as follows;

```
LABEL=data      /media/data     ext3 defaults 0 0
```

That did the trick. Now when the machine boots up, I see a mounted drive called "data", rather than a mounted drive called "/home". It's the little things that drive you crazy, eh?

Thanks again. Bill

---

