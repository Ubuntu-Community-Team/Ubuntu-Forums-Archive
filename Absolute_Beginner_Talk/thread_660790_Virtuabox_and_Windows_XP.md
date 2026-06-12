---
title: "Virtuabox and Windows XP"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by DoktorMHz on 2008-01-07
Hi,

I created an ISO file of my Windows XP Pro SP2 CD by typing 

# dd /if=/dev/cdrom of=xp.iso

After that I created a New Virtualbox session WINDOWS XP, assigned a new HardDisk (WindowsXP.vdi), and pointed the installation to my XP.ISO files.

In the process of copying the files I get several errors:

System cannot copy file xxxxx.xxxx

I checked my Windows XP CD on another PC and the installation performs smoothly without errors.

First question:
Why my XP.iso is producing such errors?

Second question:
Can I use the CD directly instead of the ISO image?

I have been trying to install XP for a couple of days withous success.

Any help would be greatly appreciated.

Thanks

---

### Post by mister_pink on 2008-01-07
Not sure why it's giving errors, but I installed directly from the CD with no problems when I set up a virtual machine in VirtualBox so it should be fine.

---

### Post by Steve1961 on 2008-01-07
I also installed directly from a CD without any problems

---

### Post by DoktorMHz on 2008-01-07
I will try from the CD and let you know.

Thanks

---

### Post by lvleph on 2008-01-07
In the CDROM selection you can select an ISO. I installed from both the CDROM and an ISO. My CDROM was giving me errors, and so I tried the ISO. Basically, the opposite of your problem.

---

### Post by DoktorMHz on 2008-01-07
Well.....it seems that both the ISO image and the CD are giving me errors. This is strange because if i use the CD on a fresh Windows install no errors are found whatsoever. So I assume there are some problems in the way Virtualbox uses the media. My Virtualbox version is the latest i downloaded from the website. Better day ahead, hopefully.

---

### Post by mdpalow on 2008-01-07
> # dd /if=/dev/cdrom of=xp.iso

Looking at your 'dd' command - it appears to be wrong. First, you have a '/' in front of 'if,' which is not right and I'm confused about your 'of,' which doesn't appear to be a good destination for the backup.

try something like this and see if it's any better:

```
dd if=/dev/cdrom of=/home/$USER/Desktop/xp.iso
```

That should hopefully put the .iso file on your desktop (you can move it after). If not, change the '$USER' to your login name (ex: /home/john/Desktop)

---

