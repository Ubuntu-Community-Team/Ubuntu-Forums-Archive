---
title: "Ubuntu shows up twice on Bootup Menu"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by TSPetersInc on 2007-08-10
Hi All,

 So I have just installed Ubuntu 7.04 and everything works fine except that on the BIOS bootup sequence, (GRUB?) Ubuntu shows up twice on the menu. This only happened after I downloaded the system updates after installing and using Ubuntu the first time. So basically, how do I get rid of the second unused bootup option for Ubuntu. All I would like to see is the options for my current Ubuntu, Windows XP Professional, and Other Operating System listed when GRUB starts. Its not a huge deal but it is kind of annoying and weird to me to see two options to load my Ubuntu. I'm also really new to using Linux so if you do have a suggestion please make it noob friendly? Thanks so much guys!

---

### Post by yuvlevental on 2007-08-10
You upgraded your kernel, the core of Ubuntu. The extra option boots you into the previous kernel for recovery mode if your current kernel suffered damage.

Hoped that helped,
Yuval A.K.A. Imperius

---

### Post by mysticmatrix on 2007-08-10
Well the fact that there are two entries of Ubuntu is not a problem. They are simply two slightly different version of the Linux Kernal.
 Sure htere exists ways to remove entries to the older kernal(which exist to make sure that you can use it in case of any compatibility problems relating to hardware or softwares).
 Therefore its probably good idea to keep those entries, and I don't think so that they contributr to a problem.

---

### Post by g2g591 on 2007-08-10
this is perfectly normal, and occurs after a kernel update, as a backup in case something breaks during the update. if you really want to remove it, you can use (in the terminal) "sudo gedit /boot/grub/menu.list" it will prompt you for your password, which you should put in, then you can delete the unwanted entry. Also if your using kubuntu, replace gedit with kate.
edit: darn, too long typing this

---

### Post by TSPetersInc on 2007-08-10
Ok, so I understand that it is there in the case my current Kernal / Ubuntu has a problem, but I already have a "Recovery Mode" option for the current Kernal I am using. So why would I need another Ubuntu if I already have a recovery mode option for the current bootup. Right now the Ubuntu options are:

Start Ubuntu
Start Ubuntu (Recovery Mode)
Run memtest86
and another one maybe, but I dont remember at the moment.

Don't quote me on those since I diddnt write down the boot options, but the question is since I have a current recovery bootup option, whats the point of having 2 kernals listed for Ubuntu to load up?

---

### Post by benerivo on 2007-08-10
The grub bootloader will show boot options for each linux kernel that your Ubuntu is based upon. One of your updates was a new kernel so you have two sets of Ubunto boot options. To delete the old one which is of no use to 99% of users, then go to /boot/grub/menu.lst and delete the old kernel entries. Also, you can go in to synaptic and uninstall the old linux-headers.

The reason you have two, is that linux 'always gives you the option', so if you prefer the performance of Ubuntu under the old one you can make your own choice. I think it's really for developers of programs.

---

### Post by TSPetersInc on 2007-08-10
"sudo: gedit/boot/grub/menu.list: command not found"

I get this message when trying to input your stated command in termina. Any other suggestions?

---

### Post by bigboy_pdb on 2007-08-10
I don't think that it's a good idea to remove the additional boot options. If you don't want them you should do what g2g591 suggested but instead of removing the lines put a # character at the beginning of the lines that you don't want. This will comment them out and if you need them later then you can replace them by removing the # at the beginning of the line. Also, if there's any problems that result from commenting out a line you can use Live CD to boot into Ubuntu, you can mount the partition with the "menu.lst" file, and then you can edit it using gedit from the Live CD.

---

### Post by kirios on 2007-08-10
[COLOR="DarkRed"]Press Alt and F2, then type **gksudo gedit /boot/grub/menu.lst** in the dialog box that appears. 
When the menu.lst file opens in gedit, comment out the lines for any options  you don't need (by adding # in front)[/COLOR]

---

### Post by TSPetersInc on 2007-08-10
Well I have the menu.list open but it looks like it is blank. There is a tab for menu.list but nothing is written in the text area. Is this normal? I don't see anything to even edit in here.

Edit: I checked again. I wish I could post a picture of what the menu screen looks like, but I can definitely access the suggested area from terminal but I do not see any text what so ever, not even a mention of the current bootup options. Am I doing something wrong? This may sound incredibly stupid but is the GRUB on my first HD using WindowsXP? When I had to remove GRUB in the past after uninstalling Ubuntu, I had to run MSWindows Recovery mode from CD and input "FIXMRB" to remove the grub. I dont know. Any suggestions?

---

### Post by mysticmatrix on 2007-08-10
> **TSPetersInc said:**
> Ok, so I understand that it is there in the case my current Kernal / Ubuntu has a problem, but I already have a "Recovery Mode" option for the current Kernal I am using. So why would I need another Ubuntu if I already have a recovery mode option for the current bootup. Right now the Ubuntu options are:

Start Ubuntu
Start Ubuntu (Recovery Mode)
Run memtest86
and another one maybe, but I dont remember at the moment.

Don't quote me on those since I diddnt write down the boot options, but the question is since I have a current recovery bootup option, whats the point of having 2 kernals listed for Ubuntu to load up?

Well the point is not of recovery, but hardware support. Suppose your favorite printer(a old one) doesn't works correctly due to change on kernel support, then you can always boot to the older kernel and get hting done, instead of dual booting wth various versions of Ubuntu( like the Win Vista/XP dual boot, quite popular these days)

If you want however, you can always remove those entries, by editing the required file.

---

### Post by bigboy_pdb on 2007-08-10
It sounds like there's no "menu.lst" file in the place that you're trying to look for it which means that you're somehow accessing the wrong folder or the file isn't in the "/boot/grub" directory. Try typing "sudo find / -name menu.lst" to find the file.

---

### Post by benerivo on 2007-08-10
Careful how you typed that command line, otherwise you'll create a new (blank) file to edit rather than opening an existing. The correct entry is ```
sudo gedit /boot/grub/menu.lst
``` not menu.list

---

### Post by kirios on 2007-08-10
> **TSPetersInc said:**
> Well I have the menu.list open but it looks like it is blank.
[COLOR="DarkRed"]You've created a new file. 
Type menu.lst (_not_ menu.list).[/COLOR]

---

### Post by TSPetersInc on 2007-08-10
Whoops! So I can see the menu.lst now. How do I get ride of that file I created now? lol

---

### Post by bigboy_pdb on 2007-08-10
sudo rm /boot/grub/menu.list

and I suggest that you copy and paste that command so you don't actually type "menu.lst" this time (by accident because it would probably have devastating effects).

---

### Post by bigboy_pdb on 2007-08-10
By the way if you're worried about making a mistake in the command line for things like this you could open a terminal and type "sudo nautilus" and a file browser with root permissions will open and you can delete the file from there.

**EDIT:** The command should be "gksudo nautilus" as Paul133 suggested in the following post. Sorry about that. I'm aware it should have been gksudo but I've gotten used to using sudo within the command line for command line programs.

---

### Post by Paul133 on 2007-08-10
Wouldn't "gksudo nautilus" be better than "sudo nautilus"?

---

