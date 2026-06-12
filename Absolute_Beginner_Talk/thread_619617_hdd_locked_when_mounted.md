---
title: "hdd locked when mounted"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-21
I am trying to mount a 500gb hard drive as a 2nd drive on Ubuntu Server. Whenever I mount it it comes up locked and I cannot access or create folders in it.  I intend to use it to share files with.
Thanks for any help.

---

### Post by Inxsible on 2007-11-21
> **davidexe said:**
> I am trying to mount a 500gb hard drive as a 2nd drive on Ubuntu Server. Whenever I mount it it comes up locked and I cannot access or create folders in it.  I intend to use it to share files with.
Thanks for any help.
When you say Ubuntu Server, do you mean you have a server version installed? Do you have the GUI ?

You probably need to assume ownership of the mount point. Try this command:```
sudo chown -R <your username>:<your username> <path to mount point>
```

---

### Post by davidexe on 2007-11-21
I tried that and it appeared to work. Then I rebooted and it came back locked.  I tried that command and it did not work.  I checked and in the GUI and it was not mounted. So, I remounted it and now can access it to read but cannot change it.  The lock reappeared on bootup and has not gone away.

I have to get off now and will work more on it later.

Thanks,

Davidexe

---

### Post by taurus on 2007-11-21
What filesystem is that 500GB harddrive and how do you mount it, from a terminal or through /etc/fstab?

---

### Post by davidexe on 2007-11-22
it was formatted in extended 3  and was mounted through the GUI.

---

### Post by natehatewindows on 2007-11-22
mount it htrough fstab. 

it should look something like:

```
/dev/sdax  /media/storage ext3 defaults 0 1
```

you will need to put it where you want it to mount, if you do it in media it will automatically put a link on your desktop (it sounds like your using a gui). but you need to make a folder first.

be sure to make a backup beofre editing fstab

---

### Post by natehatewindows on 2007-11-22
ok that was really confusing lets try again....

first 

```
mkdir /media/WHAT YOU WANT IT TO BE CALLED
```

and then 

```
sudo gedit /etc/fstab
```

and then put the line i gave you with the correct /dev/    , and path (the path to the file you just made) 

reboot

---

### Post by davidexe on 2007-11-22
I came in this am and the hdd is unlocked. It was locked when I left it. ??  Anyway, I then could map to it but not change it.  I changed the permissions and BINGO, that part is working. I can now map a Windows XP-Pro machine to it and change/add folders.

THANKS for the help.

Now I will begin the next phases..  1) get 2 user groups with different access rights set up.
2) to get the RAID-1 working to the other 500gb drive. 
3) FTP site
4) VPN.

Again, thanks much and I am sure I will be back to bother with more questions.

HAPPY THANKSGIVING!

---

### Post by natehatewindows on 2007-11-22
if you post the output of ```
fdisk -l
``` i can tell you exactly what you need to add to fstab

---

### Post by natehatewindows on 2007-11-22
sweet! good luck!

---

