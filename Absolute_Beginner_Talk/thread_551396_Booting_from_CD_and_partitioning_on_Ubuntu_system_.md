---
title: "Booting from CD and partitioning on Ubuntu system? I need quick answer, please :("
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Ethernal X ) Victim on 2007-09-15
(Sorry for possible mistakes (i'm still learning english) and mad tone (i can't live without my PC working normally anymore :( )).

**History:** :neutral:

 1. I've got a nasty virus that morphed several times. Eventually, my antivirus couldn't neutralize it. Virus blocked (I think) all .exe files. Programs were unable to be started.
When I scanned my C:, D:, and E: partitions, all .exe files were found as virus' nests.
 2. I decided to clean out that ***** ** **** by reformatting all partitions (it seemed to be easiest way for me). I was afraid to use my WinXP CD so I wished to do that during installation of Ubuntu v 6.06 OS. **But** my brother installed Ub and formatted only C: partition (here I always install OS)(I suspect virus or it's tracks wasn't deleted in D: and E: partitions. 
 3. Ubuntu started but any programs, install/uninstall, drivers', codecs' setups  or games from WinXP still didn't started. It even can't open programs in any other CD. It displays messages: *Could not open '***'   The package might be corrupted or you are not allowed to open the file. check permissions of the file* with .exe files on computer, in CDs and even in Ub installation CD (original)! ](*,)
 
**So:**

 1) I wish to reformat all my partitions **but** i don't know how to start this setup in Ubuntu. It boots with from CD but differently than XP boot menu (In Ub it offers to select line (?kernel, ?memory test) and press 'b' to boot, 'e' to edit and :???: so I don't understand anything. In Ub I can't reformat manually. I downloaded QTParted tool for partitioning but it doesn't detect drives, and asks *Maybe you are not using root user?*.
2) Finally, I need to install WinXP again.

**Did** I make some kind of mistake? My PC is done? Or i still can repair everyting? I have no ultra important files, they all can be deleted if necessary. Please explain me clearly because in this situation I'm total noob.

**I will thank you forever and ever**.

---

### Post by Nikitas350 on 2007-09-15
In order to format all the disk and install the windows xp again you should boot from the windows xp installation cd, delete all the partitions and make the installation in a new clean partition. After that you can use the ubuntu installer in order to make the two partitions needed for the linux installation (on ext3 partition and one swap) and make the installation. If you dont want to install again the ubuntu linux you can use one program called "partition magic" under windows xp to divide the disk into partitions c: , d: and e:. Now, in order to make the ubuntu installation press enter when the screen you descrider appears. It will boot in a live cd mode and when it will finally boot press the icon install to start the installation. I don't know if i helped you ... good luck :)

---

### Post by Jussi01 on 2007-09-15
> **Ethernal X ) Victim said:**
> 
 3. Ubuntu started but any programs, install/uninstall, drivers', codecs' setups  or games from WinXP still didn't started. It even can't open programs in any other CD. It displays messages: *Could not open '***'   The package might be corrupted or you are not allowed to open the file. check permissions of the file* with .exe files on computer, in CDs and even in Ub installation CD (original)! ](*,)
 


You do realise that you cant run .exe files on an ubuntu pc? if you open synaptic from the "start" menu, you can install stuff from there...

---

### Post by Ethernal X ) Victim on 2007-09-15
It seems that Os ignores my both Win and Ub CDs. I have no idea what to do. when i press Esc (Space or Enter make nothing, Computer simply boots Ub OS), it shows that menu with:
 
  Ubuntu kernel2.6.15-23-386
  Ubuntu kernel2.6.15-23-386 (recovery mode)
  Ubuntu memtest86

What should i do?

---

### Post by init1 on 2007-09-15
> **Ethernal X ) Victim said:**
> It seems that Os ignores my both Win and Ub CDs. I have no idea what to do. when i press Esc (Space or Enter make nothing, Computer simply boots Ub OS), it shows that menu with:
 
  Ubuntu kernel2.6.15-23-386
  Ubuntu kernel2.6.15-23-386 (recovery mode)
  Ubuntu memtest86

What should i do?
Select the first one by using the arrow keys and enter.

---

### Post by Ethernal X ) Victim on 2007-09-15
And it simply boots Ub OS

**I need to launch install setups and do drive partitioning. But this not happens. I'm not a programmer.**

---

### Post by staticvoid on 2007-09-15
your bios might be set up funny. you need to chnge the boot order. also try burning another Ub cd and install in text mode. you can set up partitions that way and format stuff :]
yeah, ubunutu don't run .exe files. the only executable i can think of is is  .bin file :)

sv

---

### Post by Ethernal X ) Victim on 2007-09-15
Can i try making steps (formatting) till Ub OS installation with 64-bit pc version CD? CD i'm using is v 32-bit. My CPU 32-bit

---

### Post by Skidpad on 2007-09-15
> **Ethernal X ) Victim said:**
> And it simply boots Ub OS

**I need to launch install setups and do drive partitioning. But this not happens. I'm not a programmer.**
The Ubuntu cd is working correctly - the partitioning doesn't launch until you have booted to the live cd desktop and then double-clicked on the *Install* icon.

Do keep in mind that if you want to dual-boot XP & Ubuntu, it is easier to install XP first, and then Ubuntu.  See my sig for a link.

---

### Post by Ethernal X ) Victim on 2007-09-15
Ubuntu cant run start.exe file from it's CD.'staticvoid' wrote, that Ubuntu doesn run .exe files. What a hell? .exe setup for Ubuntu OS installation that cannot be launched again in this OS?

---

### Post by Skidpad on 2007-09-15
No, Ubuntu does not use .exe files, those are for Windows. 

A similar Linux file would be a .deb (Debian) file, meaning you can double-click/launch/install.

---

### Post by Ethernal X ) Victim on 2007-09-15
Those who think they are or they really are professionals,please read my first long post to realise situation because I'm stuck.

---

### Post by Skidpad on 2007-09-15
> **Ethernal X ) Victim said:**
> Those who think they are or they really are professionals,please read my first long post to realise situation because I'm stuck.
Excuse me?  I don't know which poster you are referring to in this otherwise ridiculous statement, but no matter who it was, please note:

* Everybody on here is a volunteer, this is a hobby, and we are all lucky to have it as a valuable resource.  Nobody is being paid for this; people help each other as they are able to within their own busy lives.  Be grateful.  Just because you "are stuck", does not necessarily raise the importance of the matter to those willing to help. 

* I don't believe I've ever seen anyone on here claiming to be a professional, but rather, as a whole, almost all are helpful individuals that are far and away better than paid "professional" help.

* As you have asked different questions throughout this thread, different responses have come up in an attempt to help you.  If you would so chose to not have this situation, don't ask additional questions or make statements not relevant to *your* original post.

*I applaud your attempt at the English language, but realize your posts may indeed be somewhat difficult to understand.  Give people a chance to decipher what exactly it is you are asking.  This may take multiple responses to the same question.

* Patience, courtesy,  and a willingness to listen are (some of the) keys to a successful "help" forum.  Demonstrate this, and you will in turn, be helped.  If not, your thread will die, or perhaps become locked - like a thread the other day containing a similar statement as the one you made above.

If you can understand all of this, lets get this thread back on topic and perhaps, get you "unstuck".

---

### Post by Nikitas350 on 2007-09-16
Ethernal X ) Victim, i think that you have formatted the entire disk and you have installed only the ubuntu. As i said before, you have to install first the windows xp. If you install the xp again, there will be no virus. But as i think all the documents you had on windows xp are lost. use this [http://www.theeldergeek.com/clean_installation_of_windows_xp.htm](http://www.theeldergeek.com/clean_installation_of_windows_xp.htm) to install windows xp. Now, i f you install windows xp the ubuntu will be deleted. So if you want to install ubuntu again you sould enter again the ubuntu cd and to install it again (be carefull with the preferences about the disk to use in ubuntu). If you have any question ask it.:) (An advice be more polite, don't speak like this in people who are trying to help you even if they are wrong....)

---

