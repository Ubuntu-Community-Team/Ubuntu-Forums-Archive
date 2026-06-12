---
title: "Video Driver Needed?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-07-15
Hello once again. I'm have a video issue with my laptop ( Sony Vaio FS ) The FPS on anything is very low. The screensavers are choppy, my video's are choppy. I tried playing Dazed and Confused and the video was very choppy. Well, I did:
```
 lspci 
```
and I see I have a Intel. Corp. Mobile Graphics Controller (rev 03)
I think this is my video card and i'm not sure what the rev 03 means. Anyway, is there a video driver i need to install? When I had windows, everything seemed fine and clear.

---

### Post by autocrosser on 2006-07-15
Take a look at /etc/X11/xorg.conf & see what the "Section Device" has as a driver. If it's nv, you can do quite a bit--if it's ati, not quite as much----in any case, see what it says & post it here......

---

### Post by Kobalt on 2006-07-15
And also, what kind of a video was your movie ? A .avi , .mpeg ? Is it a DivX or not ?

---

### Post by wildseven on 2006-07-15
Hello. I appreciate both of your replies. Now to answer them.

Under Section Device it says
```
 Secition "Device"
         Identifier       "Intel Corporation Intel Default Card"
         Driver           "i8l0"
         BusID            "PCI:0:2:0"

```

And the movie I am playing is a DVD. Im guessing the standard format? I'm not quite sure what the standard formate for a DVD is lol.

---

### Post by adam.tropics on 2006-07-15
Ok so I am happy to be corrected, but it sounds like a DMA (direct memory access) issue to me. There is an excellent guide to it [here]("https://help.ubuntu.com/community/DMA") which should see you right.

---

### Post by wildseven on 2006-07-15
Thank you adam for your reply. I have read the link and when i do:
```
sudo hdparm /dev/hdc
```
it says There is no File or Directory.
What should I do?

---

### Post by adam.tropics on 2006-07-15
Well I get 

```
adam@adam-laptop:~$ sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 [COLOR="DarkOrange"]using_dma    =  1 (on)[/COLOR]
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
```

---

### Post by wildseven on 2006-07-15
```
wildseven@ubuntu:~$ sudo hdparm /dev/hdc
Password:
/dev/hdc: No such file or directory
wildseven@ubuntu:~$

```

Thats what i get.

---

### Post by adam.tropics on 2006-07-15
oh ok, me idiot!

Check where your drive is, it may not be hdc. The graphical way...just go to Disk Manager, highlight the drive, and it will say underneath it whether it is hdc

---

### Post by wildseven on 2006-07-15
heh i got it thanks!

it was /hdb ^^

edit// LoL. Well i guess it's on. Im still getting the problem i had before. Oh well, i guess my laptop sucks haha. Im gonna eventually install on the new MacPro's. 
Thank you for the help you. It was greatly appreciated.

---

