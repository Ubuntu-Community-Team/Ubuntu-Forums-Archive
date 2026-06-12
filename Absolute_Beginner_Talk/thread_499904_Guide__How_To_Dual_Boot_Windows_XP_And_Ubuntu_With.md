---
title: "Guide : How To Dual Boot Windows XP And Ubuntu Without disturbing Windows Boot Loader"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-07-13
How To Dual Boot Windows XP And Ubuntu (Or Any Other Linux Distro) Without disturbing Windows Boot Loader Or Master Boot Record (MBR)

Benefit

Useful for novice user who is trying out Ubuntu (Or any other Linux Disto) for first time with windows xp pre-sintsalled already. Since by this method you don't temper with windows boot loader or master boot record, you can safely remove Ubuntu (or Linux) OS safely without casuing any trouble to your Windows XP later on.

Pre-requsite

This is not a guide to installing Ubuntu (or Linux). I assume you know how to actually install Ubuntu (or Linux) to your computer. Its just a way out to try out Ubuntu or Linux without casuing any hassles with windows xp, for people who wish to dual boot windows xp with Linux. (mainly novice or new users.)

How to Do It

1.Suppose your windows xp is installed on Drive C.
2.Suppose you have another partition in windows xp namely D.
3.Now you want to install Ubuntu or anyother Linux on remaining space.
4.When you install Ubuntu, Ubuntu collects all the information from you like language, keyboard layout. etc. then comes partitioning. 
Here For example you create two partition,
(i). Swap 	=	/sda/hda3
(ii). Root	=	/sda/hda4
5.Now in the last page, when ubuntu installer displays all information you have selected, there is a tab below : Advanced. Click this tab. It shows Grub installation location to be (hd0). Here, you got to make it (hd0,3).
[Explanation : In linux, partition starts from 0. so your C drive is (hd0,0). Your D Drive is (hd0,1). Your Swap partition is (hd0,2). And hence, your root partition is (hd0,3). 
			By default Ubuntu installer installs grub boot loade to (hd0), that is it overwrites MBR. (Though you can boot windows XP from GRUB menu also. It detects Windos xp 
			and shows it in the list when you boot.) But the problem arises when you wish to uninstall ubuntu (or Linux) later. here, when you format you linux partiton from 				windows xp, grub still remains as it was written to MBR of your hard disk.]

	[ I have presented here a very simple configuration, but the mehtod and concept remains same. so if your partition setup s different, just apply simple logic and this method to know what 	to write in place of (hd0).]

	[ This is the case with Ubuntu installer. In other linux distro's installer, there is always an option to change install location of Grub boot loader. So just do it by simply looking for the 	option in your Linux distro installer. ]
	
	6. Now boot to your windows xp. Download a small program Bootpart (google it. its free and just few kb). Save tis to you C: drive. Unzip it. rename the folder as bootpart.

7. Open Run From Start Menu. type “ cmdprmpt ” or start MS-DOS command promp from Accesories in start Menu. 

(i). In Command prompt type “ cd\ ”. Press enter. ( to get to location C;/) 
(ii). Enter bootpart direcory by typing “ cd bootpart”. now type “ bootpart “.
	
	you will see a list, showing your partitions. Notice a line similar to below :

		“ 9 : D:  type=83  (Linux native), size = 296944 KB “

	Here this no . is 9 for linux native partition. Note the number in your case. 

	Then type this command : “ bootpart 9 bootlinx.bin Linux “. [ replace no. 9 with your no.]

	then close it and reboot. you will see Linux on boot list. select it. and you will get grub to boot your Linux OS.

	8. Now if you wish to remove Ubuntu OS (or Linux) from your computer. Just boot in windows XP. Use any partitioning manger like Acronis Disk Director or Nortopn Partiton Magic, 	to remove Linux Partitions. The to remove Linux entry from windows boot loader, just “ c:/boot.ini “ in windows explorer location bar. A file will open up in notepad. Remove the last 	line showing Linux entry.
	    
		Here you have your computer in condition, similar to prior to installing Ubuntu (or Linux).

---

### Post by Azoix on 2007-07-13
**[COLOR="Blue"]Just curious, i have a dual boot set-up on a different pc to my laptop , can i use the same removal method for taking the linux boot option out of the pc if i have it installed to the  MBR and have removed the distro already ? Or am i stuck with the bootloader listing it in the MBR record?[/COLOR]**

---

### Post by betamaxman on 2007-07-13
You can also boot xp and ubuntu with gag from cd.
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by phr0ze on 2007-07-13
Thanks for the guide.

---

### Post by Seisen on 2007-07-13
You should submit this the the tutorials and tips section. Just make sure that their isn't one exactly like it their.

---

### Post by adromidon on 2007-07-15
Also you should note the location to download the bootpart software as i am not sure it is included with XP by default.

---

### Post by benx009 on 2007-07-15
good guide:)

---

### Post by Wiebelhaus on 2007-07-15
Great guide! thanks for the write up.




on a side note: and not to jack the thread , but I don't understand what's wrong GRUB? GRUB is stable , customizable & does precisely what it's supposed to , If something goes wrong you can within 5 minutes restore both XP & vista bootloaders , Also the Ubuntu people have made it so freaking easy , I just don't understand why people want to complicate something that works absolutely perfect.

---

### Post by bme on 2007-07-15
> **sx66gns said:**
> on a side note: and not to jack the thread , but I don't understand what's wrong GRUB? GRUB is stable , customizable & does precisely what it's supposed to , If something goes wrong you can within 5 minutes restore both XP & vista bootloaders , Also the Ubuntu people have made it so freaking easy , I just don't understand why people want to complicate something that works absolutely perfect.

As stated on the post,overwriting the MBR with grub might cause some problems for the uninitiated...Like for example you don't have a xp or vista cd to restore the MBR....

for Booting purposes I use EasyBCD. It can make a backup of the vista boot loader...

---

### Post by adromidon on 2007-07-15
Some people prefer to use the windows boot loader for what ever reason it is nice to know how to configure it both ways so you can make your choice but yes grub is easier to configure however some people are just confortable with the windows boot loaders

An example would be if someone was only going to use Ubuntu for a short time then go back to Vista or XP they would not want to load the windows recovery console to fix the boot sector and MBR

---

### Post by Azoix on 2007-07-16
> **sx66gns said:**
> Great guide! thanks for the write up.




on a side note: and not to jack the thread , but I don't understand what's wrong GRUB? GRUB is stable , customizable & does precisely what it's supposed to , If something goes wrong you can within 5 minutes restore both XP & vista bootloaders , Also the Ubuntu people have made it so freaking easy , I just don't understand why people want to complicate something that works absolutely perfect.

[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Just to add my 2 cents on this subject , again,
I had dual boot , XP and Ubuntu, then XP and Fedora7, both using the write to MBR and GRUB bootloader, i tried LILO aswell, and both work without error, but i lost the system, through experimentation before trying the above steps to dual boot without either loader.

As a side note for those wanting to try dual boot, but cant work the above, i found online a Graphical bootloader, opens as a neat click button load page,supports up to 9 operating systems in one bootloader menu.

**[COLOR="Red"]DRAWBACKS :[/COLOR]** 
Only works with the LILO loader, and Ext2 file system, cant see reiserFS or Ext3.
Once installed,if you remove it, it takes LILO with it, and makes it almost impossible to then boot into the linux partition,without a rescue disk, and means of booting to it, as XP always takes over as default,when it cant find the normal MBR anymore.( At least it did in my case)

Possibly UNSTABLE, was fine when first installed, but on a second attempt ,with 3 Operating Systems installed on the one HDD, the loader wiped the MBR and drive completely.
USE WITH CAUTION and BACK-UP FIRST !!!!!!

Try It :

 **[FONT="Comic Sans MS"][SIZE="4"][COLOR="Red"]   GAG 4.9 [/COLOR][/SIZE][/FONT]**
Just enter the name in google, download and copy to floppy.[/COLOR][/SIZE][/FONT][/B]

---

### Post by adromidon on 2007-07-16
By default i do not think Ubuntu supports Lillo does it? I think you have to install it seperately

---

