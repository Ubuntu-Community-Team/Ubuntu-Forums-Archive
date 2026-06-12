---
title: "Gonna dual boot (mom needs windows back) and I need exact instructions"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-08-12
I need to know how to dual boot. I need windows back. Tell me either instructions or a link to a guide for it. Also I only have a 40gb hd and I only have under 20gb left. I am looking to make windows have 3gb only.

---

### Post by undertakingyou on 2007-08-12
here is a link to the wiki.  Hopefully it will help.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

cheers!

---

### Post by forestpixie on 2007-08-12
There's a good guide in psychocats as well - link in my sig

---

### Post by ~~Tito~~ on 2007-08-12
I deleted windows. . . . . So is there anyway to do this after the fact(3 months. . .)?

---

### Post by undertakingyou on 2007-08-12
yes, reinstall windows and start over according to the guide, or partition you drive and reinstall windows.  And after that is done us a Super Grub Disc to restore grub so that you can boot into both windows and ubuntu.

---

### Post by jvc26 on 2007-08-12
Just use your windows cd and follow the psychocats guide. You will (as mentioned above) need to use supergrub disk to let you dual boot as installing windows after ubuntu will overwrite grub.
Il

---

### Post by MindRiot on 2007-08-12
Yes, reinstall Windows.  You can do things two ways.  During windows setup, you can set the partition windows will be installed on to 3gbs.  Or, you can partition the whole drive for Windows, then run the windows disk defragmentation tool after setup is complete (once you boot into windows). Then, during the setup for Ubuntu, you can resize the windows partition. If you chose the second course, you need to make sure you turn off the page file in Windows before running the defragmentation tool,, since that file cannot be moved during the defragmention process, then turn it back on after you have install Ubuntu and booted back into Windows.

---

### Post by ~~Tito~~ on 2007-08-12
:o. I just want everything that is on ubuntu to stay(My personal stuff), and just have windows installed easily without the fear of deleting the whole partition of windows and just start fresh with windows in 3 gb.

---

### Post by bwtranch on 2007-08-12
Screw windoze. Just re-install Ubuntu. Don't be a puss. Windoze was your problem in the first place.

---

### Post by ~~Tito~~ on 2007-08-12
[SIZE="7"]**_*. . . . . . . .My mom needs it so I HAVE TO!!. *_**[/SIZE]

When I installed ubuntu I used the whole HD so I don't have any windows left just ubuntu.

This is how I want my hd:

[SIZE="5"]Ubuntu=37gb _**(staying the same and not deleting nothing)**_
Windows=4gb _**(Sacrificing gb's for windows and starting brand new)**_[/SIZE]
I decided to have 1 more gb to my windows part.

---

### Post by forestpixie on 2007-08-12
which version of windows are you actually intending to use?

At the moment how is you're hd setup, have you got a seperate /home partition or did you let Ubuntu do it's thing on it's own.

---

### Post by Lucifiel on 2007-08-12
Errr... I think Windows requires at least 5 to 6 gb for installation?

---

### Post by forestpixie on 2007-08-12
> **Lucifiel said:**
> Errr... I think Windows requires at least 5 to 6 gb for installation?

depends on the version doesn't it ?

and stop screaming Tito !

---

### Post by ~~Tito~~ on 2007-08-12
I just let ubuntu do Its magic so I am unclear. I am installing Windows Professional.
Sorry I just wanted to be clear to the other guy.

---

### Post by forestpixie on 2007-08-12
erm - which windows professional - 2k, xp, vista? Vista is obviously a monster and will never fit on 3 Gb, XP will prob fit not sure but min spec is 1.5Gb

If Ubuntu has the whole drive you will need to resize it - I'd use gparted to do the partitioning before you go to install windows you can get gparted livecd to boot with.

Make sure you back up your files first though

Aftyer you've installed windows you will need to sort grub out - windows will overwrite it - there are plenty of Grub threads on here - you could uses SuperGrub to do it

---

### Post by ~~Tito~~ on 2007-08-12
Xp. Crap that is the biggest problem right there. I cant back up, I dont have anything to use to backup. No cd's, memory cards/flash drives around me.

---

### Post by forestpixie on 2007-08-12
I think that could be a bit of a problem, but could be wrong. 

You should be able to resize the partition in the Ubuntu Livecd - I just prefer to do it seperately - but if it all goes horribly wrong without a backup you could be up the stream without a paddle :(

You need to make a partition for the XP install somehow. Have a search for resizing within the Ubuntu livecd - but I guess it all depends on how important your data is to you.

---

### Post by ~~Tito~~ on 2007-08-12
Somethings I can replace and somethings I cant. Its just that I have the system exactly how I want it, and I don't want to go through all hell(fun hell yay!!! ubuntu is fun to mess with but I don't like to repeat things that I forgot and took forever, was fun but it wont be fun the 2nd time) that I have been through.

---

### Post by Lucifiel on 2007-08-12
> **~~Tito~~ said:**
> Xp. Crap that is the biggest problem right there. I cant back up, I dont have anything to use to backup. No cd's, memory cards/flash drives around me.

How much free space do you currently have? Perhaps you could make an image and upload it to someone's ftp? :D Or make a .torrent file and ask your friends to help you download and then seed it when you come back. :D 


Lucifiel

---

### Post by Lucifiel on 2007-08-12
Oh and for Win XP Pro, here're the basic system requirements but if I were you, I'd add at least 2 to 3 gb to the disk "requirements".

[http://www.microsoft.com/windowsxp/pro/upgrading/sysreqs.mspx](http://www.microsoft.com/windowsxp/pro/upgrading/sysreqs.mspx)

Still, why don't you buy a new hard disk and get a cdwriter? They come cheap these days.

---

### Post by ~~Tito~~ on 2007-08-12
Moms are cheap these days too. She says that I cant get anything new because the computer was just fine before. I had Windows running perfectly but I wanted Ubuntu so pffrrrttttt helllo ubunu. I know a bunch of people are going to start ubuntu isn't for everyone but it is for me. just not my mom so I have to satisfy her. Wat. . .  MAYBE A VM!! But I don't want to buy because my mom.

---

### Post by MindRiot on 2007-08-12
As far as I'm aware, Windows XP must be installed to the first partition, so it looks like your screwed, unless you can somehow create a partition in front of your Ubuntu partitions. Unfortunately, I don't know how you could go about doing that.

Try as hard as you can to find a way to backup your files. Even if you have to borrow a CD burner from a friend. Try to persuade your mother to buy a used 20 gig hard drive. You pick these up for $20 from a "mom and pop" computer shop.

---

### Post by ~~Tito~~ on 2007-08-12
Thanks, this sucks badly then. Is there anyway to do what he mentioned? If so that would be awesome if it wasn't dangerous!!!

---

### Post by hartdg on 2007-08-12
Tito,

Sounds like you have a political household problem as much as a technical problem.:)

**Technical Issues.**
**Back-up**
Regardless of what operating system/s you use, if you don't have the means to do back-ups you are living dangerously! Mindriot and Lucifiel gave several suggestions for creating a back-up. Another option is to network with a friend's PC and borrow some space. There are also some on-line servers that provide free space (but you need decent bandwidth if you are transferring gigabytes of files). 

**Planning Space for Win XP Pro**
Minimum specified by Microsoft is 1.5GB. 
I've seen Windows 98 & Windows 2000 function fairly happily in 2GB.
My Windows XP Pro installation uses 4.5GB (Windows directory, plus 3GB (Program Files), and then you need to leave some space for Documents and Settings and the windows swap file. My installation is bloated with several years of updates and many programs that your mother might not need...
If your mother has a large collection of videos, photos, music etc. then you will probably need to make more space available.
You could even try begging for a redundant hard drive (say 10GB) at your local computer store or on e-bay.

So first check what functionality and programs your mother needs / wants and confirm that your 4GB allocation is adequate.

**Before You Start**
At present you have a system that works. Once you start making changes there is a real risk that things will get broken and you will need to fix them!

*Plan for the things that can go wrong* (assume that they will!)

1. Make a back-up of your current installation (or accept the risk).
2. Get a copy of Ubuntu Live CD (test that it works!).
3. Make sure you know how to use gparted.
4. Check recent posts in this forum about people who have resized partitions and then found that Ubuntu will not boot from the hard disk. Make notes of the recommended fixes.
5. Get a copy of Super Grub (as recommended by Undertakingyou and others) and cut it to a bootable CD (see: [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) and [http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html) or Google "super grub disk download"). I've not used this program so I don't know how robust it is or how easy it is to use. I recommend that you read up about it in the forums and learn from other people's experience before relying on it.
6. Make sure you have the Windows XP Pro installation disk and a valid key code.

**Action**
1. Boot up off your Ubuntu Live CD (or equivalent) and use gpart to shrink your Linux partition and create a new partition. You want the new partition to be the _first_ partition.
2. Check & repair the installation of Linux on your hard disk (based on your research of problems experienced when resizing partitions). Get Ubuntu back as a bootable system.
3. Boot up on the Windows XP CD and tell it to install into the first partition (will probably need formatting first, unless you formatted with gparted).
4. Once Windows has been installed, you will probably find that you do not have an option of booting up into Ubuntu. Now is the time to boot up off the Super Grub CD and reinstate Grub as your boot loader.
5. Confirm that you can boot up into WinXP & Ubuntu

At this stage you're done, and hopefully you and your mother are happy!

**The Political Issues**
The alternative is to understand what your mother really wants / needs to do on the computer and see to what extent Ubuntu can / does meet her requirements. This may require a lot of time and patience on your part.

1. First ask her if she's willing to think about it. Possible "selling points" (a) is for this to be a shared project that you guys do together, (b) it can help you develop your listening and planning skills with her as your "customer".

2. Sit down with her and make a list of what she does on a computer (you will need this anyway for the windows installation to ensure the set-up is right).

3. Take her concerns seriously and treat them with respect. These might include not having any time to learn new stuff, being afraid of a new environment, not liking the "look & feel" of Ubuntu because she's used to Windows. There might be files (e-mails?) in Windows that she does not want to lose. There might be a specific program she needs to use (will it work in wine?..)

4. Do home work on each of her requirements and issues / concerns and how they might be addressed in Ubuntu. Are there any "killer apps" in Ubuntu that will really appeal to your mom?

5. Give her feedback on what you've found and get her input on it.

6. Put a plan together to get her up and running on Ubuntu and show how it will meet her needs... 

7. Get her agreement and commitment to help you implement the plan.

8. Go for it (at her pace)!

Even if you do not wish to follow this path, share your plan for reinstalling Win XP. Explain the steps and the risks of what you need to do. At the very least she will also have a better understanding of the process and your frustration if something goes off-track. You may even make her more receptive to the idea of a bigger hard disk... 

Good luck.

Dave

---

### Post by ~~Tito~~ on 2007-08-12
Wow wow. Thanks for the help. 
One thing if I could fix my printer again it would work out awesome and my mom wouldn't need windows.
Also I have what she needs just IE6 but It doesn't work the printer doesn't print pags of of mlx right again it was working for a bit but now it takes like 5 min per page :(!!!!

---

### Post by hartdg on 2007-08-12
> **~~Tito~~ said:**
> 
One thing if I could fix my printer again it would work out awesome and my mom wouldn't need windows.
Also I have what she needs just IE6 but It doesn't work the printer doesn't print pags of of mlx right again it was working for a bit but now it takes like 5 min per page :(!!!!

Tito,

I switched to Firefox from IE6 about 6 months ago (under Windows XP) and have found it works just as well as (some would say better than) IE6. What are the specific things that your mom is doing that don't work under Firefox?

I don't know what "mlx" is? Could you explain. Perhaps there is a specific problem that can be addressed. 

It might be best to post a new thread about your printer. You say that it used to work ok. Perhaps that can be fixed if the problem is described in more detail.

Is printing from IE6 the only thing in Ubuntu that's not working for your mom?

Dave

---

### Post by ~~Tito~~ on 2007-08-13
All is a problem in printing. MLX is a Realtor website that was designed so horribly and can only be used my internet explorer.

---

### Post by Lucifiel on 2007-08-13
> **~~Tito~~ said:**
> All is a problem in printing. MLX is a Realtor website that was designed so horribly and can only be used my internet explorer.

Maybe try "User Agent Switcher"? An extension in Firefox?

Edit: Still, I'd make a list of what your mother needs in Windows: programs, features, etc. And consider which would be more worthwhile: dual-booting or just having Ubuntu alone?

---

### Post by ~~Tito~~ on 2007-08-13
All she needs is(and I've known this since she started):
MLX website, Microsoft office like applications, working printer. Thats ubuntu fills 2/3rds of it so I need to fix printing and mlx and she will me set. Right now she borrowed one of her assistants (she gets leads and gets the money from the commission off the loan) laptops and it has all 3 so she is fine right now but when she doesn't have it it sucks so I want to fix this major problem.

---

### Post by Lucifiel on 2007-08-13
> **~~Tito~~ said:**
> All she needs is(and I've known this since she started):
MLX website, Microsoft office like applications, working printer. Thats ubuntu fills 2/3rds of it so I need to fix printing and mlx and she will me set. Right now she borrowed one of her assistants (she gets leads and gets the money from the commission off the loan) laptops and it has all 3 so she is fine right now but when she doesn't have it it sucks so I want to fix this major problem.

Printer? You mean the printer doesn't work in Ubuntu? 

And that the site doesn't load properly in Firefox? Try the Firefox extension I mentioned then. If that doesn't work, try this:

[http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html](http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html)

---

### Post by Arthur Archnix on 2007-08-13
> **~~Tito~~ said:**
> Moms are cheap these days too.

haha... zing!

Anyway, download and burn gparted to a cd, reboot and resize your ubuntu install. Free up the space at the start of the disc. Dependening on how much data you have, this could take hour to hours. I'm able to keep my XP install down to just under 4.6 gigs, but I only use office, spss, and antivirus. I have to remove pretty much everything non-essential, and delete all the cached updates, turn off system restore, etc...

So, give your poor hard-working mom and little breathing room and free up 5 gigs. You'll just have to sacrifice one or two of your brittany spears cd's I'm afraid. :wink:

I did this the other day, but I backed up my data first. No problems, but problems can happen.

---

### Post by nalinde on 2007-08-13
Hi ~~Tito~~  :-).... Ever given a thougth about a Virtual Machine?
When i design i have to boot up Windows > Photoshop and to dualboot every time is't the funniest thing to do so i had a look at virtual machines instead.
There are 3 mayor good programs that handle Virtual Machines:
**VMware** (player or server) Free as in beer (I use this)
**Qemu **(advanced, text based, but can run the OS faster)
**VirtualBox** (Qt )

Otherwise there is **[Ie for linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")**... but i guess you have to fix the printing thingy first then.

---

### Post by ~~Tito~~ on 2007-08-13
Yea, so VM ware isn't free I don't understand that (free as in beer?)??:confused:
Listen I'm 14 so I really don't know much about beer other than I like Bacardi with oj.

---

### Post by forestpixie on 2007-08-13
Tito - the virtual machines people are talking about are free, have a look on the forum (there is loads) and at the repective websites

[Virtualbox]("http://www.virtualbox.org/")

Vmware [player]("http://www.vmware.com/products/player/")

Vmware [server]("http://www.vmware.com/products/server/")

There's an Ubuntu how to on Qemu [here]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

But they do need to have sufficient memory to run properly.

But if people are going to help with the printer they really need to know what printer it is and the problems you're having.

I think you probably need to concentrate on the printer first - then your mum's IE need.

---

### Post by Lucifiel on 2007-08-13
Well, virtual machines are great for testing and running other operating systems but they require quite a lot of work to set up for linux newbies. 

If you want to give them a try, be prepared to spend many hours tinkering and finally, make sure to back up your Linux installation. This is because more than once, I broke Linux 'cos some of the VM tools borked Ubuntu. Once, I accidentally patched some critical part of Linux and on another time, the tools caused Ubuntu to slow down, etc. 

As it is, I actually would recommend you to learn more about Linux basics first before plunging into tinkering with virtual machines.

---

### Post by forestpixie on 2007-08-13
> **Lucifiel said:**
> ...As it is, I actually would recommend you to learn more about Linux basics first before plunging into tinkering with virtual machines.

 Yea totally agree, just trying to give him/her some info -seems to think he has to pay- I've only been doing this for a few months myself - couldn't get vbox to work - managed to get vmware to work but then it wouldn't print (which is all I wanted it to do ! ). Gave up and threw toys out of pram to be honest and waited till I got an HP printer and all was well .


I think his biggest problem here is getting the printer to work, then try and get IE working :)

---

### Post by Lucifiel on 2007-08-13
> **forestpixie said:**
> Yea totally agree, just trying to give him/her some info -seems to think he has to pay- I've only been doing this for a few months myself - couldn't get vbox to work - managed to get vmware to work but then it wouldn't print (which is all I wanted it to do ! ). Gave up and threw toys out of pram to be honest and waited till I got an HP printer and all was well .


I think his biggest problem here is getting the printer to work, then try and get IE working :)

Well, it took me a lot of work to get a virtual machine working on a previous Ubuntu installation. However, once I learnt how to do it, it was a lot easier. But I haven't done that in the past 2 months or so, due to various computer issues. Anyways, I might be trying that again when I switch to Linux-mint Xfce. <3

Well, setting up IE 6.0 should be easy if he reads the guide I pasted. After that, it's a matter of googling the issues and tracing the likely causes.

---

### Post by nalinde on 2007-08-13
"Yea, so VM ware isn't free I don't understand that (free as in beer?)??
Listen I'm 14 so I really don't know much about beer other than I like Bacardi with oj."

Haha, LOL :-) Well it's an [expression]("http://www.gnu.org/philosophy/free-sw.html"), among others, the great ICON [Richard Stallman]("http://en.wikipedia.org/wiki/Richard_Stallman") uses. Oops it should be "Free as in free beer" was kind of tired :-P

Anyways, running VMwares apps always worked good for me and i've never had any critical problems with it. But a tip, as a start i would try to install it trugh [Auomatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") for an start and olny handle vmware trugh automatix, that's the simplest way for you, i think.
Well Anyways, if you decide to give VMware a try and want help. PM me here on Ubuntuforums or maybe add me on an IM-client and i'll try to help you.

---

### Post by ~~Tito~~ on 2007-08-14
Gotcha ;). Your gonna get a MSN add user in a few sec's.

---

### Post by hartdg on 2007-08-16
> **Lucifiel said:**
> Maybe try "User Agent Switcher"? An extension in Firefox?


The User Agent Switcher" mentioned by Lucifiel can be found at:
[http://chrispederick.com/work/user-agent-switcher/](http://chrispederick.com/work/user-agent-switcher/)

What it does is let your Firefox installation pretend to be a different a different browser (it offers IE7, Netscape 4.8 and Opera 9.2 as alternatives). This is sometimes sufficient for web sites that are fussy about the browsers they support but will not work in all cases (if there are special scripts or add-ons embedded in the pages).

I have then tried to access [http://www.mlxchange.com/](http://www.mlxchange.com/)  (which looks like it might be the site your mom wants to use). With User Agent Switcher (see the Tools menu of Firefox once you've downloaded and installed it) to IE7 I can get past the front page but hitting the "GO" button results in an error message. 

If you can confirm the website that your mom users maybe one of the other forum members can offer more specific advice.

Dave

---

