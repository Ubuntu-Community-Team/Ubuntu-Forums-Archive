---
title: "Windows98 slave now shows no files!"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by RockinDolphin on 2007-01-11
Okay. I went through some stuff to get my Win98SE drive working as a slave so I could try to copy files to my new Ubuntu drive.  The drive with files in it ***was[B][I]***[/B][/I] there, but when I click on Windows (It shows '0' files, anyway.) Nothing comes-up. I then noticed it showed zero files.  The only thing I've done was try to get Macromedia Flash to install, and I installed something for my ATI Radeon 9200SE which doesn't show my screensaver right.

I went to atomfilms.com to look at some animation and stuff to see how the grahics went for that. Things weren't going to good because I couldn't get Flash to load, so I thought I'd look at a movie clip from my Win98 drive and there were no files! What's going on?

Kenny

---

### Post by RockinDolphin on 2007-01-11
Gparted shows that it's there with 37.--Gig used up on a 40Gig drive, so I reckon that means that nothing has happened to the files. Also, I tried rebooting and that changed nothing.

---

### Post by Albi on 2007-01-11
It's not mounted...I'm assuming it's a FAT32 drive?

If so,
cd
mkdir windows
sudo gedit /etc/fstab

and add this to the end of it

/dev/hda2       /windows     vfat rw,users,gid=users,umask=000,       0       0

Of course, replacing /dev/sda2 with the location of your windows partition, 

then reboot and just go to the windows folder (under filesystem) to access it

---

### Post by RockinDolphin on 2007-01-11
If it weren't mounted, then it wouldn't show on the tree, would it? I tried to mount it and it said 'windows already exists.", or something to that effect/ Do I need to unmount it? will that harm anything/make me lose data?

---

### Post by RockinDolphin on 2007-01-12
bump

---

