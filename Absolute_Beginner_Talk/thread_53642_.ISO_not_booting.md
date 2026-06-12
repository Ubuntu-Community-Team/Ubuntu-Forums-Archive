---
title: ".ISO not booting"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by kaffeend on 2005-08-01
hiya, just tried to boot my system from the CD's .ISO image, and even thogh I set the boot order in the BIOS to be floppy, CD ROM, HDD 0 - I thought it should install easily (ish), but it ignores the disc and boots into Windows XP as normal. Can someone PLEASE help me out here, as whatever virus/hacker is responsible for the loss of my system tray AND task manager is slowly eating the rest of my system away, and I really need to reinstall ASAP

Please, anybody - SAVE ME!

---

### Post by Kvark on 2005-08-01
How did you burn the CD?
The only way that works is "burn image", "brun from image" or something similar depending on which program you use.

What do you see when you open the CD in windows?
If you see an .iso file on the CD then you burned it in the wrong way. If you see files and directories normally then it might be right but you best double check anyway that you did use the image option.

Is the .iso you burned from corrupted?
You can find this out by comparing the md5 checksum of the .iso with the sums found [here](http://dune.hu/ubuntu-releases/MD5SUMS). If it is not identical then it's corrupted and you have to download again.

To check the md5 checksum of a file in linux. type "md5sum file.iso" in a terminal. In windows you need a special program for it and how you do it depends on the program.

---

### Post by Alanmw on 2005-08-01
Hi,
I have tried to boot with the Live CD and get nothing also. I have set the bios to CD-Rom then IDE 0 also. I have a AMD-Duron. What type of image should I use and how do I 'Burn' it with Windows XP. 
Thanks  Alan

---

### Post by kaffeend on 2005-08-01
[QUOTE=Alanmw]Hi,
I have tried to boot with the Live CD and get nothing also. I have set the bios to CD-Rom then IDE 0 also. I have a AMD-Duron. What type of image should I use and how do I 'Burn' it with Windows XP. 
Thanks  Alan[/QUOTE]

Hmmm... Perplexing. I d/loaded the live version because I didn't want to wait 98+ hours for the torrent. Maybe this is gonna take that long anyway :/

Okay, I do see the image as a .ISO so I obviously burned it wrong. Alan, I can only assume you've done the same as me... when I clicked the download link and was redirected, I was prompted to open the link location with WinRAR - I did, and now it's simply a data CD - not a boot CD

What I want to know is, why are we doing all this? Surely there is an easier, more reliable and stable way of doing this?

And kvark, I have absolutely no idea what you were talking about, I'm afraid. maybe Linux is just for Linux users :(

---

### Post by Juergen on 2005-08-01
If you just drag the iso to the cd, you'll just get a cd with one file on it.

AFAIK the XP-builtin burner can't do what you want. 

But you should have a burn-prog like nero delivered with your CDRW-drive, or the OEM that built your box should have put it with the driver-CDs you received.
These programs have an option 'burn from iso' (nero: in 'file'-menu AFAIK)

After burning you should see several directories and not a single file no your cd.
Best try with RWs ;-)

---

### Post by byen on 2005-08-01
ok....this is what i would strongly suggest and I can gurantee you that this works!!
Go to [www.downloads.com](www.downloads.com) and search for the program "deepburner". its free and was developed by the developers with ISO burning in mind. It is really good and damn easy to use. Download it and burn the cd as an ISO project at a slower speed. Let me know if you have any probs. I might have some alternatives.
PS- some people have better luck booting off cds by  turning the ACPI support off at the boot options menu.
good luck.

---

### Post by pataphysician on 2005-08-01
another extremely easy/simple iso burning utility for windows is isoburn. it's a standalone executable. you run it, browse to the iso, click burn. it's impossible to get it wrong!

[http://dpaehl.dd6338.kasserver.com/cdr/isoburn.php](http://dpaehl.dd6338.kasserver.com/cdr/isoburn.php)

---

