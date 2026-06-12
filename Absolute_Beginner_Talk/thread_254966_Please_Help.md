---
title: "Please Help"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by snagger on 2006-09-10
Ok ive downloaded ubuntu and written it to a dvd

i restarted my comp and set it to boot from cd drive but nothing happened i still get my windows xp coming up

i can open the cd in windows and run start.exe
but this only lets me install the programs like firefox etc it doesnt let me instal ubuntu

Any ideas?

---

### Post by ramcosca on 2006-09-10
When the computer has shut down and is restarting, hit F8 (or F12, not sure) when the BIOS is loading and select the option to load from CD-ROM there.

I hope I got it right. lol

---

### Post by meng on 2006-09-10
To install you must boot from the CD. If you need to edit your BIOS to get the CD to boot before the hard drive, the required keypress could be any of the F-keys, Del, Esc, or maybe something else exotic. There may briefly flash up a message at boot-time telling you which key is the correct one.

If the BIOS is already set to boot from CD and this isn't happening, it is possible that the download is corrupted or the burn is bad. Check md5sum to ensure the integrity of the downloaded ISO, and/or re-burn at a lower speed.

---

### Post by FakeOutdoorsman on 2006-09-10
Perhaps your downloaded Ubuntu installation file has been corrupted.  Try running [md5summer]("http://md5summer.org/") in Windows and comparing these [MD5 sums]("http://ubuntu-releases.cs.umn.edu//6.06/MD5SUMS") that are shown on the Ubuntu download page with the MD5 sum of your downloaded installation file.  If they are different then you have to redownload Ubuntu or I can send you a disc.

---

### Post by snagger on 2006-09-10
Ok ive hit F12 and selected to boot from cd drive first but with no joy.

Ive ran the MD5 check thing you give me a link for and everything is fine no errors.

I created the cd using cd burner xp pro3 and added the rar file which i downloaded which was around 700mb ticked the box for 'make disk bootable' and clicked burn

After the burn is complete i can open the cd to find the rar file still there but the name has changed to UBUNTU_6

So what are your thoughts?

---

### Post by NetworkGuy on 2006-09-10
You can't make a CD image from a .rar file.  You probably need to "unrar" the  file.   You are looking for an .ISO file.

---

### Post by ramcosca on 2006-09-10
Maybe he meant the .iso image. WinRAR puts it's icon on .iso files when it is installed as default archiver.

---

### Post by jbonll05 on 2006-09-10
Reference boot sequence on startup,
 Many machines will access the cmos by pressing "escape" or "delete" quickly on startup. Go down the menu until you find a title like boot sequence. Open it and set first choice to either "A" drive (floppy if you have one), then your cdrom drive letter probably "D", and last hard drive (C). Note: All three of mine respond to "escape".
 I have one machine with a floppy(1.44 Mb) installed and use a usb floppy to retrive old note files i have on floppies. Linux handles M$ files well.
"New"Linux user;jb

---

### Post by snagger on 2006-09-10
Right im looking but cant see any .iso

Where would it be?

Ive tried to attach a screen shot so you can see..

---

### Post by FakeOutdoorsman on 2006-09-10
It appears that UBUNTU_6.ISO is your ISO file according to your screenshot.  It's what you're looking at in WinRAR.  Forget WinRAR.  You don't need it.

Your cd burning program, cd burner xp pro3, can burn from an ISO file.  Open the program and there shold be an option to "burn from ISO image" or something similar.

---

### Post by snagger on 2006-09-10
I have written a dvd already which is where that UBUNTU_6 file come from

This is what i clicked:

---

### Post by NetworkGuy on 2006-09-10
Try writing the ISO to a CD instead of a DVD.

---

### Post by snagger on 2006-09-10
I dont have any blank cds and im sure i read somewhere that you could write it to either dvd or cd.

---

### Post by NetworkGuy on 2006-09-10
What your doing should work.  It's the only thing I can think of to try.  It worked for me :)

---

### Post by FakeOutdoorsman on 2006-09-10
It looks like you're dragging the ISO file into the burn dump.  I believe your cd burning program lets you choose the ISO image.  You should end up at a screen like this before you start the burn:
[URL="http://www.cdburnerxp.se/screenshots/main-iso.png"]
Screenshot[/URL]

---

### Post by NetworkGuy on 2006-09-10
Oops, missed that in the snapshot.

---

### Post by FakeOutdoorsman on 2006-09-10
1. Start CdBurner XP Pro
2. Choose File
3. Choose Write Disc from ISO file
4. Browse for the ISO-image file
5. Choose "Write Disc"

---

### Post by snagger on 2006-09-10
> 1. Start CdBurner XP Pro
2. Choose File
3. Choose Write Disc from ISO file
4. Browse for the ISO-image file
5. Choose "Write Disc"

This isnt an option with my CdBurnerXpPro3 

I only have the options shown in my screenshots

when everyone else downloads the initial file is it a rar file?

also when its been written as an .iso what will the file symbol look like?

---

### Post by FakeOutdoorsman on 2006-09-11
Maybe you are using an older versin of the software.  Try downloading the [newest version]("http://cdburnerxp.se/download.php?latest") and uninstalling your version.  You can get the translation files [here]("http://cdburnerxp.se/translation.php").

If you don't like CDBurnerXP Pro 3, then try [burnatonce]("http://www.burnatonce.net/downloads/") or some other software.  There are [instructions]("http://iso.snoekonline.com/iso.htm") to burn an ISO for various cd burning software.

---

