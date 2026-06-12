---
title: "dvd help"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-30
I just did a fresh install on this computer, and so far everything is working fine except for my dvd-drive. It's set up to dual-boot, and it shows up in windows, but in ubuntu, it's nowhere to be found. what can i do to fix this. And before anyone asks, I have tried  rebooting to see if it can solve the problem.

---

### Post by shof2k on 2005-12-30
You don't need to reboot to get things working in linux, that's a windows feature :).  

Try putting a dvd in the drive and see if an icon appears on the desktop.  If so, right click and select 'open'.  This will show the path to your dvd and confirm that Ubuntu can see it.

---

### Post by iand675@gmail.com on 2005-12-30
no, I cant even open up the dvd drive by pressing the button on the physical disk, it wont open. It does open when im running windows. any thoughts?

---

### Post by shof2k on 2005-12-30
Fraid you got me stumped there.  You could try booting with an ubuntu live disc and see if that works.  

My gut feeling is that ubuntu is not releasing the drive to open it up.  I hope someone else can help you.

apologies

---

### Post by kaamos on 2005-12-30
You can get the tray to open with this command in terminal
```
sudo eject
```
Then insert a disk. Does the cd/dvd spin in the drive? Do you get the desktop icon?

---

### Post by iand675@gmail.com on 2005-12-30
```

ian@ubuntu:~$ sudo eject
Password:
eject: tried to use `/dev/hda' as device name but it is no block device
eject: unable to find or open device for: `cdrom'
ian@ubuntu:~$

```
here's the output.
but here's the wierd part: the cd rom drive that shows up is actually some strange reference to the partition that ubuntu is installed on. same size, non-ejectable, etc. Why wouldn't this dvd drive show up at all? Do I need to change something in the bios?

---

