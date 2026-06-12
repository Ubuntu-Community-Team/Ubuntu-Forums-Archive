---
title: "Dual Boot : SATA + IDE"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by sumitsen on 2006-07-07
Hi Friends,

Here is my problem. I have two hard drives. One SATA and one IDE connected to primary master.

WindowsXP is installed on the sata drive and it works fine.

I have installed ubuntu dapper 6.06 on my IDE drive. While installing ubuntu, I **disabled the sata drive from the bios** because I didnt want to mess up the MBR of the SATA drive.

Ubuntu is working fine but now after **[B]enabling** the sata in the bios[/B], the grub loaded on the MBR of the IDE wont show an entry of WindowsXP (SATA).

How can I get it to do that.

I have checked different posts in the forum, but their cases are different. hda(0,1) all sounds confusing to me.

Please help me linux GURUS.

Thanks & Regards
Sumit Sen

---

### Post by flarkit on 2006-07-07
You needn't touch the MBR of your Windoze SATA drive. If you haven't customised your Ubuntu too far, I would recommend the following:

- enable the SATA drive in the BIOS
- install Ubuntu on the IDE (it shouldn't touch your SATA drive)
- reboot, go into the BIOS, and set it to boot from the IDE drive (but leave the SATA drive enabled)

Grub should detect the XP installation on the SATA drive during installation and and an entry for that. When you boot from the Ubuntu drive, you should see the Grub menu with entries for both OS's.

I did something very similar last weekend, installing Ubuntu on a SATA drive, whilst having XP on an IDE drive. I simply configured the BIOS to boot from the new SATA drive instead of the old IDE one and it worked 100%. I did test to check that the IDE drive's MBR was intact, but changing the boot sequence back to the XP drive, but I returned the BIOS to booting Grub from the SATA drive.

Oh also, if you'd rather not reinstall Ubuntu, then look around for guides on reinstalling Grub after installing XP. It's a common occurrence and you can fix it by booting into a LiveCD, then installing Grub from a terminal window.


HTH

---

### Post by sumitsen on 2006-07-07
Thanks for the reply flarkit.

The SATA drive is already enabled.

When I change the hard drive order from the bios, it loads the respective OS's. Sata=WindowsXP, IDE=Ubuntu.

I dont want to reinstall the ubuntu. It is working perfect for me.

I want to boot from the ubuntu drive and see the list of menus for both OS's.

Please help !

---

### Post by Indroth on 2006-07-07
The menu might be hidden by default, in which case ESC brings it up. If that is not the case here's one way to do it:

1 ) Boot to linux.
2 ) Open a terminal (Applications>Accessories>Terminal)
3 ) go to /boot/grub (type "cd /boot/grub" in the terminal withouth the quotes and press enter)
4 ) Type "sudo gedit device.map". It will ask for the password and then bring up a text editor.
5 ) In the file you should see two lines like this:
(hd0)  /dev/hda
(hd1)  /dev/sda

If what you see is a little different that should be fine as long as you have at least two entries (one for each drive). The one with the 's' (probably sda) is the SATA drive. It is probably also the second one on the list. Note the number next to it (hd1). This is how GRUB identifies the drive.

6 ) Close gedit
7 ) In the terminal, type "sudo gedit menu.lst"
8 ) At the bottom of the file add the following lines. Substitute your SATA volume from step 5 for hd1 if it is different)

title   Windows XP
root    (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader   +1

Don't put this paragraph in the file ;)... The first line is what shows up in the menu. The second line identifies the location of the boot. The third and fourth lines make windows believe that it is on the first hdd (which is required for windows to boot correctly) , and the last line launches the windows MBR.


9 ) Save the file, close gedit and restart the computer. The menu should have "Windows XP" at the bottom of the list.

---

### Post by flarkit on 2006-07-07
Yep, if you are booting from the Ubuntu drive and have a Grub menu, which excludes an entry for XP, then Indroth suggestion should sort your problem out for you.
;) 

> **sumitsen said:**
> Thanks for the reply flarkit.

The SATA drive is already enabled.

When I change the hard drive order from the bios, it loads the respective OS's. Sata=WindowsXP, IDE=Ubuntu.

I dont want to reinstall the ubuntu. It is working perfect for me.

I want to boot from the ubuntu drive and see the list of menus for both OS's.

Please help !

---

### Post by sumitsen on 2006-07-07
Hi Indroth,

In my device.map file, only the IDE drive was showing up. I added the sata as well to that (hd1) /dev/sda.

THen I edited the menu.list and added what you told me to add and the dual boot is working fine.

The only problem is that the grub menu is not showing automatically and for a long time. I have to press ESC always to get to the grub menu.

Can anyone help.

Cheers, Sumit.

---

### Post by Indroth on 2006-07-08
To increase the timeout, look in menu.lst. There should be something that says "timeout 10" (or something like that). Change that number to whatever you want.

To show the menu without having to press ESC, find the line that says "hiddenmenu" and remove it (or add a # at the start of the line).

There are lots of other options in menu.lst. There should be a whole bunch of comments (lines starting with # are comments) that tell you hopw you can use these things.

---

### Post by Mark228 on 2006-07-23
> **sumitsen said:**
> Hi Indroth,

In my device.map file, only the IDE drive was showing up. I added the sata as well to that (hd1) /dev/sda.

THen I edited the menu.list and added what you told me to add and the dual boot is working fine.

Hi I am in the same situation as the OP with Ubuntu on my IDE and XP on the SATA. I copied what sumitsen did and added the entry "(hd1) /dev/sda" as only the IDE was showing up for me in device.map too. Then edited menu.lst etc. I rebooted and Windows Xp option was there but when I tried it I got the following:

> 
Booting 'Windows XP

root     (hd1,0)
Filesystem type unknown, partition type 0x7
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
NTLDR is missing
press ctrl + Alt + del to restart

'
I'm a total newbie, can someone help? The SATA HDD was working fine in this PC but I had to buy a PCI card for it as the MB didn't take SATA. I can't find anything in BIOS that mentions SATA (to enable/disable) either but didn't stop it from working before. :confused:

---

### Post by Mark228 on 2006-07-23
Oh, just thought I'd add that I was already dual booting with these two HDDs before with XP/win98 and deleted win98 to install Ubuntu. I mention it as I am [reading this page]("http://www.computerhope.com/issues/ch000465.htm") about what that "NTLDR missing" means and am wondering if it might be my boot.ini file on the SATA XP drive causing the problem? And if so, how do I fix it?

---

### Post by confused57 on 2006-07-23
> **Mark228 said:**
> Hi I am in the same situation as the OP with Ubuntu on my IDE and XP on the SATA. I copied what sumitsen did and added the entry "(hd1) /dev/sda" as only the IDE was showing up for me in device.map too. Then edited menu.lst etc. I rebooted and Windows Xp option was there but when I tried it I got the following:


'
I'm a total newbie, can someone help? The SATA HDD was working fine in this PC but I had to buy a PCI card for it as the MB didn't take SATA. I can't find anything in BIOS that mentions SATA (to enable/disable) either but didn't stop it from working before. :confused:

I'm assuming you can boot either drive successfully from your bios.
If you can, from Ubuntu post the output of:
```
sudo fdisk -l
```
The -l is a small "L"

Also, you might want to read the grub page in this link:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Mark228 on 2006-07-23
> **confused57 said:**
> I'm assuming you can boot either drive successfully from your bios.

No I can't, I couldn't boot the SATA on its own before but was ok using it as a dual boot :confused:  . As I said I can't find anything in BIOS that would set it to boot this SATA hdd. Old BIOS maybe because my MB didn't support SATA anyway which is why I had to buy a SATA PCI card to plug it into my PC
> 
If you can, from Ubuntu post the output of:
```
sudo fdisk -l
```
The -l is a small "L"

It's just showing the IDE:

Disk /dev/hda: 13.0 GB, 13022324736 bytes
255 heads, 63 sectors/track, 1583 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1514    12161173+  83  Linux
/dev/hda2            1515        1583      554242+   5  Extended
/dev/hda5            1515        1583      554211   82  Linux swap / Solaris
> 
Also, you might want to read the grub page in this link:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Thaks I'll check it out now.

---

### Post by confused57 on 2006-07-23
I don't have any expertise with SATA PCI cards, but is there any documentation &/or CD(with drivers) that came with the card that might help.
Also, maybe you can google for it or go to the manufacturer's website.

It could be you had downloaded the driver to the Win98 IDE drive, which enabled booting of the SATA drive?

Wish I could help more...good luck.

---

### Post by Mark228 on 2006-07-23
> **confused57 said:**
> I don't have any expertise with SATA PCI cards, but is there any documentation &/or CD(with drivers) that came with the card that might help.
Also, maybe you can google for it or go to the manufacturer's website.

It's a SIL3114 chipset (With RAID Function) and looks as though there's no drivers for Ubuntu although I found some for SuSe and RedHat (I gather these won't work?). So basically it looks like I can't use the PCI chipset and my SATA HDD in my system with Ubuntu.
> 
It could be you had downloaded the driver to the Win98 IDE drive, which enabled booting of the SATA drive?

Yeah that's what I did. Time I invested in a new PC I think, or just buy another IDE drive.

Anyone want to swap a 40gig IDE drive for my 40gig SATA? :-k 

Thanks for your help anyway.

---

### Post by confused57 on 2006-07-23
I don't know if the Suse & Rehat drivers would work or not, maybe you could try installing them & see(I don't know):

[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

I have mobo SATA controllers on 2 of my computers, but have avoided buying SATA hard drives because of their problems with Linux(driver support).

---

