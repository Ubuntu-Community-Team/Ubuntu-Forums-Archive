---
title: "A few questions (Reading NTFS partitions, WLAN perf, etc)"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by DoubleEcho on 2006-03-21
I'm a new Ubuntu user as of this weekend. I installed it with a dual boot configuration with Windows XP, and played around with getting MP3 and streaming audio working. Synaptic Package manager is pretty nice! I used to run an OpenBSD server out of my house as a web server hosting my site (with alot of help from my friends), so I'm not a complete newbie to command lines, ssh terminal work, etc, though I'm not the greatest. However, I've got a few newbie questions:

1. I know that you can give read/write access to NTFS partitions in Ubuntu, but is this safe to do? From UbuntuGuide.org it shows you how:

[B]Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?
 
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windowsTo mount Windows partition 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222To unmount Windows partition 
sudo umount /media/windows/[/B]

I've read that it's unsafe to do this (especially with Write access) and could damage your NTFS partition. I backup with Ghost 8.2 so it's not a huge deal, but I want to make sure I don't run any risks. I mainly want to do this to swap files between the OSs and use WINE with emulator programs. 

2. I noticed that Ubuntu picked up my wireless card and wireless config pretty easily, and I was pretty impressed by this. However, I noticed that the wireless performance is kind of slow. If I try to open a page, it will sit there for about 10 seconds sometimes and show "finding site". I thought it could be something with DNS, so I tried to manually configure the IP, GW, and DNS. When I did this, I lost the wireless connection, and I couldn't get it back with DHCP. I've got a Netgear MA311 (which I've heard is user friendly with Linux as far as compatibility); Should I be using a different driver?

3. Say for instance that I want to try running Warcraft 3 with WINE; Do I need to install WC3 to my /home directory, or run it from the NTFS partition?

4. Is there anything you can recommend to me (projects, etc) that I should try to get myself better acquainted with Ubuntu?

Thanks for any advice in advance! From what I've seen browsing these forums, y'all are a very helpful community.

---

### Post by Stealth on 2006-03-21
1. NTFS reading is safe, I do it all the time, using my Music folder and everything in Amarok, having it transfer to my iPod and all...WRITING however, is very experimental, and causes performance issues and corruption with some people...

2. What did you do to change it?

3. Install it with wine into your Wine's fake windows drive, you can't run it off the NTFS partition (because of registry values, dlls, etc.)

4. mmmm...hang out around here! :D

---

### Post by Brunellus on 2006-03-21
1) reading NTFS is safe.  writing is NOT.  DO NOT WRITE TO NTFS unless you enjoy irrecoverable filetable corruption.  you've been warned.

2)  Wireless connections have been known to be flaky;  I really don't know much about your particular situation, but there are plenty of variables, chief of which would be the quality of the radio signal. 

3)  Probably better to run it from /home.  HOWEVER, it may not install/run at all using plain old WINE.  I believe Cedega supports it, but that's neither free nor Free (that is, neither gratis nor libre).

4)  Buy a good book.  Learn the command line.  hang out on these forums.  Read man pages.  use google.

---

### Post by DoubleEcho on 2006-03-21
[QUOTE=Stealth]1. NTFS reading is safe, I do it all the time, using my Music folder and everything in Amarok, having it transfer to my iPod and all...WRITING however, is very experimental, and causes performance issues and corruption with some people...

2. What did you do to change it?

3. Install it with wine into your Wine's fake windows drive, you can't run it off the NTFS partition (because of registry values, dlls, etc.)

4. mmmm...hang out around here! :D[/QUOTE]

Ok, I can see why NTFS write is bad, read should do what I need. 

As far as the wireless config, I went into the Network tools in Ubuntu (I believe it was under Administration) and set the IP, GW, DNS manually. That's when the wireless signal wasn't available. I then tried to set it back to DHCP and when it tried to reconfigure it, it hung and then told me it couldn't connect. In WinXP my signal is usually 95-99% as well as the link quality. If I could run the wires I would, but seeing as I live in an old Victorian house converted into an apartment, I doubt they'd let me drill and run cable :) 

Any books you'd recommend, Brunellus?

---

### Post by Stealth on 2006-03-21
On the network thing, do this in a commandline:

```
cd /etc/network/
```

and

```
ls
```

You might be able to find a backup of a file called "interfaces" (probably called interfaces~). Then you can:

```
sudo rm interfaces
```

and 

```
sudo mv interfaces~ interfaces
```

To delete the current non-working configuration, and then rename the old one for use again.

---

### Post by Sutekh on 2006-03-21
[QUOTE=DoubleEcho]
1. I know that you can give read/write access to NTFS partitions in Ubuntu, but is this safe to do? From UbuntuGuide.org it shows you how:

[B]Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?
 
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windowsTo mount Windows partition 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222To unmount Windows partition 
sudo umount /media/windows/[/B]

I've read that it's unsafe to do this (especially with Write access) and could damage your NTFS partition. I backup with Ghost 8.2 so it's not a huge deal, but I want to make sure I don't run any risks. I mainly want to do this to swap files between the OSs and use WINE with emulator programs. [/QUOTE]

Just so you know the commands you have in bold **do not** allow write access to the NTFS partition.  Those commands only setup read/execute permissions for the mounted NTFS partition.  The key is the umask setting.  umask=0222 doesn't allow writing to the NTFS.

Also, because the kernel doesn't have NTFS write support enabled, even if you did change those permissions, the drive would still reject it.  You need a special program to try to write to NTFS.

---

### Post by Brunellus on 2006-03-21
I'd look into an external antenna, if feasible.  

As to books, my personal reference is "How Linux Works" by Brian Ward (No Starch Press).  Not distro-specific, not intelligence-insulting, and command-line centric. Good for getting up to speed with the guts of what's really going on quickly.

---

