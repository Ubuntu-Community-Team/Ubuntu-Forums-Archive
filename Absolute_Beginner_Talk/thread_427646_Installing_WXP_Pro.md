---
title: "Installing WXP Pro"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by misterz on 2007-04-29
I'm an absolute beginner at Ubuntu. I built the computer yesterday and installed Ubuntu. Works great. But, I want to install XP Pro as a dual boot, now. Have not a clue. Where can I get step by step instructions? Also, is there a "Ubuntu for dummies" out there? Basic things, like how to download and install new programs, are a complete mystery. Something oriented like "in Windows, it's called this. In Ubuntu, it's called that".
Thanks!
-Mark :(

---

### Post by Ganda_Melga on 2007-04-29
Well... I suppose the usual way is to partition the HD in two, or like me have two HDs. I think will be easier if you install Windows first and then install Ubuntu. Install Windows in the first partition and Ubuntu in the second partition. At the end of the Ubuntu instalation, it install something called GRUB. This grub will allow you to choose wich sistem to boot from. I'm a newbie, can't help anymore than this. Sorry.

---

### Post by oilchangeguy on 2007-04-29
you'll find it alot easier if you install windows first. then ubuntu.
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ganda_Melga on 2007-04-29
> **misterz said:**
> I'm an absolute beginner at Ubuntu. I built the computer yesterday and installed Ubuntu. Works great. But, I want to install XP Pro as a dual boot, now. Have not a clue. Where can I get step by step instructions? Also, is there a "Ubuntu for dummies" out there? Basic things, like how to download and install new programs, are a complete mystery. Something oriented like "in Windows, it's called this. In Ubuntu, it's called that".
Thanks!
-Mark :(

Ah...there are some tutorial out there, but I'm a bit lazy to find them. To install programs it's a breeze. In the main menu there's a ADD/REMOVE option. You install most of the stuff from there.

Also I found out that there are packages that auto-install. They have the extension DEB. If you're as dumb as I am, you will not be able to play music, because of some restricted formats thing. And don't forget to enable the repositories. Every doubt I had was answered here by other members wiser than me. Stick around and don't be afraid do ask. :popcorn:

---

### Post by misterz on 2007-04-29
I tried to go back and install XP Pro. I tried using Partition Magic to format the drive. But, I'm finding that the XP disc I have is not bootable. Plus, even when I repartition anmd format I'm finding that on boot up there's still some Ubuntu left. It shows it's attempting to load Ubuntu but fails. Really no clue what to do.

---

### Post by rapmuzick on 2007-04-29
To install software you can either:

1) search for stuff in the Applications --> Add/Remove thing
2) search for packages in Synaptic (sometimes you can find package information like the name & all that online)
3) use the terminal command "sudo apt-get install <whatever>", where <whatever> represents the package name

Occasionally you might find a .deb (Debian installer package) which works kinda like a .exe install program in windows. On rare occasions you may have to compile the program yourself, but I've never had to do that.

Check [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by annda on 2007-04-29
you have GRUB left on your hard disk. to get over this, you need to either use the ubuntu cd or the windows cd, depending on what you plan to do next. if you want to dual boot, you need to install windows now. how come the windows disk is not bootable? a system cd MUST be bootable. is it a recovery disk? in that case, you can still boot from it and reinstall, but probably all the partitioning will be lost.

---

### Post by Terl on 2007-04-29
> **misterz said:**
> I tried to go back and install XP Pro. I tried using Partition Magic to format the drive. But, I'm finding that the XP disc I have is not bootable. Plus, even when I repartition anmd format I'm finding that on boot up there's still some Ubuntu left. It shows it's attempting to load Ubuntu but fails. Really no clue what to do.

That sounds like a bad windows disk.  Every winXP disc I have had boots.  The windowsXP cd is used as a recovery cd too so it should boot.  Are you set to boot from cd first?

---

### Post by dfreer on 2007-04-29
Welcome to ubuntu! ok basically the eaisest way to dual-boot is to install windows XP first, and THEN install ubuntu. You CAN install windows after ubuntu, but bascially what will happen is windows will boot exclusively, and you will need to use a linux live cd to fix things so that you can dual boot. Ubuntu will automatically set up a dual boot enviroment if windows is installed first, and ubuntu installed afterwards.

Well, I dunno if there is a equivelent to what you are looking for. Ubuntu Guide (check my sig for the link) has step by step instructions to install the most common programs, the only thing you need to know is how to open a terminal window (similiar to a DOS prompt in windows). However, the disadvantage of ubuntu guide is that you are just copy+pasting commands, maybe not learning anything but that isn't such a big deal.

Basically, this is some of the things I taught my sister when she was learning to use Ubuntu for the first time:

root account is similiar to Administrator account in Windows XP. as a normal user in ubuntu, you do not have nearly as many privileges as a normal user in Windows. Ubuntu is designed this way, and it is a good thing. if you ever use the command line, you will need to learn about sudo.

The start menu in windows is similiar to the 3 menus at the top left of your screen. specifically, Applications = All Programs, Places = My Computer, and System = Control Panel.

The command prompt/DOS prompt in windows is similiar to the terminal in Ubuntu, the only difference is the terminal is EXTREMELY powerful, pretty much anything you do in the GUI has an equivelent command in the terminal. That is why whenever you ask for help, the majority of the time your answer will be "open up the terminal and type..."

Add/Remove Programs in windows is = Synaptic Package Manager. Note, however: In windows it is only possible to Remove programs using this tool, and the only "Adding" of programs is installing windows components and running a .exe from CD or disk. Synaptic package manager actually contains over 20,000 programs to choose from and download/install. the .exe in windows is = .deb in ubuntu, you *cannot* install .exe programs in ubuntu without wine.

Wine, BTW, is a program that you can use to install and run windows programs in linux. Not all programs will work, however quite a few will, check there website to see what does and doesn't. I currently run Half-life 2, steam, starcraft, Call of Duty, and a few others using wine and they work quite well.

Umm your Home folder is similiar to My Documents in windows, that's about all for now. Any specific questions and myself or someone else around here should be able to help you, this is probably one of the best and most active forums around IMHO.

---

### Post by dfreer on 2007-04-29
> **misterz said:**
> I tried to go back and install XP Pro. I tried using Partition Magic to format the drive. But, I'm finding that the XP disc I have is not bootable. Plus, even when I repartition anmd format I'm finding that on boot up there's still some Ubuntu left. It shows it's attempting to load Ubuntu but fails. Really no clue what to do.

Partition magic is pretty good for windows, but it doesn't always play nice. I would use the Ubuntu LIVE cd to repartition your hard drive, make sure to make at least 3 partitions. 1 = windows, 2 = ubuntu, 3 = ubuntu swap.
The MBR is the first 512 bytes of your hard drive, and when you install windows windows will automatically will wipe and install it's boot loader there. it doesn't give you a choice. So install windows first (after you figure out why you can't boot your XP cd), and then install ubuntu. you can't wipe the MBR without using special tools, that is why after using partition magic the ubuntu bootloader was still there.

if you tell us everything written on that XP CD, we can probably let you know about whether that cd should be bootable or not.

---

### Post by misterz on 2007-04-29
Firstly, thank you all! It is fabuous the way so many folk rush in to help. I think I'm going to enjoy this. 

The WXP Pro disk I have is a copy (consistent with the Ubuntu philosophy that OS's ought to be free :-) ). So, there's not much written on it. But, I discovered when I tried to boot from it on my other XP machine, it wouldn't. So..., it isn't a bootable disc. But, if you run it when the machine is already booted, then it autoruns fine. Now, I've got a W98 disc that appears to BE bootable. So.., given this what do you recommend? Can I somehow make the XP disc bootable? I tried some approaches I found on the web but none worked. Should I try installing W98 first as a meaans to upgrade w/. the XP Pro disc? Or, ...?:confused:

---

### Post by annda on 2007-04-29
> **misterz said:**
> But, if you run it when the machine is already booted, then it autoruns fine. Now, I've got a W98 disc that appears to BE bootable. So.., given this what do you recommend? 

the pirated xp you have is probably an upgrade. but you still need a serial number. if your win98 is legal and you have a serial for it, go ahead, install 98, upgrade to xp. do not install any programs, just go straight to ubuntu installation.

depending on how successful your previous partitioning was, you will get an empty partition to install ubuntu to, or you will need to partition the disk again.

---

### Post by Coucouf on 2007-04-29
I've been (re)installing Windows a few times in the past, and as far as I know, you won't get pretty far with a WXP disk that isn't bootable... The best you can do is probably find someone that still has a bootable WXP CD *plus* the Ubuntu philosophy to share it with you ;) 

By the way, I'm not sure how you possibly could partition your HDD with partition magic without installing Windows... or did I misunderstand ?

What seems to be happening to you is you indeed formated the Ubuntu partition so the system isn't there anymore.
But GRUB, the boot loader (that can let you choose between Ubuntu and Windows) is still there.

You should try and install WXP with a correct CD (it will erase GRUB, Windows beeing sooo interested in its environment :) ), and then install Ubuntu on top of it.

If you don't have a WXP CD and want to try an all-free life, just reinstall Ubuntu, it will setup your boot correctly again.

---

### Post by misterz on 2007-05-13
Actually, I was able to reinstall WXP from a non-bootable disk by going to the I386 directory and executing winnt.exe. I first got to there by using files from [www.bootdisk.com](www.bootdisk.com). Also, my Partition Magic can be used without Windows. Itself is a bootable CD. I finally got this solved, pretty much as you said, by reinstalling WXP and then Ubuntu. Things are nice now. Although, now I've got to learn the finer points of Ubuntu, which'll take some time.
Thanks!

---

