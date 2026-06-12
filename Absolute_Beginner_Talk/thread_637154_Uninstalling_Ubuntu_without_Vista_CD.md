---
title: "Uninstalling Ubuntu without Vista CD"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by mrg714 on 2007-12-10
Hi everyone,

I am in a particularly sticky situation. For reasons I wish were not the reality, I cannot use Ubuntu on my computer. I had set up Vista and Ubuntu to run on a dual boot and had 2 partitions set up. In my negligence I thought that deleted the partition was the way to get rid of Ubuntu. 

Then, like a bad monster movie, it sprang up with one gasp for air. I now cannot boot up vista because of GRUB (error 22). Unfortunately, I do not have the Vista DVD to boot up vista with nor do I know anyone who does. 

I tried using the Super GRUB disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) which was recommended in other posts and it did not work. (unless I burned the cd incorrectly...do you just burn it like any other data cd?). I tried loading it the boot menu but it went back to the same Error 22. 

If anyone has any ideas from here I'd really appreciate it. I'm in a deadline right now for work and desperately need my computer back and running. 

Wish I could keep Ubuntu,
Mark

PS It was not my decision that I could not have Ubuntu. Considering I didn't buy the computer I guess I'll listen...for now.

---

### Post by overdrank on 2007-12-10
> **mrg714 said:**
> Hi everyone,

I am in a particularly sticky situation. For reasons I wish were not the reality, I cannot use Ubuntu on my computer. I had set up Vista and Ubuntu to run on a dual boot and had 2 partitions set up. In my negligence I thought that deleted the partition was the way to get rid of Ubuntu. 

Then, like a bad monster movie, it sprang up with one gasp for air. I now cannot boot up vista because of GRUB (error 22). Unfortunately, I do not have the Vista DVD to boot up vista with nor do I know anyone who does. 

I tried using the Super GRUB disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) which was recommended in other posts and it did not work. (unless I burned the cd incorrectly...do you just burn it like any other data cd?). I tried loading it the boot menu but it went back to the same Error 22. 

If anyone has any ideas from here I'd really appreciate it. I'm in a deadline right now for work and desperately need my computer back and running. 

Wish I could keep Ubuntu,
Mark

PS It was not my decision that I could not have Ubuntu. Considering I didn't buy the computer I guess I'll listen...for now.

Hi and maybe you can find some useful info here
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!

---

### Post by forestpixie on 2007-12-10
> do you just burn it like any other data cd?
No you got to burn it as an iso - so you can boot with it

---

### Post by mrg714 on 2007-12-10
> **forestpixie said:**
> No you got to burn it as an iso - so you can boot with it


I reburned the CD with the extracted ISO file and it still does not work. 

Not sure what is going on here. I'll try some of the other ideas on the website above.

---

### Post by mrg714 on 2007-12-10
So nothing was working for some reason, I tried a few different boot solutions suggested. I just figured the easiest way at this point to fix the problem was to install Ubuntu once again (I had deleted Ubuntu's partition in Vista before this whole mess started which caused the GRUB lock up on my MBR). 

So, what is the easiest way to uninstall Ubuntu now that I have access to Vista? Note: I do not have the Vista DVD. 

I've been told that doing the following is what you do
Command prompt:  bootrec.exe/FixMbr 
Then, delete partitions

But when I try typing the command into the Vista command prompt it looks like this:
C:\Users\NAME>bootrec.exe/fixmbr
'bootrec.exe' is not recognized as an internal or external command, operable program or batch file. 


What should I do? Is there a process to get out of the C: on the command prompt? I have a feeling thats what it is.


I'm so sorry everyone, I'm a real n00b. 


Thanks!

Mark

---

### Post by forestpixie on 2007-12-11
> I reburned the CD with the extracted ISO file and it still does not work

You don't extract anything - burn the file you downloaded as an iso - just like you you did when you burned the ubuntu livecd

---

### Post by chips24 on 2007-12-11
i had the same sityation with freespire/vista

---

### Post by mc4man on 2007-12-11
There is no recovery console in vista, the repair tools are on the dvd. Some people have had success in restoring mbr without the dvd
reading
[http://www.daniweb.com/forums/showthread.php?t=95308&page=2&highlight=restore+mbr+in+vista+without+dvd](http://www.daniweb.com/forums/showthread.php?t=95308&page=2&highlight=restore+mbr+in+vista+without+dvd)
[http://vistasupport.mvps.org/vista_faq.htm](http://vistasupport.mvps.org/vista_faq.htm)
[http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

I would for future use call your pc manufacturer, tell em your hdd died, and request an image disk or whatever

---

### Post by billgoldberg on 2007-12-11
Yeah, super grub disk will work to restore your vista mbr.

As someone else said, you don't need to extract anything! And you don't burn it as a data cd.

Most modern burning software has a "iso" or "image" option to burn.

Use that, reboot your pc (make sure bios is set to boot from cd first), navigate the windows menu in super grub disk, and repair your mbr.

---

### Post by strydermed on 2008-07-19
If you are stuck in a dual boot with Ubuntu/Vista or triple boot with Ubuntu/Vista/XP and want to remove Linux without affecting XP and /or Vista , there are many options..
If u have a Vista DVD, just boot off it and use the recovery console. Type *bootrec /fixmbr*
That's it you are done. If you don't have Vista DVD, then there are a few options. 
If you have deleted your Ubuntu partition from Windows you might that your system refuses to boot. Download Super Grub Disk and burn it to a cdrom, you can restore Windows after booting from that. 

ps: VistaBootPro does not work in this situation, but you can use it to do lots of other cool stuff.
If you can boot into Vista then, there is a easy way. Just follow the steps below:
1. Download MBRFIX.EXE from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) 
2. Put it in your C or D drive. It does not matter where. Now right click on it and select security tab. Make it "Run as Administrator"
3. Type cmd in vista search box in start menu and right click it and select run Run as Administrator. 
4. In the command prompt go the directory where u have MBRFIX and now type *MbrFix /drive [COLOR="DarkOrange"]0[/COLOR] fixmbr /vista /yes* . This wont work without administrator permissions. Replace 0 with the number of ur drive. Just leave it if u have only one hard disk
That's it reboot and Vista boot manager will be back in  place of Grub. Now you can go into Disk manager and format Linux partitions and reclaim the space

---

