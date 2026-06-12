---
title: "Accessing Files saved in Windows using Ubuntu Live CD"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-03-03
Ok, here's the deal....

I have this Ubuntu live CD that I've been booting too occasionally, but for some reason the wireless card won't work. I've been reading the "unofficial Ubuntu Guide" ([http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)) and trying to work with my Wireless notebook card (WPC54G v1.2) ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)). On the guide, it says I have to download this certain firmware update for my card in order for it to work, but I can only get online when I'm using XP because that's the where my wireless card will works. I'm still sort of interested in the stability of Ubuntu and I'd like to continue exploring it but I can't figure out how to access the files I downloaded to my desktop in Windows. Do I need to partition the hard drive or something or is there a way I can access those files from my Ubuntu Live CD?

-Cliff

---

### Post by Amenemhet on 2007-03-03
I am not positive but i thought you could see Windows drives with the live cd? Maybe only after you install. I know for a fact, if you install it alongside windows, your fat and ntfs drives will automatically appear on the desktop. Then you can get what you need. Maybe the best option for you would be to put the drivers you require on a usb drive if you can, if you have one etc.
But i also think that you wont be able to do what you want until you install, as I think perhaps the live cd, while running as a cd, is read only, therefore you must install. Try it, what can you lose? A bit of time perhaps.

---

### Post by taurus on 2007-03-03
You have to mount the drive before you can see/access it.

---

### Post by luke411 on 2007-03-03
I assume you are doing all of this on the same pc, booting Live and then restarting in Windows? If that's the case, the only way you can pull this off would be to move the files you downloaded onto a flash drive or some other device while in windows and then access them when you boot Live.

When you use the Live cd, you are not accessing the hard drive at all and it probably is not even mounted. Also, if your pc is NTFS, you will hve problems sharing files anyway, because linux will read FAT 32 but it's not NTFS friendly.

If you really want to make a go of it, I would suggest plugging your pc into an ethernet jack in the router, install the Ubuntu with a dual boot system so that you still keep windows and then work on your card. Most likely your card will work but when you use LIVE CD, you cannot make any permanent installs and download the files you need because once you reboot, they're gone.

---

### Post by Amenemhet on 2007-03-03
I believe Taurus is right, it needs to mounted, which I am not sure you can do while running the live cd. And, Luke, sorry you are wrong, you can access ntfs, read ntfs, the issue is actually writing to an ntfs disk, which, i also believe can be done now (its those pesky 100+ ntfs permissions)but you need to install the update, and darned if i can remember what it is.

---

### Post by taurus on 2007-03-03
```
sudo mkdir /media/windows
sudo mount -t ntfs **/dev/hda1** /media/windows -o nls=utf8,umask=0222
df -h
```
Assuming /dev/hda1 is where XP is.

---

### Post by Andross707 on 2007-03-08
Just curious, but what does all that text mean? I'm still new and I'm guessing that learning more about terminal commands could be a helpful thing if I'm linux-bound

---

