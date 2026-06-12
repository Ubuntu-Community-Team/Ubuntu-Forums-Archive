---
title: "Ubuntu USB Questions"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-06-23
Ive installed ubuntu on my 4gb usb drive using this guide: [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

I got it working and everything, I just wanted to know a little about what I can and cant do. Im assuming since it thinks its a live distribution (even though it saves changes) I cant update it right? Which would mean, I cant have use that great feature in 7.04 to auto mount my windows disks. 

So, I really am interested in three things:
1: Is there anyway for me to update to gain any of the new features or stability (not like thats really an issue)
2: If no, is there any way for me to permanently mount my other disks?
3: Is there another way to do it via USB? Like, since I have such a pretty big thumbdrive (4gb) could I just install it to the thumbdrive and still have it work? Heck, I even have a 40gb portable HDD that I could install it to if that would work. 

Well, as always, thanks for any help thats given!

---

### Post by BobCFC on 2007-06-23
When I go to System->Preferences->Sessions I have a Startup Program called update-notifier which runs every time I log into gnome.  Maybe if it thinks it is a liveCD it isn't being run.

Try typing 

```
update-notifier
```

at the terminal to see if you can run it.  (Assuming you have an internet connection.)


To mount disks permanently you need to edit the file in /etc/fstab as root...

```
sudo gedit /etc/fstab
```


The first thing I would do is make a copy of this file in case you need to restore it.  Remember only root can touch it if you need to copy your old file back. So use sudo.

It seems daunting at first but you will get the hang of it.  You can use the exiting entires as a guide with copy&paste...  There are many tutorials about fstab.  Come back if you are stuck.


Sorry my old flash drive is too small I cannot try it myself to help you

---

### Post by say592 on 2007-06-23
Well, it thinks its a live CD because it is made from one. They said you have to use 610 because 704 wont work with saving information, and that is a big deal for me, because I am using this as my primary operating system for a little while.

---

