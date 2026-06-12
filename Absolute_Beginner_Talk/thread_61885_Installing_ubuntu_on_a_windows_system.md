---
title: "Installing ubuntu on a windows system"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by tst on 2005-09-02
Hey All, I'm new to linux.

I've been reading all these threads on MBR, and its kind overwhelming. I have windows currently installed, and plan to install Ubuntu. Before I proceed with the installation, I'd just like to get a few things clear, just in case i screw up everything.

I'm using a laptop, a 60 gig drive. I have three partitions already, and some non-partitioned free space which I've created using partition magic. I plan to install Ubuntu (root and swap) in this free space. So I've been hearing about GRUB, hell, i don't even know what that is, but I really don't want Ubuntu to terminate my access to windows by mucking around with the MBR and whatnot. So my question is, is my current partition setup okay? What should I do in the installer to ensure that my windows (and access to it), and other existing partitions are not overwritten, etc?

Many Thanks.

---

### Post by Brinstar on 2005-09-02
[QUOTE=tst]Hey All, I'm new to linux.

I've been reading all these threads on MBR, and its kind overwhelming. I have windows currently installed, and plan to install Ubuntu. Before I proceed with the installation, I'd just like to get a few things clear, just in case i screw up everything.

I'm using a laptop, a 60 gig drive. I have three partitions already, and some non-partitioned free space which I've created using partition magic. I plan to install Ubuntu (root and swap) in this free space. So I've been hearing about GRUB, hell, i don't even know what that is, but I really don't want Ubuntu to terminate my access to windows by mucking around with the MBR and whatnot. So my question is, is my current partition setup okay? What should I do in the installer to ensure that my windows (and access to it), and other existing partitions are not overwritten, etc?

Many Thanks.[/QUOTE]
 Welcome to linux :)

you can use a specially-made bootable cd, the website is located at [www.sysresccd.org](www.sysresccd.org)

Also you could try Norton Partition Magic, but thats probably overkill...

edit: also try this link -> [http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)

---

### Post by tst on 2005-09-02
Thanks! I think i'll try to go along with the guide, and download the system recovery just in case i screw up.  :smile: Lets hope for the best.

---

### Post by byen on 2005-09-02
hey tst. welcome to Ubuntu.
Before I answer the question ...how much free space are you talking about ? I would say a safe bet would be over 5gb. Now coming back to the issue...asssuming that you have already downloaded the ISO file from [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) and that you have burned it onto a cd using "burn ISo/ burn Image" function. THis is what you do:
1.Start the PC and set the Computer to boot through the cd  (primary boot)
-this can be done by pressing f2/f6/or esc to get to the bios menu
2.restart the pc with the burned ubuntu cd inserted
3. You would get a menu where it will give you info abt your hd and you can choose the free space from there and select that drive to install it. (you can also format drives from here.... its easy as click-click) (remember to format the drive you wish to install ubuntu in is formatted into ext3-format)
4. Around this stage..it will show you the list of other operating systems on your pc and will ask you if you would want to install grub into the MBR
(what grub is ..is a menu that pops up during system boot to help you select the OS you would like to boot into....nothing much really)
 
the rest is easy to follow......try it out...let us know if you need more help.

---

### Post by tst on 2005-09-02
I have about 10gbs of free space. This installation seems relatively easy from the guide. I hope i don't encounter the same problems as others have with the MBR and GRUB.

---

### Post by byen on 2005-09-02
[QUOTE=tst]I have about 10gbs of free space. This installation seems relatively easy from the guide. I hope i don't encounter the same problems as others have with the MBR and GRUB.[/QUOTE]
 just select the option (yes) for "install grub into MBR" . Its pretty simple. dont worry...goodluck.

---

### Post by xequence on 2005-09-02
Grub and MBR - MBR is has boot loader that loads the OS. Windows has its own that only allows you to boot windows. When you put grub to the MBR it will delete the windows boot loader and you will have a choice of what OS you want, ubuntu, windows, or whatever other OS you use. Installing windows again will overwrite grub with a windows only loader so you will need to install grub again.

---

### Post by tst on 2005-09-03
Thanks for all the help people, I had a sucessful install and everything seems to be working quite nicely. I'll be sure to search around the forums if i have any other questions.

First Impressions: Everything runs nice and smooth. I like it.

---

### Post by poofyhairguy on 2005-09-03
[QUOTE=tst]Thanks for all the help people, I had a sucessful install and everything seems to be working quite nicely. I'll be sure to search around the forums if i have any other questions.

First Impressions: Everything runs nice and smooth. I like it.[/QUOTE]

welcome.

---

