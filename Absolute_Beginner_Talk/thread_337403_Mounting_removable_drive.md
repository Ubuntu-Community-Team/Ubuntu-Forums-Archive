---
title: "Mounting removable drive"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by noisc on 2007-01-12
I want to change the default mount point when I hot-plug in my removable USB drive. 

Here's my problem: my USB drive has the label "WD40", so by default it mounts to /media/WD40. I've added some lines in my /etc/fstab:

```
# 40GB WD Passport drive
LABEL=WD40 /media/music vfat noauto,users,rw 0 0
```

Now when I plug in my USB drive, it mounts back to the default /media/WD40, which is what I **don't** want it to do. (I've already done sudo mkdir /media/music)

So it's not mounting to where I thought I told it to. Can anybody help me out? If it helps, on the list of drives on the left of Nautilus, it lists a "music" drive, and when I double-click it, it says "Unable to mount the selected volume.", and the detailed error message is "mount: can't find label=wd40 in /etc/fstab or /etc/mtab".

---

### Post by rai4shu2 on 2007-01-12
I'm not completely sure, but I think what you want to do is described here:

[http://www.debuntu.org/comment/reply/145](http://www.debuntu.org/comment/reply/145)

---

### Post by noisc on 2007-01-13
Right, I only read the vfat section of that link you posted (my drive is fat32), but it talks about changing the label of the drive. And yes, I could change the label of my drive to reflect where I wanted it mounted. However, I'm also trying to learn about linux, and I thought that editing my fstab file would allow me to explicitly tell the OS where to mount the drive. I want to learn how to do this.

Besides, suppose I didn't want my drive mounted in a subdirectory of /media. I don't believe simply changing the label will allow me to do that. But editing the fstab should allow me to that, right?

---

### Post by rai4shu2 on 2007-01-13
Either way, you're going to be using hal to mount the device. So, either you relabel or you create a symlink. To do a symlink, you would do something like this:

sudo ln -s /media/WD40 /media/music

---

### Post by noisc on 2007-01-13
Thanks for your responses.

Ok, I'm a little confused. I had to google/wikipedia some of the terms and commands you used, but if I use sudo ln -s, it creates a 'symlink' as you said, right? Essentially it creates a bunk of links in a new folder, but the actual files stay in the original location. Any reads/writes directed to the symlinks are redirected to the original location in the filesystem. Isn't that more complicated than what I want to do? I just want to make a user-defined mount point.

I am essentially trying to do what is outlined in [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab]("http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab") under the 'fstab syntax' section. It seems pretty straightforward, but I guess I messed something up because it's not working. 

For example, for one of the partitions of my hard drive, I have a line in fstab that looks like

```
UUID=4594-0C2A  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```

Now if I change **/media/sda5** to **/media/newlocation**, I've essentially changed where this partition is located, right? There is no footprint of the drive left in /media/sda5 (like I believe a symlink would leave). Why can't just add a line in fstab like this for my removable media?

A very simple solution for me would be to tell ubuntu not to automatically mount removable drives, and then I could manually mount the device to wherever using mount. But that's undesirable because I have to do it *every time I plug the device in*. 

Isn't there a simple way to tell linux to mount automatically to a specific location? I though editing the fstab would do this. I feel like I've just got the syntax wrong or something.

---

### Post by bodhi.zazen on 2007-01-13
In a nut shell editing fstab is the way to go for your hard drives.

Removable devices, however, are different.

If you put an entry in fstab for a removable device you will then need to mount it manually ...

The easiest solution is to change the label of your device.

---

### Post by Crakie on 2007-01-13
I am pretty much a beginner myself, but I have been fooling around with fstab. I support your reasoning Noisc, and it would have been my solution as well. As this fails nonetheless, I can only offer you a few thoughts on what *I* would have tried next.

- The first thing that came to my mind, is whether there is something going wrong with case-sensitivity. You have 'WD40' as a label in fstab, but the error message lists 'wd40'. 

- Is fstab the right place for removable drives, since they will not be present always at boot?

- If fstab is ok, is it possible to identify your drive by other means than its label? By UUID or by path (/dev/???), perhaps?

Good luck and hopefully someone more knowlegdable comes around :)

---

### Post by noisc on 2007-01-13
[QUOTE="bodhi.zazen"] In a nut shell editing fstab is the way to go for your hard drives.

Removable devices, however, are different.

If you put an entry in fstab for a removable device you will then need to mount it manually ...

The easiest solution is to change the label of your device.[/QUOTE]

I see. That's unfortunate. So there's no way to hot-plug a device and have it automatically mount to a directory that's not a subdirectory of /media, then? I'm surprised there's no (obvious, non-hackish) way to do this. I understand now that I can put a line in fstab to mount it somewhere else, and then mount it there manually. 

By the way, bodhi.zazen, kudos on your howto I linked to in my previous post. It's quite thorough.

[QUOTE="Crakie"]- The first thing that came to my mind, is whether there is something going wrong with case-sensitivity. You have 'WD40' as a label in fstab, but the error message lists 'wd40'.[/QUOTE]

As I understand it, mlabel (the command I used to change the label in the first place) uses all capitals no matter what. So the label is WD40 even though that particular error message from Nautilus says it's wd40. I *did* actually try to change LABEL=WD40 to LABEL=wd40 in fstab, and I got a different error message, essentially saying that it couldn't find a device with a label wd40. 

[QUOTE="Crakie"]- Is fstab the right place for removable drives, since they will not be present always at boot?[/QUOTE]
Well, I guess we've learned from this thread that you could do without going into fstab. But I believe there is an advantage to putting some code in fstab. So suppose I plugged in my removable device, and I wanted to mount it manually. Without doing anything to fstab, I could say something like
```
sudo mount -t vfat /dev/sdb1 /music
```
and my drive would be mounted to /music, though I'd have to type this command in every time I mounted it. 

Now if I kept a line in fstab like
```
LABEL=WD40 /music vfat defaults 0 0
```
then when I plugged in my device and wanted to mount it, I could simply type
```
sudo mount /music
```
and furthermore, if I included a 'user' or 'users' option in the fstab line, I wouldn't even have to sudo it. 

Anyway, I hope I got all that right. If not I'm sure somebody will come along to correct me :)

[QUOTE="Crakie"]- If fstab is ok, is it possible to identify your drive by other means than its label? By UUID or by path (/dev/???), perhaps?[/QUOTE]
I did try this. I did try to go by UUID and path. Neither worked either.

Anyway, thanks everyone. I certainly learned a lot here :D

---

### Post by bodhi.zazen on 2007-01-13
noisc

Add this to ~/.bashrc:

(mmusic for mount music, use what mnemonic you wish)

mmusic='mount /music'
umusic='umount /music'


Then you can mount/umount with mmusic and umusic

HTH

> By the way, bodhi.zazen, kudos on your howto I linked to in my previous post. It's quite thorough.

:redface: Thanks, glad I could help.

If you would like to hack further you will need to configure hal, udev, and/or gnome-volume-manager. To be honest I found that process difficult and not worth the effort ....

There is a link to udev in my how-to on fstab ....

Good luck :)

---

