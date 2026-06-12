---
title: "Need help with Linux Mint iso file"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-12-21
I am not sure how to get this Linux Mint 2.1 'Bea' on to a CD

The file(s) are in a small window on my desktop, with the invitation to 'extract'.

When I 'extract' it, it creates a folder with various files but K3b doesn't seem to find the 685MB file that it burns to the CD.

In the past I have successfully burned a few ISO CD's and I'm not sure why it doesn't seem to be going my way this time.

Any help will be appreciated.

---

### Post by aysiu on 2006-12-21
Don't extract the ISO. Select to burn a disk image, and then select the ISO.

**Edit**: Never mind. So you've burned ISOs before.

Linux Mint doesn't come with a .iso extension? What's the extension? .tar.gz?

---

### Post by meng on 2006-12-21
If you got it from here:
[http://lt.k1011.nutime.de/download.html](http://lt.k1011.nutime.de/download.html)
Then it's an iso.

---

### Post by L Campbell on 2006-12-21
> **meng said:**
> If you got it from here:
[http://lt.k1011.nutime.de/download.html](http://lt.k1011.nutime.de/download.html)
Then it's an iso.

Thanks and yes, this is where it came from.

---

### Post by bodhi.zazen on 2006-12-21
> **L Campbell said:**
> Thanks and yes, this is where it came from.

[list=number][*]Check the md5 sum.
[*]I just burned the iso last night without problems. I also use k3b. I launch from the CLI:[/list]```
k3b /path/to/LinuxMint-2.1.iso
```

HTH

---

### Post by L Campbell on 2006-12-21
> **aysiu said:**
> Don't extract the ISO. Select to burn a disk image, and then select the ISO.

**Edit**: Never mind. So you've burned ISOs before.

Linux Mint doesn't come with a .iso extension? What's the extension? .tar.gz?

Thanks. 

This 'window' on the desktop is titled ' LinuxMint-2.1.iso '

It consists of 3 folders and 2 files.

Should K3b be able to burn a CD from this, or do I have to 'extract' it?

---

### Post by meng on 2006-12-21
Forget the window/folder, just point k3b to the iso and let it burn.

---

### Post by L Campbell on 2006-12-21
> **bodhi.zazen said:**
> [list=number][*]Check the md5 sum.
[*]I just burned the iso last night without problems. I also use k3b. I launch from the CLI:[/list]```
k3b /path/to/LinuxMint-2.1.iso
```

HTH

OK, thanks, I tried that but got this error:-

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Coudl this be because I hadn't done the 'extract'  ?

---

### Post by riven0 on 2006-12-21
> **L Campbell said:**
> OK, thanks, I tried that but got this error:-

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Coudl this be because I hadn't done the 'extract'  ?

Perhaps there is something wrong with the cd-rw drive? :confused: Can you burn anything else on that drive?

---

### Post by meng on 2006-12-21
Did you check the md5sum?
How about just launch k3b (no arguments) and then use the app itself to choose the file.

---

### Post by bodhi.zazen on 2006-12-21
> **L Campbell said:**
> OK, thanks, I tried that but got this error:-

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Coudl this be because I hadn't done the 'extract'  ?

As has been mentioned, you do not need to extract anything.

K3b gives error messages when starting, but burns just fine. I do not recall them all as I ignore them :mrgreen:

If K3b did not start, have you burned an iso before with our cd bruner? is it working (? hardware failure).

---

### Post by L Campbell on 2006-12-21
> **meng said:**
> Forget the window/folder, just point k3b to the iso and let it burn.

I don't seem to be able to get K3b to see the file.

The only file it sees is:-

hadjaha-001a0ab1b9.desktop

Trust me, I have NO idea what that is.   :-)

---

### Post by meng on 2006-12-21
Where are you looking?

---

### Post by L Campbell on 2006-12-21
> **meng said:**
> Where are you looking?

I went to Applications - Sound & Video - K3b

Then, with the K3b window open, I click Home, then Desktop.

---

### Post by L Campbell on 2006-12-21
> **meng said:**
> Did you check the md5sum?
How about just launch k3b (no arguments) and then use the app itself to choose the file.


I launched K3b, told to to make CD image but it did nothing, as if it couldn't find an ISO file to burn.

---

### Post by bodhi.zazen on 2006-12-21
LOL Where did you save the .iso ? On your desktop ?

Browse to the location with k3b ;)

Desktop = ~/Desktop

---

### Post by L Campbell on 2006-12-21
> **bodhi.zazen said:**
> LOL Where did you save the .iso ? On your desktop ?

Browse to the location with k3b ;)

Desktop = ~/Desktop


Thanks for your continued interest.

This is what I did:-

I went to Applications - Sound & Video - K3b

Then, with the K3b window open at create CD image, I click Home, then Desktop.

Is it fair to assume thats what you mean by "Browse to the location with k3b"  ?
__________________

---

### Post by bodhi.zazen on 2006-12-21
> **L Campbell said:**
> Thanks for your continued interest.

This is what I did:-

I went to Applications - Sound & Video - K3b

Then, with the K3b window open at create CD image, I click Home, then Desktop.

Is it fair to assume thats what you mean by "Browse to the location with k3b"  ?
__________________

Yep. Did you find the mint .iso ?

---

### Post by L Campbell on 2006-12-22
> **bodhi.zazen said:**
> Yep. Did you find the mint .iso ?


Well, yes and no.

I did the 'extract' thing and got 2 folders on the desktop.  casper and isolinux

K3b doesn't find (and I do not see) a ' .iso ' file.

I took a couple of screeshots:-

---

### Post by meng on 2006-12-22
Okay, since you're using GNOME, try this:
Minimize/shut all windows, right-click on the .iso file which you've said is on your desktop, then choose the option "Write to Disc..."

---

### Post by L Campbell on 2006-12-22
> **meng said:**
> Okay, since you're using GNOME, try this:
Minimize/shut all windows, right-click on the .iso file which you've said is on your desktop, then choose the option "Write to Disc..."

The file that is on my desktop is not a . (dot) iso ask far as I can understand.

It is ' isolinux ' with no dot.

Also, right clicking on the file doesn't offer me the option you suggested but thanks anyway.

---

### Post by meng on 2006-12-22
Then download the .iso file, the isolinux is not an .iso file, we seem to be going around in circles here.

---

### Post by meng on 2006-12-22
Let's give it another try. Have you got a file named:
LinuxMint-2.1.iso

This is the file you need to burn a CD from.

---

### Post by L Campbell on 2006-12-22
> **meng said:**
> Let's give it another try. Have you got a file named:
LinuxMint-2.1.iso

This is the file you need to burn a CD from.

I believe you've hit on the crux of the problem.

LinuxMint-2.1.iso is the file I was downloading and I expected it to land on my desktop as a 'folder' 

What I got was what I would call a 'small screen' wich had 3 folders and 2 files on it.  This had the option to 'extract' and when I 'extracted' I had 2 folders (see screenshot)

---

### Post by L Campbell on 2006-12-22
> **L Campbell said:**
> I believe you've hit on the crux of the problem.

LinuxMint-2.1.iso is the file I was downloading and I expected it to land on my desktop as a 'folder' 

What I got was what I would call a 'small screen' wich had 3 folders and 2 files on it.  This had the option to 'extract' and when I 'extracted' I had 2 folders (see screenshot)

The screenshot was too large to attach.  Sorry.

---

### Post by meng on 2006-12-22
Make sure you are saving the target and not "opening with".

---

### Post by L Campbell on 2006-12-22
> **meng said:**
> Make sure you are saving the target and not "opening with".

OK, I took the default, 'open with'.

Let me try downloading it again as 'save to' and I'll let you know what happens.

Many thanks.

---

### Post by L Campbell on 2006-12-22
> **L Campbell said:**
> OK, I took the default, 'open with'.

Let me try downloading it again as 'save to' and I'll let you know what happens.

Many thanks.


This was definitely the whole problem.

I used the 'save to' option and now have the LinuxMint-2.1.iso file on the Desktop and have successfuly burned the CD.

I appreciate you sticking with me here.

---

