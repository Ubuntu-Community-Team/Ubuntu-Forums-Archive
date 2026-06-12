---
title: "Interesting Situation"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Cyann0923 on 2007-05-13
I seem to have backed myself into a corner and really have no idea what to do.  I have searched and found many how-to's related to my issue,  but none specifically targetting my situation.

I have two hard drives, one 250 gb and one 160 gb.  I decided to install Kubuntu on my second hard drive. When I installed it,  I unplugged my windows drive like the genius that I am. My bios does not seem to allow me to choose which drive is master and which is slave, so even without the windows drive, my linux drive is slave. I want to be able to run them both without unplugging one,  and I want to access either drive from either OS for ease of moving files before I toss windows. When I plug the windows drive in while I am in linux,  It shuts down and freezes the entire system. I know that there are some things I need to input somewhere in windows, and I want to use Lilo since it has more features than grub. Grub is my default linux booter, but I installed Lilo and want to make that the primary one,  then work my way around all this unplugging drives stuff and make swap space and all that. 
Has anyone seen a How-to that will help me with this issue, or does anyone have a way to workaround all this nonsense?
I am so new to linux that it hurts so any and all (civil) input is welcome.
Thanks in advance.

---

### Post by Thingymebob on 2007-05-13
I have never come across a bios that doesn't recognise master/slave configurations, are you sure you have set the jumpers on the hard disks correctly.

---

### Post by Malta paul on 2007-05-13
Hi,
I would say you need to change your settings in the BIOS 'Integrated Peripherals' If you happen to have a Amibios you would then go to 'On-Chip IDE Configuration' 
Each time you make a change, save your settings, reboot and enter the bios again then check the HD setting. A few tries you will get it correct. [don't forget to note your original settings though]
Hope this may help :)

---

### Post by seshomaru samma on 2007-05-13
what features does lilo have that grub doesnt?

---

### Post by eholly on 2007-05-13
The jumpers and/or the cabling determine the master/slave relationship. The bios can only recognize  a  good situation.  Plugging a drive in while in operation is probably not the thing to do. You can get the system working with either drive as master. 

          After you get things working, Win does not recognize the Linux file systems but Linux does recognize Win file systems.  It also does fairly well with Mac file systems.  

           The experts or nerds are swinging toward grub as the boot loader of choice because of its wide array of options.  Lilo works, seems simpler and is more logical to me. 

                  E Holly

---

### Post by mikewhatever on 2007-05-13
In this kind of setup, you need to boot from the drive Ubuntu is on. It will bring up GRUB, and in order to have a choice for Windows, you'll have to edit Grub's menu.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by Kal9001 on 2007-05-13
I will just confirm what others have said. the master/slave jumpers determine which drive becomes master for a given ATA channel. your drives may be set to CS (cable select) which means depending on weather your drive is on the end or middle connector on the cable. I find this the most awkward and always have my drives set.

The way I have my system set up is to use 1 drive to house Windows and Ubuntu and a swap plus 1 last bit for data. then the other drive becomes my bulk storage. so if the OS's ever go belly up I can remove my data drive with ease and sort the OS drive out without worry of corrupting all my data. 
also doing this means GRUB is easier to handle as its all on one drive and all the references are to the same drive.

It would be much easier if someone rethought the whole layered boot process and maybe took one step out of it by in cooperating a full boot loader into the BIOS/CMOS . . . then again due to the relativity low number of users who "dual boot" it wont change and we will just have to live with this slightly awkward system.

---

### Post by Cyann0923 on 2007-05-14
Thank you for all the replies. 
Concerning the cable deal. I have switched the linux and windows drives on the cables, and it still doesn't do anything.  I will continue to work out the bios issues. Been kinda scared about messing something up there, I have never really needed to change anything on it before, but I will tinker with it. 
I would put both on one hard disk, but I have a lot of extra data on the windows hard disk that I didn't want to move, and I thought dual booting from two drives would be easier. Really didn't plan it out well enough. I can save all of my settings in Kubuntu and then move it over to the other drive, right? Is there a how-to for switching drives that Kubuntu is on? This may take me a couple of tries, but I will get this working. 

And I am definately not an expert, may be a geek in the highest,  but not an expert. If grub is really the choice to go with, then I will keep that, but if it is too much more complicated than lilo...
Opinions on boot loaders?

---

### Post by Cyann0923 on 2007-05-20
Alright, got windows as slave and Grub edited. 
Go to boot windows and get none other than the blue screen of death. I can hear women screaming and men gnashing their teeth.
Windows was stopped because of an unknown error. 
So Reboot, safe mode. Press escape to stop sptd.sys. Ok?
Stop it. Blue screen, women scream, etc.
Windows was stopped because of sptd.sys. It made itself pageable when it is not. 
So after 20 minutes of different configs,  I realized that windows has proven it's worth to me. 
I googled said sptd.sys and found that it is part of daemon tools. I feel that I am now out of choices here.

Does anyone have any advice for me at all, or should I try a windows forum. I don't think that my issues have anything to do with Kubuntu or Grub, but I have important stuff on that drive, stuff I want to use in Kubuntu when windows has died the terrible death. 
Can I get some help please?

---

### Post by Cyann0923 on 2007-05-20
All issues fixed.  Windows boots fine, Can access the drive in linux. All is well.
Thank you chkdsk.

 I appreciate all the help.

---

