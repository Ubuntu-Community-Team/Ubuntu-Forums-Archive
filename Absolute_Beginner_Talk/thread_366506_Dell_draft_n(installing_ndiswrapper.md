---
title: "Dell draft n(installing ndiswrapper"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-02-20
I need some help installing the ndiswrapper.  On a website is tells me to type this command

sudo apt-get install linux-headers- `uname -r`

and this came up-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.17-11-generic


I have no clue what im doing and ever tutorial has something else i need to go to  another tutorial to find out how to do something.

I'm not sure if i need to replace `uname -r` with something else because i don't know what that means

---

### Post by ashmew2 on 2007-02-20
I dont think there's any space between linux-headers- and `uname -r`
Try again!!

---

### Post by ashmew2 on 2007-02-20
`uname -r` means that it will automatically type your kernel's version.
Or u can also type the entire code "2.6.XX.X..X" or whatever if u dont like that command :D

---

### Post by grogger13 on 2007-02-21
okay well, now im on the second command:
ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

im not sure how to write this, i am running 2.6.17-11-generic

---

### Post by ashmew2 on 2007-02-21
lol whenever you are typing commands from a website , just take one line at a time
and u SHOULD copy paste them into the terminal , For example :

Try copying this (by selecting and right clicking copy )
```

sudo apt-get update
```

Go to your terminal and right click and PASTE.

Also , in Ubuntu , u can press ur middle mouse button (or scroll wheel) to paste text here and there.

---

### Post by ashmew2 on 2007-02-21
and wherever it says <kernel version> , you should replace it with `uname -r`
As i said earlier, the command `uname -r` tells the computer your kernel version.

---

### Post by grogger13 on 2007-02-21
i actually did copy and paste that, 

For VERSION im suposed to put my version of linux, what is that, generic?

---

### Post by grogger13 on 2007-02-21
update- got the link performed-

now im onto extracting it, and i was wondering if it matters were i extract it, i was planing on putting it in my home folder, but where is that best place to put these types of files.

---

### Post by ashmew2 on 2007-02-21
If u extract files from an archive (.tar.gz , .zip , .tar.bz2) i think using a fodler on desktop is best thing  so that after installing it u can delete that folder...Atleast i do so :)U can put em anywhere u like and if some program asks u where to install you SHOULD select home directory (/home).

---

### Post by ashmew2 on 2007-02-21
> **grogger13 said:**
> i actually did copy and paste that, 

For VERSION im suposed to put my version of linux, what is that, generic?

No , for kernel version its (what i think) , 386 (on normal computers 32 bit and intel processors)
686 (64 Bit intel processors)
k7 (AMD processors)
Generic etc are further types (i aain think lol)

so if u encounter something like <kernel version> , u can simply find it out by typing in a terminal
uname -r

and if its a part of some other command , 

`uname -r`

so it automatically supplies the kernel version eliminating your need to do so..

I hope u get it :P

---

### Post by tjtansey on 2007-02-21
Grogger,
What wireless card are you using?  I've gone through the install so many times, I can probably give you some guidance

---

### Post by grogger13 on 2007-02-21
/lib/modules/VERSION/build should be a link to the kernel source, where VERSION is the version of the kernel you are running.

heres what they put on the web site.  im not sure, but VERSION and <kernal-version> are different.  i typed in 
/home/mike# ln -s /usr/src/linux-`uname -r` /lib/modules/2.6.17-11-generic/build

was that the right command, it check and there is a directory for it and there was no error message

---

### Post by grogger13 on 2007-02-21
i have the dell draft n 1500 on an E1705

---

### Post by grogger13 on 2007-02-21
followed tutorial up to make and i get a bunch of errors.

make distclean //seemed to work fine without a hitch and then it says type make, is it sudo make?

---

### Post by ashmew2 on 2007-02-21
yep it is sudo make

---

### Post by grogger13 on 2007-02-22
so i think i have my card installed becuase when i type iwconfig i get this:

```
mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  Nickname:"sandiego"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=270 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

