---
title: "USB Card Reader??"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by PrettyInUT on 2007-07-18
So I have a USB Compact Flash reader. When I plug it in, a new drive appears in my Computer folder, entitled "USB MASS STORAGE DEVICE". When I put a compact flash card in it, nothing happens, and if I attempt to mount it by right clicking on the device, I get this error:

"Unable to mount media. There is probably no media in the drive."

But there is media - it's a blank CF card. Sandisk Extreme III.

What do I need to do to get this working?

---

### Post by Gabn on 2007-07-18
try putting the card into the reader first then pluging in the reader. 

is the CF card formated ?

---

### Post by PrettyInUT on 2007-07-19
I tried both inserting the card reader with the card in, and the card out. I get the same message.

The card shouldn't have anything on it at all.

After fiddling with it for a while, I was able to see it as dev/sdb in Gparted, but then it started getting fiddley and now my computer doesn't see the reader at all.

The reader still works over on my Windows computer, but plugging it into my Linux computer now results in nothing at all. Like it doesn't even see it.

Edited to add: I attempted to format the CF card in Windows, but it can't format it, and I can't open it there, either.

'Nother edit: I got my digital camera to reformat the CF card. It is now FAT32 formatted with absolutely nothing on it. Linux still doesn't see my CF reader, whether it has a card in it or not.

---

### Post by Gabn on 2007-07-19
Dump a file on it in windows just so you have more to play with. or take some photos with your camera. 

besides that have you restarted you system since you pluged it in the first time ? 

I know how to fix this problem in kbunutu just not ubuntu. you have to go to disk and filesystems and enable the  usb drive.

---

### Post by PrettyInUT on 2007-07-19
D'oh! Restarting with the card in the reader, and reader plugged in, results in a working card and reader combo.

>.<

I guess I assumed (bad me!) that Linux wouldn't be subjected to the "oops it doesn't work, try restarting!" rigamorale that Windows puts you through.

Is there a way to make it so I don't have to restart every time I want to use my reader?

---

### Post by ubanchaos on 2007-07-19
does it have all the drivers nessesary maybe....sorry i cant be more of help

---

### Post by PrettyInUT on 2007-07-19
How could I tell if I've got the right drivers? It's just some cheapy compact flash reader I bought for 5 bucks, it didn't come with any software.

---

### Post by Gabn on 2007-07-19
> **PrettyInUT said:**
> D'oh! Restarting with the card in the reader, and reader plugged in, results in a working card and reader combo.

Is there a way to make it so I don't have to restart every time I want to use my reader?

yeah there it's a mounting issue when you boot up the machine it auto mounts all the drives it can find. 
therefore restarting caused this to happen so that's why it worked on restart. 

in System -> Preferences -> Removable drives and media 

check that mount drivers when hot-plugged is checked. 

for more options add/remove programs and install  Disk Management 

you should be able to use that to mount and umount your usb card reader.

---

