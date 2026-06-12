---
title: "Installing Linux, wont boot of Live CD"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by RougiPwns on 2007-04-20
I have a dell pc with vista installed and i have Dapper Drake on CD and have downloaded Fiery Fawn.

When i leave my cd in the pc it dusnt boot it goes straight into vista :( 

And the download i have got looks pretty much the same as the cd, do i have to burn this to cd if so do i just burn the files and it should work or what?

Iv searched but most people arnt this useless and most have actually got the thing installed :(

---

### Post by taurus on 2007-04-20
How did you burn the ISO image?  If you look at the content of the CD in Vista, you should see a bunch of files and directories.  Do you see that or do you see only a one large file?

---

### Post by grahams on 2007-04-20
Hopefully we can save you from Vista :)

Can you boot from any other install CD such as the Vista recovery or install disks. If not you may need to edit your bios settings to allow boot from CD. 

The downloaded image needs to burnt into a CD as an ISO image. Under LINUX I use k3b for that, I believe there is a free ISO burner for Windows, but I don't know what it is called.

Have fun

---

### Post by RougiPwns on 2007-04-20
what iso image? :( :( 

iv extracted the files from the .rar archive that i downloaded

also just tried to burn this too disc and i need an extra 418 kb, very lame, i guess using a dvd dusnt matter right?

---

### Post by bobplano on 2007-04-20
actually don't use a dvd unless you downloaded the dvd version. are you sure that the file is a .rar? it is supposed to be a .iso and you're not supposed to extract the files. a free iso burner by the way is infrarecorder (burn the image at slow speeds like 4X so there are less errors)

---

### Post by RougiPwns on 2007-04-20
ok well i tried using a dvd but was gonna take an hour so i stopped that...

is there anyway to make the live cd i have work? because my cds are all just under the amount of space i need :(

---

### Post by taurus on 2007-04-20
Somehow your WinRAR converts the .iso into .rar.  Therefore, just rename it (without unpacking it) and burn it as an _ISO image_ with your CD burner.  It would fit on 700MB CD so don't worry if it is more than 700MB.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by grahams on 2007-04-21
If you downloaded the livecd from ubuntu it is an ISO file and can be burned directly to a cd-r or cd-r/w disk. If you downloaded a .rar file I'm not sure that is the official live cd. 

BTW. ISO files are CD images

---

### Post by bobplano on 2007-04-21
> **taurus said:**
> Somehow your WinRAR converts the .iso into .rar.  Therefore, just rename it (without unpacking it) and burn it as an _ISO image_ with your CD burner.  It would fit on 700MB CD so don't worry if it is more than 700MB.


the most likely reason it is bigger is because somehow it is now a .rar file

---

### Post by Tasu on 2007-04-21
Probably the original poster has the filename extensions not shown on windows (it's an horrible "feature" of windows, that can't understand a file from it's content, but just from it's extension, this so called feature of windows is really a stupid hack!), moreover, he installed winrar that associated itself with all the known archive types (rars, zips, isos, etc.), these two facts led to the icons of iso and rar files be the same, and the inability to see the extension of a file (the original poster probably sees the downloaded file like "ubuntu-7.04-beta-desktop-i386" missing the .iso at the end), led him think he would have downloaded a rar file.
Ok, solution to the problem: you don't have to extract the content of the iso file, you have to use a program to burn a iso image on the disc, you don't have to burn directly the whole iso image to the disk as a single file, but you have to use a burn program to point to that iso image (that's just a representation of a cd in a huge file) using the right tool.
Following this guide [http://neilmonday.blogspot.com/2007/04/how-to-burn-isos-directly-in-windows.html](http://neilmonday.blogspot.com/2007/04/how-to-burn-isos-directly-in-windows.html) will show you how to burn the iso image using vista (you have to install a freeware software).

If you would like to see the extensions of your files (I've never understood why microsoft thinks it's good to hide them), so to have a bit more control over your computer (and never fall again in a trap like the one you've experienced, by mistakingly think that an iso is a rar), follow these steps:

1. Click Start 
2. Select Control Panel 
3. Select Classic View 
4. Double-click Folder Options 
5. Click the View Tab 
6. Uncheck Hide Extensions for Known File Types 
7. Click Apply button (at the bottom of the window) 
8. Click Apply to Folders button (at the top of the window) 
9. Click OK

from now on the only problem that could arise, is that your computer is not set to boot from cdrom, if the ubuntu cd won't start again, please enter your computer's BIOS (usually by hitting the del key on the first stages of the computer's boot, when it looks for ram and hard disks), and change the boot options from there to have the cd boot before the hard disk (actually, before everything! ^_^)

regards

---

