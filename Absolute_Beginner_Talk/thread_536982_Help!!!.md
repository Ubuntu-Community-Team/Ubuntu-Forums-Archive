---
title: "Help!!!"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by marcopolo1981 on 2007-08-28
Please can somebody tell me how to uninstall Ubuntu?
I Installed it "temporarily" onto my wifes laptop purely so that i could have a look at it. I installed it onto a 4gb Partition so as not to disturb her work files. Whilst many of you might think I must be particularly stupid to do this without her consent, I prefer to think I was Brave!
She was/is running Windows xp pro. I thought it would be easy enough to delete/format the partition taking ubuntu with it, but I just can't figure it out!
Personally, I like it, but my wife has hit the roof!
Please, Please, PLEASE can somebody help prevent my imminent divorce?!

---

### Post by jfinkels on 2007-08-28
> **marcopolo1981 said:**
> Please can somebody tell me how to uninstall Ubuntu?
I Installed it "temporarily" onto my wifes laptop purely so that i could have a look at it. I installed it onto a 4gb Partition so as not to disturb her work files. Whilst many of you might think I must be particularly stupid to do this without her consent, I prefer to think I was Brave!
She was/is running Windows xp pro. I thought it would be easy enough to delete/format the partition taking ubuntu with it, but I just can't figure it out!
Personally, I like it, but my wife has hit the roof!
Please, Please, PLEASE can somebody help prevent my imminent divorce?!

Boot into the Live CD environment and use the program GParted to erase the partition. Just make sure it's not mounted, then choose "Delete the selected partition". You may have to find out how to rewrite the Master Boot Record with the standard Windows MBR in place of the GRUB boot loader.

---

### Post by wolfen69 on 2007-08-28
download and burn gparted.

---

### Post by asmoore82 on 2007-08-28
> **marcopolo1981 said:**
> Please can somebody tell me how to uninstall Ubuntu?
I Installed it "temporarily" onto my wifes laptop purely so that i could have a look at it. I installed it onto a 4gb Partition so as not to disturb her work files. Whilst many of you might think I must be particularly stupid to do this without her consent, I prefer to think I was Brave!
She was/is running Windows xp pro. I thought it would be easy enough to delete/format the partition taking ubuntu with it, but I just can't figure it out!
Personally, I like it, but my wife has hit the roof!
Please, Please, PLEASE can somebody help prevent my imminent divorce?!

do you really need to remove Ubuntu,
or just set up a dual boot with WinXp as the default?

the latter should be much easier and the only way to not have to use a
Windows disk to restore the micro$oft MBR.

---

### Post by WebSiteGuru on 2007-08-28
> **asmoore82 said:**
> do you really need to remove Ubuntu,
or just set up a dual boot with WinXp as the default?

the latter should be much easier and the only way to not have to use a
Windows disk to restore the micro$oft MBR.

I would go with  the second option. Then you can still play with Ubuntu. ;)

---

### Post by jerrynewt on 2007-08-28
[QUOTE=asmoore82;3268521]do you really need to remove Ubuntu,
or just set up a dual boot with WinXp as the default?
How do I set up Feisty as default over Gutsy?

---

### Post by Unstuck on 2007-08-28
> **jerrynewt said:**
> [QUOTE=asmoore82;3268521]do you really need to remove Ubuntu,
or just set up a dual boot with WinXp as the default?
How do I set up Feisty as default over Gutsy?

If your wife is really that upset you may want to have XP as the default, but you can choose which OS you want to use from the GRUB screen.  The easiest way to manage them is with [SUM]("http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml").  After installing this, you can choose, among other things, the default OS and the amount of time you have before the default automatically loads.  I found it to be extremely useful and easy to use.

Edit: You probably want to check Synaptic Package Manager for "startup manager" first.  This is always the easiest way to install apps if it is part of the repository...I just don't remember if it is or not.

---

### Post by jfinkels on 2007-08-28
> **jerrynewt said:**
> [QUOTE=asmoore82;3268521]do you really need to remove Ubuntu,
or just set up a dual boot with WinXp as the default?
How do I set up Feisty as default over Gutsy?[/QUOTE]

To change which system is the default system to which to boot in GRUB, edit your /boot/grub/menu.lst in this way:```
gksudo gedit /boot/grub/menu.lst
```

In the section that looks like this:```
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

``` just change the default number from '0' to whatever number your desired installation is in the list at the bottom of the file (the first entry is 0, the second is 1, etc.)

---

### Post by marcopolo1981 on 2007-08-29
Thanks all for your advice. The missus decided that I'm never to be trusted within10feet of her laptop again and has taken it to a pro. Wouldn't let me even carry it for her. 
I have manged to install Ubuntu on my own pc now tho. Its my first time on any system other than windows and I have to say I'm very impressed with it.
As I use this pc for work, I need to know that the Openoffice.org software is fully compatible with micro$oft office 2003. Has anyone ever reported problems when opening MS spreadsheets in Openoffice spreadsheet? Or vice versa? If so, is there a more compatible software I need?
Thnks again.

---

### Post by jfinkels on 2007-08-29
> **marcopolo1981 said:**
> Thanks all for your advice. The missus decided that I'm never to be trusted within10feet of her laptop again and has taken it to a pro. Wouldn't let me even carry it for her. 
I have manged to install Ubuntu on my own pc now tho. Its my first time on any system other than windows and I have to say I'm very impressed with it.
As I use this pc for work, I need to know that the Openoffice.org software is fully compatible with micro$oft office 2003. Has anyone ever reported problems when opening MS spreadsheets in Openoffice spreadsheet? Or vice versa? If so, is there a more compatible software I need?
Thnks again.

Because Microsoft does not cooperate with our open standards and they use proprietary file formats, some files may not work the way they were intended to if you open a Microsoft Office Word document file, Excel workbook file, etc. in the OpenOffice equivalents. If files are causing you problems, you can try opening them in AbiWord or Gnumeric. You can install them individually by typing in the terminal:```
sudo aptitude install abiword gnumeric
```or you can install the entire GNOME office suite, by typing in the terminal:```
sudo aptitude install gnome-office
```

If THAT doesn't work for those goofy Microsoft files and you want to spend (waste) your money buying Microsoft Office, you can try to install and run those programs using 'wine' (or the commercial application "CrossOver" which actively tries to get Microsoft Office to work on Linux: [http://www.codeweavers.com/](http://www.codeweavers.com/)). To install wine, type in the terminal:```
sudo aptitude install wine
``` To run a program with wine type ```
wine "/path/to/executable.exe"
```

---

### Post by cubeist on 2007-08-29
As a student I have never had any issues with openoffice  and people in the windows world.  When I am working on a project I tend to save as .odt but then when I have finished I save a copy as .doc using the "Microsoft Word 97/2000/XP" option.  It works perfectly every time.  The only issue I have ever encountered is trying to complete a complex database.  The OpenOffice Database program doesn't match feature for feature to the Microsoft Program Access.

> **marcopolo1981 said:**
> Thanks all for your advice. The missus decided that I'm never to be trusted within10feet of her laptop again and has taken it to a pro. Wouldn't let me even carry it for her. 
I have manged to install Ubuntu on my own pc now tho. Its my first time on any system other than windows and I have to say I'm very impressed with it.
As I use this pc for work, I need to know that the Openoffice.org software is fully compatible with micro$oft office 2003. Has anyone ever reported problems when opening MS spreadsheets in Openoffice spreadsheet? Or vice versa? If so, is there a more compatible software I need?
Thnks again.

Also, you make a very strong case against marriage! :razz:

---

