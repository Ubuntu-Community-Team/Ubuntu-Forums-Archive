---
title: "U Have To Help Me Now!"
date: 2005-04-11
forum: Apple PPC Users
---

### Post by ninjag5 on 2005-04-11
ok so i installed ubuntu linux , whipes the mac hard drive and now i want mac back on there and ubuntu off

i putt in the mac osx installer cd, it all runs fine untill its gets to 

"Select a destination volume to install the Mac OS X software"

IT HAS NO HARD DRIVE it cant find the hard drive i cant reinstall it what the F and im gonna do now im worrying i wanted to whipe the mac anyway and reinstall again people said it would be simple as anything to do but it isnt i cant install :(


ill see if it can do it with disk utility but if not be warned heads will roll

---

### Post by ninjag5 on 2005-04-11
ok your all very lucky panic is over i can reinstall now, in future i want to know how to dual boot so if anyone can point me in the right dirrection that would be fantastic thanks!

---

### Post by kassetra on 2005-04-11
[QUOTE=ninjag5]ok your all very lucky panic is over i can reinstall now, in future i want to know how to dual boot so if anyone can point me in the right dirrection that would be fantastic thanks![/QUOTE]

In the future, please note that you'll get more responses with honey than you will with vinegar.

This should at least get you started:

[font=arial][size=-1]**Installing Ubuntu:**
In order to install Ubuntu on your Mac, make sure you have 2 smaller partitions empty for your Linux install. Insert an Ubuntu install disk and reboot.
 [/size][/font] [font=arial][size=-1]After installing Ubuntu into these two smaller partitions (one for Ubuntu and one for the Boot Options), it should proceed like normal, and allow you to boot into Ubuntu and finish installing.. [/size][/font]

 [font=arial][size=-1]*note: Ubuntu doesn't automatically see the wireless Airport card built into any Mac. The Airport wireless cards aren't supported by Linux because QUALCOMM hasn't released those specs to the open source community. You will need a standard ethernet device.
 [/size][/font]

 [font=arial][size=-1][b]
Editing the boot sequence:[/b]
Yaboot controls the boot sequence on Macs with Linux installed, letting you choose which operating system you want to use. By default, it offers a 15 second window to decide which OS, then defaults to Linux. If you want your computer to default to Mac OS X instead of Linux, there's a great yaboot reference document online at the yaboot site ([http://penguinppc.org/bootloaders/yaboot/]("http://penguinppc.org/bootloaders/yaboot/")). 

However, the changes are fairly easy to do: in the file /etc/yaboot.conf you need to add defaultos=macosx.  [/size][/font][font=arial][size=-1]The second - and critical - step is to actually install the updated bootstrap loader configuration file, and that's done with /sbin/ybin -v, which figures out where the new configuration file should be moved to and does it. [/size][/font]

---

### Post by ninjag5 on 2005-04-11
what size should i make these partions?

---

### Post by ninjag5 on 2005-04-11
and sorry for being so nasty i was upset  :neutral:

---

### Post by Len on 2005-04-11
Well, the description makes things a bit complicated.

It depends on what you will do with that partitions. If you are just playing with FireFox, Gimp and OpenOffice, 5 GB will be more then enough. If you want to compile every app you come across yourself, you probably need over 10 GB. If you want to make Linux your main system, well, fill in yourself.

Technically Ubuntu will be fine with a 3 GB partition. Still enough space left to install additional apps and to create some documents.

I'd take my steps like this:
- Put in the OS X installer CD and boot from it (hold 'c')
- Choose "Disk Utitily" from the "Installer" menu.
- Create two partitions (or more if you'd like one for Mac OS 9 as well), one for the Mac, and a placeholder (linux, make it 3 GB or more). Choose "Free Space" in the "filesystem" menu!
- Name the OS X partition and write the changes to the disk (this will erase your drive of course)
- Install OS X on the OS X partition

- Put in the Ubuntu CD
- Boot from it
- READ the message "Ubuntu comes with ABSOLUTELY NO WARRANTY!". Just teasing, couldn't resist ;-).
- When the installer presents you a screen about how to partition your disk, just choose "use free space" to allocate a swap and linux partition in the free space. Easy as that! Really :)

I hope this makes things more clear.

---

### Post by ninjag5 on 2005-04-11
hmm yes everything good except the " this will erase ur disc of corse" lol

---

### Post by ninjag5 on 2005-04-11
so i create 2 partions? eg. 1 called Macintosh HD 
1 called Linux

is that right? 

or do i make 3 eg. 1 macinotsh hd , 1 linux, 1 free space

---

### Post by Len on 2005-04-11
No, you create 1 macintosh, and 1 free space of minimal 3 GB

Linux will automatically create partitions for you in the free space.

---

### Post by ninjag5 on 2005-04-11
ok sorted, i created 2 partions one named macintosh HD and for simplicity i named the other linux and its 5gb

---

### Post by ninjag5 on 2005-04-11
WHAT SHOULD I PUT AS A MOUNT POINT??
and mount options?
bootable flag??

---

### Post by eBeL on 2005-04-11
[QUOTE=ninjag5]ok sorted, i created 2 partions one named macintosh HD and for simplicity i named the other linux and its 5gb[/QUOTE]
 Correct me if I am wrong but I think ^this is wrong.

You need to create a prtition for mac os x, Macintosh HD, and one that is just free space.  Free space has no name or file system on it.

When you choose to install Ubuntu on the free space it creates a swap partition and a partition for Ubuntu. (Once again, correct me if I am wrong.)

---

### Post by ninjag5 on 2005-04-11
I DONT KNOW  :shock:  :oops:  :(  :( need more help

---

### Post by eBeL on 2005-04-11
[QUOTE=ninjag5]I DONT KNOW  :shock:  :oops:  :(  :( need more help[/QUOTE]

Alright, so you have nothing installed on your computer.. right?

Fire up holding C with the Mac OS X installer.  Open Disk Utility and partition your HD.  Create two partitions: Mac OS HFS+ named Macintosh HD(Or w/e u call it) and one with no name with the type as Free Space.

Install Mac OS X on the partition Macintosh HD.  When complete:

Start up the Ubuntu CD and install it on partition labeled FREE SPACE and has the amount of space specified when you partitioned it.

If all goes well you should have Ubuntu installed completely after your first boot into Ubuntu.

if successful and you want yaboot to automatically boot into Mac OS X after 10 seconds:

Boot into Ubuntu
Open Terminal

Run command "sudo nano /etc/yaboot.conf"

Add the line "defaultos=macosx"

Save and exit.

---

### Post by ninjag5 on 2005-04-11
done :D

=me and you happy  \\:D/

---

### Post by eBeL on 2005-04-11
[QUOTE=ninjag5]done :D

=me and you happy  \\:D/[/QUOTE]
 Wow, you got both installed awfly fast

---

### Post by ninjag5 on 2005-04-11
well linux ubuntu is still installing but almost done, in anycase i no that mac and ubuntu are going to work side buy side perfectly

---

