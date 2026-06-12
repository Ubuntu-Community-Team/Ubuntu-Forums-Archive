---
title: "I am not able to install 7.04 ?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by theem on 2007-08-06
The system where I am trying  to install 7.04 has the specifications below !!

[B]Pentium III 866/33 MHz
256 Ram
MBus Speed 133 Mhz
Intel 815 Chipset[/B] 

ubuntu boot runs successfully 
Clicked on the 1st option .. 
It started loading the a black screen poped up giving me the errors 
[ 246.297822 ]Buffer I/O error on devices fdo , Logical Block 0
 and the errors go on and on ...
.
.
.
.
.
.
.

What Should I do to install Ubunntu on my system ?

Please help !

---

### Post by jonathanmotes on 2007-08-06
Try using the alternate install disc. It often works when the live disc doesn't. You can download it at the same place ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), you just have to check the box below the "start download" button. The only disadvantage will be that you won't get to try it before installing on your hard drive.

---

### Post by theem on 2007-08-06
> **jonathanmotes said:**
> Try using the alternate install disc. It often works when the live disc doesn't. You can download it at the same place ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)), you just have to check the box below the "start download" button. The only disadvantage will be that you won't get to try it before installing on your hard drive.

Sorry but i can't download it because i have a very slow connection !! 

I have got this ubuntu installation disk today ?  :confused:

don't we have any other method so i could install it ?

---

### Post by southernman on 2007-08-06
It's been a while since I looked at the Livecd.

When you first boot it up, does it give you an option to use a text based installer? Seems I recall that option, but I've been up going on 30 hours playing with a new custom kernel. :/

---

### Post by theem on 2007-08-06
> **southernman said:**
> It's been a while since I looked at the Livecd.

When you first boot it up, does it give you an option to use a text based installer? Seems I recall that option, but I've been up going on 30 hours playing with a new custom kernel. :/


Nop It Didn't asked me for the text based installer !! 
How can i use that option in live cd ? 
it has the option to run a command by pressing "F6"
is there any command for that ? :(

---

### Post by sysikon on 2007-08-07
No, there isn't, I think...

There are other ways to do this.

1. Take a CD, go to a computer with a high speed internet connection, then download ImgBurn (google it), and make a bootable cd. (Assuming you're on Windows)

2. Search Ubuntu installation guide and boot from the iso itself (using Linux).

Trust me, I've had the same problem, just get the alternate disc and use that. Works great. Just make sure you install all your drivers correctly though.

Also, the logical block is probably 'cause it doesn't recognize the drive.

---

### Post by Inxsible on 2007-08-07
Did you burn the CD that you have? If so, at what speed ?

Did you check the CD for integrity?

Lastly, maybe your machine is not suited for Ubuntu. You should try the alternate CD as already suggested, or give Xubuntu a go which is a light weight OS.

---

### Post by theem on 2007-08-07
> **Inxsible said:**
> Did you burn the CD that you have? If so, at what speed ?

Did you check the CD for integrity?

Lastly, maybe your machine is not suited for Ubuntu. You should try the alternate CD as already suggested, or give Xubuntu a go which is a light weight OS.


I didn't burned the disk !! 
I got it from Cronicals i mean  ubuntu.com shipped it to me !! 

why my machine is not suited for  ubuntu ?  :confused:

---

### Post by hyper_ch on 2007-08-07
on that computer specs I'd rather advice to use Xubuntu instead of ubuntu... and also the alternate install cd instead of the livecd

---

### Post by Kingsley on 2007-08-07
An earlier release, Ubuntu 6.06, may give less trouble.

---

### Post by jonathanmotes on 2007-08-07
If you don't have access to a higher speed connection you could go to [http://www.bittorrent.com/download](http://www.bittorrent.com/download) and download the bitTorrent download manager. It will allow you to download Ubuntu over the course of a few days, and will continue the download where it left off if your computer is shut down or if your connection is reset.

You can download the torrent files here: 

For Ubuntu:
go to [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)
click on the "ubuntu-7.04-alternate-i386.iso.torrent" link in the list at the bottom of the page

For Xubuntu:
go to [http://torrent.ubuntu.com/xubuntu/releases/feisty/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/feisty/release/alternate/)
click on the last link

The torrents are small files that you can save on your desktop and open with the bitTorrent download manager. If your using Windows, the .iso image file should be stored in "My Documents/BitTorrent Downloads." As sysikon suggested, you can burn it to a CD using ImgBurn (from [http://www.imgburn.com/](http://www.imgburn.com/)).

---

### Post by K.Mandla on 2007-08-07
Do you have a floppy disc drive in your computer? Buffer I/O errors on fd0 usually suggest the system is trying to poll a floppy drive that doesn't exist. I get the same errors on my laptop because it doesn't have a floppy, but if I wait a few minutes, they quit and installation continues.

---

