---
title: "Another Windows Network Share problem"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by leona on 2006-09-29
Hi there.

Running Ubuntu64 6.06.

I am trying to get my machine to auto mount a directory on my windows file server.

I've got this working in Suse no problem.

I can do it manually, but if I put the commands in the fstab file nothing happens it will not mount.

The manual commands I'm using
```
sudo mount //192.168.1.1/fileshare /home/leona/network -o username=files,password=xxx,fmask=777,dmask=777
```
the fstab line.
```
//192.168.1.1/fileshare  /home/leona/network/    smbfs   username=files,password=xxx,dmask=777,fmask=777   0       0


```
What is going wrong?  Is there a log I can look at to see the error?

your help much appreicated.

---

### Post by petri on 2006-09-29
Have you searched the forums? I found this [http://ubuntuforums.org/showthread.php?t=260251&highlight=automount+samba](http://ubuntuforums.org/showthread.php?t=260251&highlight=automount+samba)
take a look.

---

### Post by leona on 2006-09-29
Thanks petri, maybe I need to refine my search words then as I didn't find that, seems a bit over kill don't know why it just can't work the way its supposed to, but I'll try the workaround. sigh :(

Ok have done what the post suggested, rebooted and again nothing, it will not mount the share, but if I run the command / file "connectshares" from terminal it works fine.

This is driving me mad!

---

### Post by petri on 2006-09-29
Yes, it's annoying when things don't work as they supposed to. 

Your question is though quite advanced, are you aware of that you posted it at Absolute beginners forum? This might suite better at [Networking]("http://ubuntuforums.org/forumdisplay.php?f=136") forum.

Sorry my english if I use strange words :)

---

### Post by leona on 2006-09-29
Hi, thanks again, I was aware that I posted this in the beginers section, cos that's what I am, though I know 1 or 2 commands, I'm still finding my way around, I though I may be missing something simple, my worry about posting in a more advanced thread is that I'll not understand the replies :)

---

