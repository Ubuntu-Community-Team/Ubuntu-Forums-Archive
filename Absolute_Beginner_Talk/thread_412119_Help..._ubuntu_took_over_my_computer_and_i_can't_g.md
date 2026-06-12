---
title: "Help... ubuntu took over my computer and i can't get it off"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2007-04-17
I installed ubuntu on this computer... at first the keyboard didn't work at all.. so i couldn't select any options. but then it defaulted to install.. so i managed to get it working from there 

(im using a usb keyboard)

however after the install there are two main problems: my usb mouse no longer works . it did at first but doesnt any more. I unplugged it and tried changing the usb around to different ports.. and restarting the computer etc... but the mouse just plainly does not work. The keyboard does however and here is the kicker:

whatever process it is that linux starts through grub it somehow disables the keyboard. i know my bios works with usb keyboards because before grub or linux starts loading.. i can access the setup menu for my bios with it... but as soon as linux starts loading.. it stops working.. until it brings me up to the gdm login screen.

the other main problem is that the usb wireless card does not work automatically (its a ralink) even though i know i can get it to work... the computer will not be updatable because as soon as the kernel is updated the manually installed drivers will break etc.

So i decided to install windows in it. but it WONT LET ME. i tried changing all the boot devices to cd rom and leaving no other options. the problem is that grub starts loading first somehow.. and says to press any key to boot from the cd. the problem is that at that point the keyboard is the DISABLED.

i have tried 3 different windows CD's and none will boot. they all wait for the key to be pressed.

"miraculously" the ubuntu cd will boot to install mode.. which gives me access to a live cd.

I thought i could fix all this by simply erasing /boot and sudo rm -r / . I tried to erase linux completely from the hard drive but somehow it is still installed on the MBR so i guess it keeps interrupting when i try to boot from a windows cd.

THIS IS REALLY ANNOYING.

what i need to know is what command should i use from a tty terminal from the live cd , to erase the MBR so i can freaking boot up the windows CD. 

unfortunatley i don't have a ps2 keyboard. i have a usb to ps2 adaptor but it is colored green.. and doesn't want to work with the keyboard. UGH

THANKS

---

### Post by loserboy on 2007-04-17
there should be an option in BIOS that lets you computer treat your USB keyboard as a PS/2
i think its called legacy usb or something, maybe just try enabling that

also the color of the adapter shouldnt matter, all my adapters are green too.  you can borrow my keyboard if you want *throws keyboard*

---

### Post by jerryrw on 2007-04-17
That sounds like a bios issue.  That press any key to boot from cd....  promt is from the windows install cd boot sector.  Grub is not loaded at this point, after the timeout the xp cd bootloader passes control to grub.  And the color of the adapter makes no difference if the adapter is for a keyboard and not a mouse.

---

### Post by NoTiG on 2007-04-17
i just found out my mouse actually died.. somehow. it was working and then i unplugged it to plug it in a usb port in the front and it stopped working after.. i tried on 3 different computers. ugh. it wasnt even a year old and is the logitech g5 laser mouse.

if the boot from cd is coming from the cdrom itself then i guess i have to get a ps2 keyboard and there is no other option. there is no choice for legacy usb in the bios

---

### Post by locke.dragon on 2007-04-17
sorry, can't really help you with your problem.  ubuntu's on my machine for good (not stuck, i just want to keep it there).

---

### Post by Herman on 2007-04-18
Hello NoTiG, 
Here are links to illustrated how-tos for six different ways I know of to overwrite Grub's IPL in your MBR with an IPL for Windows NTLDR or at least some other bootloader, [Windows XP 'Recovery Console' method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console") |  [Windows 98 Floppy Disk Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method") | [Use  MbrFix.exe]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")  |   [Restore your MBR with a 'dd' command from a backup (if you made one)]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Restore_your_MBR_from_a_backup")  |     [Super Grub Disk can do it]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk") | [URL="http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager"]Or use GAG Boot Manager instead
[/URL]All of those work for most people's computers, just choose the one you think will be easiest. :D

Or leave Ubuntu and install Grub to Ubuntu's boot sector (as opposed to MBR), and install GAG Boot Manager to MBR instead.(Or just run it from a floppy disk). If you really think Grub is the culprit and you can boot with GAG Boot Manager without any trouble, that would help to indicate whether it's really grub that's your problem or something else.
If you still have mouse and / or keyboard problems after that, does you mouse and keyboard work again when you re-install the IPL for your Windows bootloader? Or not?

What kind of motherboard or BIOS have you got anyway, and hardware? I would like to know in case I can help someone else with the same problem again someday. And we can warn people what kind of hardware to steer clear of, too.  I have read one or two other complaints about grub and keyboards over the past few months, but so far no-one who seems to be willing to come forward with any useful details that might help others. One poster claimed to have had keyboard drivers installed in the MBR that was overwritten by grub. Thanks for at least sharing what kind of mouse it is/was. This is the first time I've ever heard of grub affecting a mouse in any way.

Regards, Herman :D

---

### Post by loserboy on 2007-04-18
heh, I haven't tried this but in your booting order maybe you could put cdrom first and just turn off all the other ones, maybe it would force a boot from cdrom, I havent played in bios in a while (which i'm happy about)

---

### Post by Herman on 2007-04-18
Well there is a grub command, [13.2.13 setkey]("http://www.gnu.org/software/grub/manual/grub.html#setkey") but I have never needed to try it out myself or heard of anyone else needing it. 
Some of these grub commands that no-one ever seems to use turn out to be really good once they are given a try and played with until we discover what they can do.
> Command: **setkey** [to_key from_key]
Change the keyboard map. The key from_key is mapped to the key to_key. If no argument is specified, reset key mappings.No guarantee it'll help, but it might be worth a try. It's just an idea.
Sometimes I kind of wish it was me who had the problem so I could have the fun of trying to solve it. I guess I'm a bit weird eh? 
Regards, Herman :D

---

