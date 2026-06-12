---
title: "Absolute Newbie, HELP!!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by jgk0904 on 2007-03-13
OK, I have enough of Windows. I am ready to jump in.  Please help.

Heres my info.
I want Linux mostly for security reason when I surf the Web.
I still want to do my work in Word and Excel etc. under XP.
I do not game, do not download ( or work with ) song or video. 
I use my desktop for work and internet only.

My system info: 
Stand alone desktop, no network.
AMD Duron 1294 MHz
256 RAM
1 hard drive, 6 GB with 3 GB free space ( I know its very small, but for what I do, its enough ).
Internal dial up moderm.
Running XP professional.

Questions.

I want to have 1 GB space for future Windows documents and allocate 2 GB for ubuntu ( for surfing only ), is 2 GB enough for ubuntu, Firefox and dialup program?

Will ubuntu automatically config my moderm and set up driver ( or I need to download driver from the moderm company website )?

Do I need to call my ISP provider to send me a exe progame for the Linux envoirment?

Is it hard to set up a dual-boot?

Does dual-boot means I can choose which OS I want to use during boot.

What is CRUB? Will GRUB come with ubuntu in one package ( or I need to download GRUB separatly )?

Base on my download speed, is it better to ask ubuntu to send me a CD? is the CD free?

Is it hard to learn ubuntu? How can I get help to learn?

What is WINE, will WINE give me the interface similar to Windows ( so that I don't have to learn a new OS and start using Linus right away )? Is WINE free?

Are the common Linus freewares ( e.g. word processor, spreadsheet ) allow me to save the file as Windows verson? so that I can take the fils to work in office too.

What else do I need to know??

I know all these questions have asked many times before...Thanks in advance

---

### Post by LucasLinard on 2007-03-13
if you use dial-up internet you should ask for a ubuntu cd. It's free.

---

### Post by jem7v on 2007-03-13
1. 256 mb RAM will run Ubuntu, but not very quickly.
2. 2 gb for Ubuntu? That may not be enough.
3. Modem: If it's a hardware modem, it'll probably be okay, but if it's a winmodem you might Never get it to work.  Winmodems rarely have working Linux drivers.
4. You shouldn't have to phone your ISP for a special program to dial in with.  Also, Linux doesn't use the exe file format... that's pretty much just windows.
5. The installer sets up the dual boot. It's very easy.
6. GRUB is the boot-up manager that gets installed by default when you install Ubuntu. It's on the install disc.  It's what lets you choose whether to boot into XP or Ubuntu.
7. It will probably take you a long time to download the disc if you are on dial-up. It might be better to order a CD.  I think you basically pay for materials and shipping, so it might be a few dollars.
8. It's not very hard to learn to use Ubuntu for basic tasks like internet and word processing.  If you read the desktop guide [https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html) you'll know most of what you need, and if you have specific questions this forum and Google have most of the answers.  The menus are laid out very inuitively compared to Windows.
9. Wine is a program to let you install and run Windows software, but it doesn't work with every program.  It is generally easier to use the native Linux program than to struggle with Wine.
10. Ubuntu comes with the OpenOffice.org suite installed by default.  It is a near complete replacement for MS Office and can open more MS file formats than current versions of Office actually can.  Many Linux programs have excellent file compatibility with their Windows alternatives and almost everything is free. (It's usually called Open Source instead of Freeware, though.)

---

### Post by jgk0904 on 2007-03-13
I beleive its hardware moderm, it came with my Elite mother board....so I don't have to download driver, right??

From your explaination on Openoffice.org, I take it it can open Windows files, work with it, and save it in a Windows format so that I can open in MS Office later.

2 MG really not enough for ubuntu?? I don't intent to load any large program, all I need is ubuntu, openoffice and dial up.  And I will forget about Wine base on your recommandation.

---

### Post by jem7v on 2007-03-13
I would try the LiveCD first to see if you can get your modem working before you install.  There's still a good chance it's a winmodem... They have hardware too, eh? But they cost much less to manufacture, so you don't see full-fledged hardware modems any more. [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) talks about dialup modems in Ubuntu.

As for space, to quote [http://techheadaches.blogspot.com/2006/07/user-friendly-guide-to-installing.html](http://techheadaches.blogspot.com/2006/07/user-friendly-guide-to-installing.html) : "You'll need to allocate at least 3GB of space for your Ubuntu installation, but a more realistic minimum of 10GB should be allotted so that you have room to install additional applications."


And yes, you can do that with OpenOffice.

---

### Post by seshomaru samma on 2007-03-13
Your biggest obstacle will be configuring your dial -up modem. If it's a winmoden - forget it . Try to find out the model of your modem and use the search function of this forum to see if people have managed to use it with linux.
If you can sort out the modem problem , then your next step will be to download open-office for your Windows (its free , from [www.openoffice.org](www.openoffice.org) ), check it out and see if you can use that instead of Microsoft Office (you can try Abi word as well which is simpler and faster - [http://www.abisource.com/](http://www.abisource.com/)) if you can use one of them then there is really no reason to keep windows , is there ?

Another possibility , if you have only 2GB is to use Puppy Linux - it is superfast and easy to configure. It doesn't have many programmes but it has Open Office and Firefox. It is also a very small OS - about 60MB if I remember correctly so you can download it on a dial-up. It's the ideal OS for those who just want to surf the net and edit some word files and have a small harddisc. It's very fast - did I mentioned that?
Check it out - [here]("http://www.puppylinux.org/")

both Puppy and Ubuntu come as a live CD from which you can boot and experience the OS without the need to install it , you can use the live CD to see whether your modem works under Linux ( Ubuntu's live CD is a bit slow, Puppy is VERY fast)

---

### Post by milton1 on 2007-03-13
You will need at least 3 gb to install ubuntu. Probably more, to allow usable space on disk following the install. Remember, you are installing an entirely new operating system, not just a few new programs.

---

### Post by jem7v on 2007-03-13
If you decide to look for a lighter weight distro of Linux as seshomaru samma suggested, DSL-N might be another good choice.  It's also very easy to install/use, though it doesn't have OpenOffice installed by default like ChubbyPuppy does.  I think you can install .deb based programs in it, which makes it attractive.  Puppy is probably going to be prettier to start with than DSL-N though.

Then again, part of Ubuntu's ease of use is the Gnome desktop environment they default to.  Anything using the Fluxbox desktop environment (or similar) is going to be much more foreign feeling to a Windows user.

---

### Post by jgk0904 on 2007-03-13
You guys really have me concern about moderm driver.  I am a student with a part time job. I am paying $7 for my dial up and can not afford $30 a month for cable boardband.  
So if I can not use my moderm under Linux, I can not use Linus...I guess I am out of luck.  

As samma suggested, there is no reason to keep Windows....but I need at least photo shop, front page and all their files, I think I still keep Windows just for the peace of mind ( that is if I can over come the moderm driver issue ).

---

### Post by jem7v on 2007-03-13
You could still try to find out if your specific modem works or not. It might.  Alternatively, you could spend $40-50 on a real hardware modem and keep using dialup.

As for Photoshop and Frontpage? You could Probably install them in Wine, but they'll likely run better in Windows anyway.  I'd keep the Windows partition just in case you need it.

---

