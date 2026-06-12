---
title: "First Install"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by BelaR on 2006-12-22
Hello and HELP!
I want to quit Windows and therefore I wanted to experiment with Linux on my old computer. I downloaded the Ubuntu and Kubuntu Live CDs. Running both I had my first problem: The monitor got crazy, and showed only stripes – "overrange" as it told me. It took me two days to find out that when I turn off the monitor while "installing" the Live CDs the monitor – for what reason ever - will work. Gnome/Ubuntu was more sympathetic too me than KDE/Kubuntu. But I wanted to see both in live action, so I experimented.

Installing both programmes separately and one after the other resulted in both cases in a "GRUB error" (I think 17). It took me another three days to find out that I will need the LILO bootloader for my (seven years old) computer. So I downloaded the alternate CDs for Ubuntu and Kubuntu. I chose the expert mode, answered all questions…

IN Kubuntu in the installation I never was asked to give a User-ID, when the system booted everything was fine – only I was asked to enter my User-ID and my password – an I obviously failed to get into the system.

In Ubuntu the installation process asked me to enter a User-ID, only when the system booted I had the stripes on my monitor again – so I could not do anything.

In Live CD, monitor turned off, the system switches to 61 Hz. Graphic card is ATI Range 128. Monitor a no-name flat-screen.

So this is Linux in my first experience – I have to admit that I am a beginner regarding Linux. Though I am a user and writer, I am not stupid regarding computers, in Windows I sometimes even went into the registry and so on, but Linux seems too complicated to me – I just want to produce texts with my computer, mail and use the internet…

And what is OEM-mode?

Buelent

---

### Post by jvc26 on 2006-12-22
Hi there, well first of all, you've probably come to the right place to answer a lot of your questions, and welcome to the forum - dont give up yet! Like any OS, learning Linux takes time (and although it sounds like you havent had much luck so far) will take you some time to get your head round - like i should think windows took when you first used that and to adapt from the windows way of doing things to that of linux will take some time.

In answer to your questions, i would ask you a couple of others - what are your system specs - as this may well have a major influence on why things arent working - RAM being too little for example. And the second is there much beyond the things you've stated you want to be able to do with your computer that you want to do - as linux has the capacity for all the mentioned things.

Anyway, hope we can all be of service :),
Il

---

### Post by Antarctica on 2006-12-22
I'm so glad that you want to quit using Windows.  Welcome to my world.  First of all I recommend you install Ubuntu instead of Kubuntu if you have a low processor speed and a small amount of RAM.  For example, I have a six year old Pentium II 350 MHz processor with 320 MB SDRAM (the old type).  Also, I have seen more support for Ubuntu than Kubuntu although the only difference is the desktop environment (GNOME vs. KDE).  Next, your monitor problem, overrange, is happening because your graphics card is using a frequency that your monitor cannot display.  You may choose another monitor, choose a different frequency and resolution, or try choosing another graphics driver.

Next, about your bootloader, you must have a really old motherboard to have to use LILO instead of GRUB.  Okay, about the LiveCDs now.  Go pop Ubuntu 6.10 (Edgy Eft) into your newer computer (if you have one).  It won't affect your current operating system unless you tell it to do so (which requires some work).  If you do choose to use Ubuntu, download and burn the Alternate Install CD and install Ubuntu in text mode.  Your graphics shouldn't be affected like in graphical mode.  In the installation, you are required to setup an account.  You must give yourself a username, a password, and a computer name (whatever you want).  You asked what OEM mode is.  OEM stands for Original Equipment Manufacturer.  If you were a computer vendor and chose to distribute Ubuntu with your new computers, you would choose OEM mode so that your users can setup their own username, password, and computer name.  I hope that I can be of any more assistance.  PM, email me, or IM me on AIM or MSN if you need any other help!

---

### Post by rccharles on 2006-12-23
> **BelaR said:**
> Hello and HELP!
 It took me another three days to find out that I will need the LILO bootloader for my (seven years old) computer. So I downloaded the alternate CDs for Ubuntu and Kubuntu. I chose the expert mode, answered all questions…



I found the expert mode a bit overwhelming.  Try the easy install (not exactly sure of name).

---

### Post by BelaR on 2006-12-23
Thanks - your are right one tends to forget all the sorrows with Windows

---

### Post by Albi on 2006-12-23
Okay, when it goes to the stripy screen, press alt+f2 and do the following:

you have to do sudo dpkg-reconfigure xserver-xorg once it works.  After you finish the part about the keyboard and driver (driver should be ati, if its not leave it default and see what happens), then it asks you what modes you want xserver to use, and now just choose ones that you're SURE your monitor will display.  next, go to medium when it autodetects your monitor to choose your default resolution, and that's it.  Now restart your computer.

Also, don't install in OEM mode.  I'm not sure exactly what it does, but yeah it doesn't ask you for a username.

I would go with regular ubuntu for now, but since your computer is slow, I would switch to Xubuntu once you get more comfortable with

---

### Post by BelaR on 2006-12-23
> **Antarctica said:**
> I'm so glad that you want to quit using Windows.  Welcome to my world.  First of all I recommend you install Ubuntu instead of Kubuntu if you have a low processor speed and a small amount of RAM.  For example, I have a six year old Pentium II 350 MHz processor with 320 MB SDRAM (the old type).  Also, I have seen more support for Ubuntu than Kubuntu although the only difference is the desktop environment (GNOME vs. KDE).  Next, your monitor problem, overrange, is happening because your graphics card is using a frequency that your monitor cannot display.  You may choose another monitor, choose a different frequency and resolution, or try choosing another graphics driver.

Next, about your bootloader, you must have a really old motherboard to have to use LILO instead of GRUB.  Okay, about the LiveCDs now.  Go pop Ubuntu 6.10 (Edgy Eft) into your newer computer (if you have one).  It won't affect your current operating system unless you tell it to do so (which requires some work).  If you do choose to use Ubuntu, download and burn the Alternate Install CD and install Ubuntu in text mode.  Your graphics shouldn't be affected like in graphical mode.  In the installation, you are required to setup an account.  You must give yourself a username, a password, and a computer name (whatever you want).  You asked what OEM mode is.  OEM stands for Original Equipment Manufacturer.  If you were a computer vendor and chose to distribute Ubuntu with your new computers, you would choose OEM mode so that your users can setup their own username, password, and computer name.  I hope that I can be of any more assistance.  PM, email me, or IM me on AIM or MSN if you need any other help!


THX for your answer. I think I have rather aged motherboard, but I wanted to experiment with LINUX before installing – and I did and do not want a "mixed" system – and LILO is the least problem. Now I managed to install Kubuntu, and I did not have any problems with the monitor, graphic card and overrange. I got into the system – yet, the audio card is not functioning now – and everything what goes with the CD. The good news: I managed to deinstall the English Open Office package and to install the German ones, and I managed to install Skype. I did not succeed in installing Firefox and Thunderbird, yet. USB-sticks do not work (which will a problem later), printer does.

But I would prefer Ubuntu – installing the alternate disk leads to the monitor/graphic card overrange problem, but while seeing only stripes or a collapsing entry window, I clearly can hear a sound. So Ubuntu configures the audio card correctly. Installing the Live CD and turning the monitor off while running leads to a functioning Ubuntu, now I will try installing Kubuntu from the Live CD and see about the results.

Installing Ubuntu in text-mode? Fine, just what do I do then – I am not really familiar with the console… and installing Ubuntu alternate leads to defunct image – so I cannot change the monitor, the graphics card or the resolution. How I can at least try to change these?

Thanks for help – I do not want to annoy you… I know, the easiest way would be to buy a new computer…

---

### Post by andguent on 2006-12-23
I would second the idea of checking out Xubuntu.org for a lighter weight version of Ubuntu for an older computer. Also, just want to make sure you are aware of [http://www.ubuntuusers.de/](http://www.ubuntuusers.de/) if German is your primary language. You of course are very welcome on this forum too!

I have found that Ubuntu has a great success rate with the dozen computers I have installed it on. Most are 1 year to 4 years old. If hardware is your problem, your newer computer will probably be easier to get working once you learn on your old system.

Option: If you are comfortable working with internal hardware, I would highly recommend picking up a new hard drive and installing it in your new computer IN PLACE of the hard drive with Windows on it. You can keep your Windows exactly as is and let it sit on your shelf. If Ubuntu or another form of Linux don't do it for you, you can always swap the drive back and be exactly where you were.

Option 2: If you get everything working on the new PC, one piece of software to be aware of is VMware server (vmware.com). The server is free, you install it, and then you can install Windows inside a program. That will allow you to run basic windows applications without problem. Heavy duty games with 3d acceleration is slightly more complicated....

---

### Post by BelaR on 2006-12-23
Hello,
thx for your active help.  Have written to the German users, too – but did not get so much helpful answers than here. So I stick here – unfortunately for you. To be honest I am aboz to give up – do not want to start with Xubuntu (guess there I do not get Gnome or KDE etc…), I rather get a new motherboard. I am disappointed somewhat because I really do not come into really getting involved with Linux, rather feel like a computer scientist.

"Okay, when it goes to the stripy screen, press alt+f2 and do the following:

you have to do sudo dpkg-reconfigure xserver-xorg once it works. After you finish the part about the keyboard and driver (driver should be ati, if its not leave it default and see what happens), then it asks you what modes you want xserver to use, and now just choose ones that you're SURE your monitor will display. next, go to medium when it autodetects your monitor to choose your default resolution, and that's it. Now restart your computer…"

Now here I get a red table, under it, its says "boot:" - entering here the command "sudo…." it says "No such list, entering Tab shows a list". Whatever that means.

I installed K/Ubuntu now more than thirty times.
Ubuntu Live CD – switching the monitor off – produces a Live program, where the sound is working, CD too, USB no, Kubuntu Live CD – switching the monitor off while installing – produces a Live program with no sound, and nothing working in connection with the CD Rom, no sound, Kubuntu Alternate the same, Ubuntu Alternate produces stripes – if Ubuntu und Kubuntu differ only regarding Gnome and KDE, why does one program recognize the graphic card/monitor the other not? Kubuntu also installs KPPP for my modem (this is an old computer), Gnome does not, and I would not know how to connect to the internet

But thanks - I am just afraid of investing in a new computer without being familiar with Ubuntu and then I have a Windows system again

---

### Post by BelaR on 2006-12-23
Now I tried the rescue system, producing a shell I entered
"sudo dpkg-reconfigure xserver-xorg"

and got the answer:

"Unknown terminal: bterm
check the TERM enviroment variable.
Also make sure the that the terminal is defined in the terminfo database
Alternatively set the Termcap environment variable to the desired termcap entry
Debconf: whiptail output to the above errors, giving up (remark: Hahaha!)"

By the way I am a historian, writing texts…. And I really do not think I am absolutely stupid with computers

Merry Christmas

---

### Post by BelaR on 2006-12-23
Another thing: Installing Kubuntu from the alternate CD leads to a stop at point "Choose software and install it" at around 6% - and I am asked to configure xserver.xorg setting in to the highest resolution I am sure it works with – Ubuntu install does NOT stop here – which ultimately leads to the stripes I guess. In Kubuntu you can afterwards easily adapt to your graphic cards (ATI Rage Tvout) and a Plug and Play screen – works perfectly. When the difference between Kubuntu und Ubuntu is only Gnome and KDE why do they install differently in such a vital point – at least regarding my case?

IN Kubuntu though the CD Rom does not work, modem is not recognized, and USB-stick neither. (in Windows both worked properly).

Question: Why is it recommended for beginners not to make /home-partition?

Addition: Installin Kubuntu another time, Kubuntu also did not ask for resolution – can it be that when xserver.org was configured I had my monitor turned off, so it could not "communicate" and asked me for precisioning – this is crazy that an installation reacts differently all the time. There is a point when it says "installed xresprobe" this must have to do with resolution. Crazy…  soon there will be a complete surrender

---

### Post by Sef on 2006-12-23
> Question: Why is it recommended for beginners not to make /home-partition?

Probably because it involves manually partitioning the hard drive.  If you regularly back up your fines, you really don't need a home partition.

---

