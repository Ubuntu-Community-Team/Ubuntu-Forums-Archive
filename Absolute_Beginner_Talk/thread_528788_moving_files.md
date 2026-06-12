---
title: "moving files"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-18
when I try to move files from one partition of my hard drive to another, an error saying that I don't have permissions pops up.

---

### Post by taurus on 2007-08-18
You cannot write to directories outside your $HOME.  To do that, you need to be root so use the sudo command instead.

```
sudo mv filename destination
```
Then, use the same password that you log in with when it asks you for it.

---

### Post by kwacka on 2007-08-18
Which means that you are attempting to write to a directory that you don't have permission to write to; usually no need to do this unless you're trying to install an application or edit a config file (or similar).

If you really need to:

In a terminal type:

1. gksudo nautilus, nautilus will open with root privileges

or

2 sudo cp file.name /usr/doc/file.name (for example)

---

### Post by hyper_ch on 2007-08-18
or you could alter the ownership of that folder... but you should really know what you are doing before attempting that.

---

### Post by mysticmatrix on 2007-08-18
Is the other hard drive partition a NTFS partition, i.e. one used by windows? If so is the case, you'll need to install a program NTFS-3g to access it.

Go to Applications --> Add/Remove. Then search for NTFS under All availible programs and Install NTFS-3g.

---

### Post by seren6ipity on 2007-08-18
Thanks! I was unable to cut and paste certain installations but mv worked.

---

### Post by jon557 on 2007-11-21
Hi,

I think my laptop is going to be the most troublesome install of Xubuntu ever. Its a toshiba 1Ghz 1.25GB RAM, R100. Very small, and so it has no floppy or cdrom.

I am familiar with unix and linux but not too much with the commands etc.

Anyway, hopefully you can help me.

I have got everything prior to the instructions under " HOWTO: Install Edgy 6.10 from an .iso file". For a while the istaller couldnt find the iso, but its fine now.

I get an error during the install saying my Kernel is missing modules and was most likely downloaded from a mirror site. (very intelligent observation it made there, as its right). I'm trying Xubuntu 7.10 on my laptop. I have a 1GB partition where the ISO is stored, and about 20gb of unallocated space ready.

The kernel i used was the one linked from the instructions above at [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

Is it because on that link it says the date for the kernel was october 2006? And my Xubuntu is 7.10?

This is a mission, any help would be appreciated!

Thanks, Jon

---

### Post by jon557 on 2007-11-21
WOOOOOP!!!

Sorry, forget my last message! I have just realized the link in the instructions was for EDGY and my version is based on GUTSY! So I changed the url in the middle to
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/")

I have learnt so much tonight!

All seems to be installing well now!

Cheers anyway.

Jon

---

### Post by jon557 on 2007-11-22
ok, false alarm. doenst work! installed it ok, but only works in commandline.

Spoke to an expert LInux guy at Uni and he said that my grphics needs tweaking, some parts wernt installed. And that Ububtu is very reliant on having the internet for updating, so i need to give it a network connection to the net and maybe it will work!

I shall try it tonight!

Jon

---

### Post by Jammy4041 on 2007-11-26
Thanks kwacka, the gksudo nautilus worked. It came in handy when I had to move stuff to the firefox folder.

---

