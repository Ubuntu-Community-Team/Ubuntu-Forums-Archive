---
title: "Can't Unmount Drive"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by bigbudz on 2008-04-04
Hello, I'm using the default Bittorrent client on Ubuntu to download large files to my external USB drive. I stopped and closed a few before they were finished and went to unmount the drive and I get a message saying "an application is preventing the volume 'New Volume' from being unmounted." 

I tried unmounted in the gnome terminal : sudo umount /media/New Volume, but I get, the device is busy, device is busy  followed by media/New not found and Volume not found. 

Can anyone help? There is the 2nd time this happened. Last time I restarted and it recognized a socket was open and closed it. I guess worst case I can do that again, but I'd like to know why I keep getting that error.

---

### Post by stefangr1 on 2008-04-04
I have that too sometimes, I believe it's normal. You shouldn't pull it out without unmounting though, just shutdown or reboot the pc.

---

### Post by MrFSL on 2008-04-04
The "sync" command from any terminal will write any buffered information to the drive. I would do this before I unplugged it.

More then likely though, you can simply end the process that has locked the drive.

From the Terminal type:
```
ps -e
```

This should give you a good listing of running apps.

Find the one locking the drive and then use a "killall" statement to end it.

Hope this helps.

---

### Post by LeoSolaris on 2008-04-04
I reread and my post was assuming less tech skill than you're showing.

Sorry bout that!

---

### Post by bigbudz on 2008-04-04
> **MrFSL said:**
> The "sync" command from any terminal will write any buffered information to the drive. I would do this before I unplugged it.

More then likely though, you can simply end the process that has locked the drive.

From the Terminal type:
```
ps -e
```

This should give you a good listing of running apps.

Find the one locking the drive and then use a "killall" statement to end it.

Hope this helps.

There seems to be alot of stuff running. If I had to guess I'd say it would be  5536 ?        01:00:05 mount.ntfs-3g. But Im not sure.  I just started using Linux and alot of this doesnt make sense yet so Im just going to restart the computer for now. Thanks

---

### Post by MrFSL on 2008-04-04
If you can't easily tell from looking at the running processes *i.e. ps -e* then I suggest using fuser:

```
fuser -v /media/New\ Volume
```

This will show you everything accessing that folder.
You can then kill the process using its PID or using killall and the app name.

For more information about fuser type:
```
man fuser
```

---

### Post by bigbudz on 2008-04-04
It definitely had something to do with the mount.ntfs-3g command. Now my Vista laptop thinks the external drive is corrupt because the file system has been changed to ntfs. I thought a file system was just folders and files in them and pretty universal to all OS but I guess not. What kind of filesystem does Vista use? How can I change it back? Is there a way to use the external drive with both OS?

---

### Post by burnetbj on 2008-04-04
Hello there 

I am very new to linux and have had unmounting issues before. The fix I used was just booting into live CD then you can unmount what ever drive you want in Gparted then when reboot into hdd they will be fine the reason they wont unmount is they are busy they will stay busy untill you stop using them ......I realize there is a knowlage way to do this but this will fix it for now till some Linux champs can help you with a more proper way ......hope this helps

---

