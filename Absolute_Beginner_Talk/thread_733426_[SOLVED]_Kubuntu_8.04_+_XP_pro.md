---
title: "[SOLVED] Kubuntu 8.04 + XP pro"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Zralou on 2008-03-23
For the last two days i've been tearing my hair out trying to install Kubuntu 8.04 (beta) on my computer that already has XP pro installed.
I have a 120 gig HDD, partitioned as 95 gig ntfs XP and 20 gig fat 32 file storage (to share with Linux, and the network).  I also have a second HDD of 80 gig that i'm trying to install Hardy on.

Now to the problem.  I want to use the NTLDR boot manager to handle the boot sequence, so during the install of 8.04 I pointed grub to install on hd1 (instead of hd0 as offered by default), but after disabling the 'master hdd' (XP) in bios and enabling 'slave hdd' (Kubuntu) to boot, I get to grub no problem, but after selecting Kubuntu I get the message: cannot mount...... error 17?.

What am I doing wrong?, I am completely novice with Linux, but am fairly compitent in microsoft, I know its something simple i'm missing or doing wrong, but i've hit that point now where 'I can't see the wood for the trees' and keep going round in circles.
Please don't tell me to install grub in the MBR, because I don't want grub to be the boot manager, I know its possible to do because i've done it with Mandrake before.  I just need someone to show me where i'm screwing up, I suspect it has to do with where I point grub to install, but I need help decifering my mistakes.:confused:

Sara Lou

---

### Post by PmDematagoda on 2008-03-23
The problem is that, since both the Windows drive and the drive on which Ubuntu was installed on, GRUB considered both hard drives and made the menu.lst accordingly.

When you reach the GRUB menu, press "E" at the normal Ubuntu entry and then change the root entry such that that number being highlighted here:-
```
root  (hd**1**,0)
```
is made:-
```
root   (hd**0**,0)
```
The other parts of the entry or the root entry does not matter, what really matters is the number that I've highlighted.

After the change is done, press "B", and that should boot up Ubuntu properly.

---

### Post by Zralou on 2008-03-23
But won't setting grub to hd0 cause it to overwrite the MBR, thus making NTLDR useless? (exactly what i'm trying to avoid).

Sara Lou

---

### Post by Zralou on 2008-03-23
Ok, changing to hd0 allows me to boot into Kubuntu on a 'one time' basis, after a reboot its back to the way it was.

I'm looking for a way to add Kubuntu to the NTLDR boot loader in XP Pro.  At the moment the only way I can get to ubuntu is to disable the primary master hdd (XP) from booting in bios, and enabling the primary slave hdd (ubuntu) to boot, then I have to edit the grub menu to change to hd0.
This isn't what I was hoping for, I just wanted to be able to dual boot XP + Kubuntu using XP's boot loader, I know it can be done with other distros because i've done it with mandrake.

So looks like i'll just end up another lost linux user who gets stuck with MS....

Sara Lou

---

### Post by smartboyathome on 2008-03-23
I think you have to use it as the main, with XP as the slave, otherwise it won't work. Also, edit your /boot/grub/menu.lst so that all (hd0,0) to hd(1,0) and vice versa.

---

### Post by Zralou on 2008-03-24
I never had this problem with the last distro I installed as a dual boot.  Looks like i'll have to ditch Ubuntu and go back to Mandriva, which is a shame as I liked the look and feel of Ubuntu, but if it can't do what I need it to, its no use to me.

Sara Lou

---

### Post by PmDematagoda on 2008-03-24
That's because you confused GRUB by having two hard drives during the install and then removing one of them, this changes the layout of the hard drives for GRUB and it can prevent Kubuntu from booting.

Just make the changes permanent by opening the menu.lst file for editing with:-
```
gksudo gedit /boot/grub/menu.lst
```
go to the last few lines and change the entries for Kubuntu accordingly.

---

### Post by Zralou on 2008-03-24
I didn't remove anything, I just changed the 'boot' order of hard drives in BIOS.  Both hd's are still there and connected, all I did was allow the slave drive to be the 1st boot drive and the primary was taken out of the 'boot' list of BIOS.
Its the only way I can get into ubuntu, if I leave the primary as 1st boot, it goes straight to XP, I can't get the .bin to work properly in XP, I get the option on the XP boot menu for ubuntu, but selecting it just takes me to a blank screen with flashing cursor.

Sara Lou

---

### Post by Zralou on 2008-03-24
After spending several hours searching all over the internet for a solution to this problem, it seems to me GRUB isn't capable of anything other than overwriting the MBR on the primary drive.

Is there a way to install LILO instead, at least that works (or at least in the past when i've set up dual boots, it has).
Or does anyone have a real solution that allows me to use NTLDR to boot XP and unbuntu without having to switch hard drives in BIOS whenever I want to switch operating systems.

Sara Lou

---

### Post by LowSky on 2008-03-24
Why are you using a Beta version of Ubuntu, use Gutsy.
Second Grub work fine for me and doesn overwrite the MBR as long as the Ubuntu hard drive is considered the primary drive in the BIOS. I can disconnect my ubuntu drive and windows will boot with no issues.

If you want LILO you need to use the alternative install CD, that has LILO on it

---

### Post by Zralou on 2008-03-24
Using the beta version isn't the problem, its close enough to stable for me.
I can swap boot order in BIOS and boot into XP or ubuntu easily and don't have to disconect anything, but thats not what I want.  I'm wanting to use XP's NTLDR bootloader to start XP or ubuntu, why is that so difficult?.

Sara Lou

---

### Post by |2A|N on 2008-03-24
I am having the same exact problem I run a RAID0 for my Vista partition and an IDE 40G HD for my Hardy but I had to set my Hardy drive as a slave because Windows wouldnt let me see the drive at all to install Hardy on so my question is if I change the pin on the IDE drive to primary will it mes anything up when rebooting? I hate having to switch the boot sequence in the bios as well when I want to use either Hardy or Vista....

---

### Post by Zralou on 2008-03-26
> **Zralou said:**
> 
Or does anyone have a real solution that allows me to use NTLDR to boot XP and unbuntu without having to switch hard drives in BIOS whenever I want to switch operating systems.

Sara Lou

And here it is: [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723).
Works perfectly, XP boots no problem, Ubuntu boots no problem, and both boot from XP's NTLDR.
Just finished installing Kubuntu on the second hard drive (set as slave), copied the bootloader file over to XP and everything worked as it should.  I still need to edit grub so I don't get the boot menu screen after selecting ubuntu from NTLDR, but just minor things, at least I have my dual boot the way I wanted it.

Sara Lou

---

