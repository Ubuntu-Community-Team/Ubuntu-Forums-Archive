---
title: "Problem getting from Ubuntu back to Mac OSX"
date: 2012-04-30
forum: Apple Hardware Users
---

### Post by Magoosy on 2012-04-30
Hey Guys,

My MacBooks HDD crashed and I installed Ubuntu onto a new HDD and it works fine.

So right now there is no OSX on my Hard Drive.
But now I would like to get back to OSX.

So I burnt a OSX Lion 10.7.2 disk. When I try to boot the Macbook the ALT key it shows me the Ubuntu partition as "windows" and the OSX DVD as "EFI-Boot". When I try to select the OSX disk, an apple - logo shows up for a second and then Ubuntu is booting. 

So now I wonder how to reinstall OSX and how to make the osx-disk work. Can anyone help me? Big thx

---

### Post by alexblackie on 2012-04-30
I don't think you'll be able to install OSX after Ubuntu. AFAIK,  OSX has to be installed first, then Ubuntu afterwards (in order for the OSX EFI to work correctly, or so you can install [rEFIt]("http://refit.sourceforge.net/"))...

---

### Post by Magoosy on 2012-04-30
Oh, worried about that. So then the only solution would be to format the hdd, delete ubuntu and everything on it and install osx? Do you think this would wrork?

---

### Post by DavidSommen on 2012-05-01
Yes, this will most likely be the best way to do it.

---

### Post by Magoosy on 2012-05-01
okay, thank you for your response. I'll try to format it with a gparted live disk... let's see if it works.

---

### Post by Magoosy on 2012-05-01
Now I formated the hdd but it's still showing me the osx disk as "efi boot". Maybe there is something wrong with the disk. Or did ubuntu change the efi settings of the laptop. 
Slowly I'm getting crazy about it ;)

---

### Post by m3topaz on 2012-05-04
Your Lion disk should be bootable. Hold down alt/option key when you power up and the disk should be recognised. Boot from it and use Disk Utility from the menu at the top (which might be hidden, move the mouse over it to reveal) - you should see the partition layout in Disk Utility.
If you want both OS X and Ubuntu, prepare a partition for OS X, label and format to HFS+. Format the rest of the disk as FAT - Ubuntu can install in that FAT space once you have re-installed OS X.
After OS X goes on, use rEFIt as the first thing you do. It should allow you to install Ubuntu from a bootable CD to let you dual boot.

---

### Post by Magoosy on 2012-05-10
Thank you guys for all your suggestions!
Now I am back at mac.


m3topaz' solution was almost right but my problem was that I didn't get the OSX Lion Disk running. 

So here's the solution:
[LIST=1]
[*]Download and Burn Gparted or Parted Magic Live-Disk
[*]Shut down Mac and run the Live-Disk by holding the "ALT" key after the start sound
[*]Use gParted tool to create one HFS+ partition (The OSX disk needs at least one HFS+ partition to be able to start.
[*]Insert OSX disk, reboot and hold ALT again.
[*]Now you sould be able to run the disk and re-install OSX or use diskutility
[*]Done. :)
[/LIST]

BUT. My problem also was that I wasn't able to burn a OSX-dis because thats very hard to do with Ubuntu. All the dmg2img solutions don't really work. So my solution above didn't help me. I made it by following this excellent Totorial. It shows you 

[COLOR="Red"]ONLY DO THIS WHEN YOU ALREADY OWN AN OSX LION LICENSE!
[/COLOR]
[B]How to install OSX from an Ubuntu-only Macbook without burning an OSX DVD or creating an USB Thumbdrive:
[/B]
[http://linuxforums.org.uk/index.php?topic=1072.0]("http://linuxforums.org.uk/index.php?topic=1072.0")

The only addition for OSX Lion:
[COLOR="red"]I had to skip this step![/COLOR]

> You will need to edit (as root) the
/Library/Preferences/SystemConfiguration/com.apple.Boot.plist
file (on the 8gb partition), and set a kernel flag to point to this partition... i used gedit, but any text editor will do.

Look for the lines:
<key>Kernel Flags</key>
<string></string>

I changed them to:
<key>Kernel Flags</key>
<string>rdisk0s3</string>
but you will need to change rdisk0s3 to wherever YOUR 8gb partition is located.

rdisk0s3 = First Physical Hard Drive, 3rd partition (so another example would be rdisk1s2 = second HDD, 2nd partition)

Where:- rdisk0 = First HDD, rdisk1 = Second HDD etc.
and s1 = First partition, s2 = Second partition etc.

save the file.

Many Thanks to Mark Greaves for that!

---

### Post by PCNetSpec on 2012-06-06
You're most welcome .. glad it helped .. and thanks for the info on what needs to be left out in Lion :)

---

