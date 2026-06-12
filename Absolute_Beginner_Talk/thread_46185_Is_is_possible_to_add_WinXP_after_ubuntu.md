---
title: "Is is possible to add WinXP after ubuntu?"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by H_Roark on 2005-07-03
I have ubuntu installed, but am considering adding WinXP and making the system dual-boot.  My question is whether I can do this with Ubuntu already on the machine, or if I have to uninstall Linux, add windows, and then re-install Linux.
Thanks in advance.

---

### Post by manicka on 2005-07-03
Yes it's possible but you'd have to reinstall grub afterwards as XP will overwrite the MBR. There are several ways to do this. I believe that it can be done using the ubuntu install CD but am unsure of the exact procedure.

---

### Post by Vorian on 2005-07-03
[QUOTE=H_Roark]I have ubuntu installed, but am considering adding WinXP and making the system dual-boot.  My question is whether I can do this with Ubuntu already on the machine, or if I have to uninstall Linux, add windows, and then re-install Linux.
Thanks in advance.[/QUOTE]

See this howto in tips&tricks

[Click Here!](http://www.ubuntuforums.org/showthread.php?t=39513&highlight=install+windows) 

Good Luck!

---

### Post by sapo on 2005-07-03
[QUOTE=manicka]Yes it's possible but you'd have to reinstall grub afterwards as XP will overwrite the MBR. There are several ways to do this. I believe that it can be done using the ubuntu install CD but am unsure of the exact procedure.[/QUOTE]


typing rescue in the boot screen when inserting the ubuntu install cd i think... but F1 will show the options

---

### Post by H_Roark on 2005-07-03
Will I need to make a separate partition for Windows?

---

### Post by sapo on 2005-07-03
[QUOTE=H_Roark]Will I need to make a separate partition for Windows?[/QUOTE]

sure  :grin:

---

### Post by Vorian on 2005-07-03
[QUOTE=H_Roark]Will I need to make a separate partition for Windows?[/QUOTE]

Only if you want a dual boot.  If you want to dual boot, when you re-install windows, the install will walk you through partitioning the disk.

I have portioned ubuntu with mandriva 50/50.  I installed mandriva post ubuntu install.

follow the how to if you want to run windows in ubuntu.  i love the irony of running windows inside of linux. \\:D/

---

### Post by H_Roark on 2005-07-04
Thanks for the info.  I read the howto, and although it's interesting, it strikes me as a bit complex, and I don't think it will accomplish what I want.  Simply, I'm trying to allow myself to use some features of windows(Specifically, the ability to print-I've got a newer Canon and from what I can tell, making it work with Linux is not an option).  I don't want to feed the best and go back to MS, but until some issues are worked out in Ubuntu, I suspect I'll need XP from time to time.

So, what I'm trying to do is this: create a dual-boot system with the full versions of each OS.  I know that one option here is to remove Ubuntu, install windows, find a partition program to run under windows, partition the disk, etc...etc...  But I would prefer to just dump MS on top of Ubuntu.  I was hoping there would be  a step-by-step guide somewhere, but if there is I havn't found it.

At any rate, thanks again for the advice.

---

### Post by knewbix on 2005-07-04
Hiya. Not sure I understand your posts correctly and I have no experience of resizing partitions etc, but I've read a lot and have friends who've tried stuff. Hopefully this gets conversation started if nothing else.

First of all, back up every single important file you have! That is the main thing to do before any of this! Then you use qtparted to resize/create the partitions you need. I think you have to apt-get this but it came with all the other distros I have more experience with, plus I use Kubuntu which doesn't help matters. And I haven't even got to the bit about me being a total n00b yet! Well, that's about it really. Something you should ask yourself is "do I have anything *that* important that I can't just wipe the whole drive?" In my case, I would just backup important stuff and wipe the whole thing and start from scratch, but I realise that doesn't help you much.

---

### Post by aysiu on 2005-07-04
[QUOTE=H_Roark]Thanks for the info.  I read the howto, and although it's interesting, it strikes me as a bit complex, and I don't think it will accomplish what I want.[/QUOTE] Mepis and Knoppix (both live CDs that can also install) have QTParted built into them. It's important that you use QTParted from a live CD to partition your hard drive, as otherwise your hard drive will be in use and won't be able to partition itself. After that, you can reinstall Windows on the first partition and Ubuntu on the second partition. Actually, make three partitions:

1. NTFS
2. EXT3
3. swap (you can read more about what swap is [here](http://itinfo.mit.edu/answer.php?id=7226))

Then, install Windows on the NTFS partition.
Then, install Ubuntu on the EXT3 partition. When asked if you want to install Grub on the MBR, say "yes."

You should be all set.

---

### Post by manicka on 2005-07-04
[QUOTE=H_Roark]
...  But I would prefer to just dump MS on top of Ubuntu.  I was hoping there would be  a step-by-step guide somewhere, but if there is I havn't found it.
[/QUOTE]

What you're asking here is impossible. Each OS has to live on it's own partition. I'd recommend percevering to have a go at partitioning your drive and setting up a dual boot. I've been doing it for years and it works really well.

Like many of us you'll find that you'll boot into windows less and less as time goes on with this setup. I'd wipe windows for good but I can't convince my partner and children to give it up. Dual boot is an ideal solution in this scenario.

You could also look into running vmware on top of linux to run windows when necessary, but it's a pricey solution

---

### Post by H_Roark on 2005-07-04
The live CD idea is a good one.  After some thought, though, I've decided to try to avoid putting WinXP back on the machine.  I realized that the only reason I can think of to have XP on there is to use the printer.  Since Open Office will work with MS docs(I think, havn't checked yet), there's no real reason to pollute my machine with Windows.  

Now, I just need to find a hack to make the IP1500 work.  That's turning out to be a challenge.  The alternative is to dig up my Epson C82, which, from what I understand, is supported by Linux.

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=H_Roark]The alternative is to dig up my Epson C82, which, from what I understand, is supported by Linux.[/QUOTE]

That sounds like a great solution to me. I use my 802.1b card because it works out of the box in Ubuntu (my broadcom 802.11g card hates Linux).

---

### Post by H_Roark on 2005-07-04
Well, I just tried TurboPrint on the Cannon, and was successful.  I'll have to pay to remove the watermark, but the price is about the same as replacing the cartridges on the Epson, without the risk of finding the print heads too fouled to use.  Also, giving money to Epson, even through cartridges, is something I'd rather avoid.  They rival Micro$loth in their tendecy to be evil.  So....all is well for now, and I'm keeping the machine Linux-only.  Now, if I can just get WMV files to play with sound... that's a minor concern at best, though.

Thanks again for everyone's help.  The community is one of the things that make the open-source movement so wonderful.

---

### Post by mohaham on 2005-07-04
here's howto restore GRUB after re-installing Windows
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by AndyWise on 2005-08-31
Hi 
My problem is a little diferent!
The  thing is .. I had WinXP and Ubuntu installed and all was working perfect .. but my Win crashed (go figure) .. so i tried to do the WinXP repair but here comes the problem (after restarting) .. i cant boot win from grub anymore .. there is no grub file in windows anymore so grub cant start win boot. 
I tried [How to restore GRUB menu after Windows installation?](http://amd64.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) but it didnt work .. 
I would like to try to disable GRUB but i cant (dont know how to) .. 

What else is there to do?
I dont want to delete Ubuntu!!
Please help

---

### Post by Steve1961 on 2005-09-05
Can you still start XP as normal or does Grub still load?  You may need to fix the mbr of windows first and then use the ubuntu cd to gain root access to your Ubuntu install to reinstall grub.  See the how to at the end of this thread for fixing the windows mbr:

[http://www.ubuntuforums.org/showthread.php?p=334463#post334463](http://www.ubuntuforums.org/showthread.php?p=334463#post334463)

Why do you want to get rid of grub?  You won't be able to dual boot without it.

---

