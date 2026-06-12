---
title: "Downloading to a hard disk while in Live CD boot"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by aimpau on 2008-04-11
So, you've gotten your first ubuntu live CD...and you want to try downloading a lot of files from your new ubuntu OS but you want to save it to your desktop?

I just found this out recently and since I am a complete noob myself, i haven't figured out the command line syntax for this.

1. When you boot up to your desktop, you'll see your hard disk on the desktop, right click it then click mount.

2. Start up firefox, go to edit-->preferences and change the donwload to destination to /media/(your harddisk)/(your folder).

And that's it. Download files etc. to your harddisk while in Live CD boot.

BTW: I'm using xubuntu 7.10.

Just a request, can someone share to me what's the command line syntax for what I just wrote here?

thanks!

---

### Post by wolfen69 on 2008-04-11
it really wouldnt make too much sense to do that in terminal. you would have to have firefox open to get the link of the download, then do alot of typing. if firefox is open, why use the terminal. the command line is great, but for surfing, the gui is much better.

---

### Post by aimpau on 2008-04-11
Oh sorry. I wasn't clear. What I meant was about the mounting and stuff, not the firefox tinkering.

Thanks.

---

### Post by SOULRiDER on 2008-04-11
```
mount <device> <mount point>
```
Say you wanted to mount your second partition of the first SATA drive to a folder called "drive" in your desktop, you would have to do:
```
sudo mount /dev/sda2 ~/Desktop/drive
```

Remember: to mount you have to be root (thats why I added sudo) and the mount point has to be an existing directory.

---

