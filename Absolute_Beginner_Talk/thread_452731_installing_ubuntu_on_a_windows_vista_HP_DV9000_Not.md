---
title: "installing ubuntu on a windows vista HP DV9000 Notebook"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by m1e1w1 on 2007-05-23
i have made the choice to install ubuntu on my DV9000 HP notebook, but it wont install.
my notebook specs are:
2GB ddr ram
2.0 GHZ AMD Turion64 x2 tl-60
120GB HD in 2 partitions
Nvidia Gforce I express 16
current OS - Windows Vista Home Premium

installing- ubunto 7.04 AMD 64 version
i attempted to boot ubuntu from the disk, selected default install method. it hangs up, and or sends out firmware errors, and has a problem with system bus and beeps.

i had also tryed installing the older 6.10 x86 version, but with the same results.

how can i start the install?

---

### Post by Inxsible on 2007-05-23
Can you be more specific as to what errors are you getting?
 
Does it hang while partitioning or while doing the install ?
 
Try these links for a step by step in partitioning and installing :
 
[SIZE=2][COLOR=#008000][www.**psychocats**.net/ubuntu/**partitioning**]("http://www.psychocats.net/ubuntu/partitioning")[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][www.**psychocats**.net/ubuntu/**installing**]("http://www.psychocats.net/ubuntu/installing") [/COLOR][/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=#008000]If you noticed, I have the same machine except for the processor and the fact that I installed the 32-bit version of Ubuntu. So installing shouldn't be a problem. Is there any specific reason you need the 64-bit version?[/COLOR][/SIZE]

---

### Post by dan171717 on 2007-05-23
does the live cd run??? if it doent then choose safe vga mode. it is one hell of a laptop youve got there so that probbly wont work but it is worth a shot. if that doesnt work try another distro. say dsl maby. of that doesnt work you drive or bios wont want to load a kernel or whatever of a cd.

---

### Post by m1e1w1 on 2007-05-23
ive only got as far as loading the hardware, right after restricted drivers, and it locks up.
ive tryed tweaking the boot line, from pressing F6 and ive got it all the way up to loading gnome background, then it locks up. i get several verious fermware errors, and the one time i got to the gnome background, it did a clicking sound repeadly and locked up, before even loading the top white bar, and icons in the setup pictures i looked at.

spacificly the errors im getting, i dont know what they all mean. but they have to do with not being able to load hardware drivers.

it has problems with loading something for the networking, and something else right after that causes the system to beep, like error beep code.

ive got the DV9000z CTO also has the bluetooth wireless

---

### Post by m1e1w1 on 2007-05-23
just tryed vga mode, and it loads up to the orange bar, going from left to right, solidly (gets pass the back and forth motion) about half way, then locks up. tryed twice.

---

### Post by MikeDK on 2007-05-24
this is obviously a commonly "known" problem.

ive installed on a dv9232eu also amd turion x2

there seems to be problems with some of HP's firmware refusing to be deleted, but i did this:

tryed several ubuntu-versions untill i tryed the Old 5.04 version, and still got these firmware errors. But I was allowed to install.
after this i was told that it could be solved by using the fwcutter-package to get rid of the firmware, and so i did, now the only thing remaining is the "failed to allocate mem resource" problem. but that seems to be a big problem for a lot of laptop with duo core, or X2 CPU's
N.B. hope its a help

Kind regards MikeDK

---

### Post by m1e1w1 on 2007-05-24
ive gotten some additional information, and was able to boot the demo OS, to start the install.

current problems:

screen resolution only goes up to 800x600 max. (windows are cut off) in demo mode during install.

i want to install ubuntu on my smaller partition, having partition 1 with /windows and ntfs format table (windows vista home premium) and partition 2 with / on  the ex3 format table
(no swap space) i.e. 2GB of ram. or do i need swap space?

when it nearly completes the install, "Grub can not be installed" error. and the install quits.

how do i configure the partitions to keep windows, and dual boot. formating only the smaller #2 partition for ubuntu?

or, to explain it, i have a 120gb HD. I want to use a 20gb partition for ubuntu. windows vista is already installed. the partition im going to install ubuntu is already made up, as 20gb. when i go to install ubuntu, how do i manualy set the locations? partition 1, is it /windows NTFS and partition 2, / ext3? and i belive a little extra space for /home swap?  im just asking to make sure, becuse i dont want to use the windows vista partition (largest amount of space) for default install. i already know what to do with configureing GRUB once its all installed.... just not sure how to tell the lunix partition that i want ubuntu and windows seperate.

---

### Post by m1e1w1 on 2007-05-24
did a search on the fourms, don't see anything about what to call the partitions.

i was thinking of building 3 partitions perhaps.

#1 for windows vista witch i thought should be /windows NTFS
#2 for ubuntu witch i though should be / ext3
#3 for swap space (if its needed) witch i though should be /home Fat32

id like to make sure its right before i procide with install... though since my screen resolution is cutting half the windows off, it will be hard

---

### Post by MikeDK on 2007-07-19
by the way, do any of you have the F28 Phoenix Bios or F27
and have you upgraded the BIOS and how did you do it

Kind Regards MikeDK

---

### Post by Brightbelt on 2007-07-19
I installed Ubuntu Studio 32-bit on my HP DV9030us laptop and most everything worked right out of the box.

The webcam has yet to come through but I haven't spent much time on it either. 

I've always understood that the general consensus is that you'll have a much easier time and a lot less headaches by sticking to 32-bot.

Just a thought.

Frank B.

---

### Post by dan171717 on 2007-07-21
try a alt-install cd

as for swap. it needs to be linux-swapformat and mount point must be set as swap

as for grub do you have a /boot partion

---

