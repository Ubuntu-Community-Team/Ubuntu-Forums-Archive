---
title: "Can I run OSX apps in Ubuntu?"
date: 2006-07-02
forum: Apple PPC Users
---

### Post by Commander South on 2006-07-02
If I have a mac mini, and put say ubuntu linux on it, have went from only being able to run mac apps to only being able to run ppc linux apps?  Or will, because of either the UNIX base or something I am unaware of altogether, be able to run my OSX apps in Ubunut(or any other PPC distro for that matter)?  Thanks for the help guys!

---

### Post by simonn on 2006-07-02
No. OSX and Linux are both flavours of unix, but they are not binary compatible.

Have a look at [http://www.maconlinux.org/](http://www.maconlinux.org/), probably not what you want, but may be of interest.

---

### Post by Ctrl+Alt+Del on 2006-07-02
you will not be able to run any of them. Gui Apps won't work for a variety of reasons. Cli Apps are mostlikely not going to work since their are linked against library versions you do not have on your linux.

edit: oops beaten by a second

---

### Post by Commander South on 2006-07-02
I am going to start browsing that site now.  I am a little familiar with virtualiztion, and when I hear epopple talking about Qemu and stuff they say it is really slow.  Does this run at near full speed given the software would run on this hardware anyway?

---

### Post by simonn on 2006-07-02
IME and IMHO, you are probably better off compiling any open source apps you want to run on OSX. Most will.

Have a google on darwin ports, fink etc.

You will need to install the X server and development tools from the OSX install DVDs.

---

### Post by onehotcutey on 2006-07-03
I run MOL, Mac On Linux, on my powerbook with and it runs very well, near full speed, but then I have a 512 megs of ram dedicated to it.

I can pretty much run what ever app I want to with it, though Linux doesn't support the mic on my PB so we I can't really test audio formats.

As for compiling OS apps on mac, it works, but it's not that great, because they are usually not native either and run through X11.

So really your just going to have to choose which one you want to run natively, OS X or OS.

---

### Post by calum on 2006-07-03
[QUOTE=Commander South]I am going to start browsing that site now.  I am a little familiar with virtualiztion, and when I hear epopple talking about Qemu and stuff they say it is really slow.  Does this run at near full speed given the software would run on this hardware anyway?[/QUOTE]

MacOnLinux runs pretty fast under Linux; about 80-90% of the speed of native OSX on my PowerBook G4 I would say.  Things like qemu are usually only "really slow" when they are emulating a different chipset.

However, hardware support with MOL is a bit limited; it supports networking, CD/DVD drives, printing, and some USB 1.0 devices, but not much else.  Overall, you wouldn't want to use it for games or multimedia apps, but it's just fine for most other things.

---

### Post by chasisaac on 2006-07-06
For older Apps:

BaliskII - stays at os9 and below.

---

### Post by barryhen on 2006-11-09
can you run mac-for linux on non-ppc hardware?  I have a macbook pro,  which I love having OSX on,  and I also have an hp nc8230 runnning ubuntu 6.10,  i was hoping to be able to run some osx apps somehow on it...any help would be appreciated...

---

### Post by ricanelite on 2006-11-10
Will Mac On Linux run on Edgy?

The reason being is that Ive always wanted to run MOL since my Mac machine right now has only Ubuntu because for some reason I cannot install OS X on my machine it says something is wrong with my Harddrive, but for 2 months now Ubuntu Linux has been running perfect.

Now I have upgraded to Edgy so I'm just wondering if MOL will be able to run on Edgy.

I'm new to Linux but as of now I'm really enjoying it and loving the experience of it.

Also is there any applications out there that I could run a hard drive test to see if there is anything wrong with my hard drive. Because on the MAC OS X Install of the operating system I get a error message which I cannot repair or fix.

So I was wondering if it could be me Install CDS. because now I have Ubuntu Linux install and I have not had any problems with my hard drive and so far now error messages I see.

If there is any Hard drive testers out there please let me know, Thank you so much!

You all have a great Friday!

---

### Post by linear on 2006-11-10
> **barryhen said:**
> can you run mac-for linux on non-ppc hardware?

No, it requires a PPC processor. :(

---

### Post by chadeusmaximus on 2006-11-12
> **ricanelite said:**
> Will Mac On Linux run on Edgy?

The reason being is that Ive always wanted to run MOL since my Mac machine right now has only Ubuntu because for some reason I cannot install OS X on my machine it says something is wrong with my Harddrive, but for 2 months now Ubuntu Linux has been running perfect.

Now I have upgraded to Edgy so I'm just wondering if MOL will be able to run on Edgy.

I'm new to Linux but as of now I'm really enjoying it and loving the experience of it.

Also is there any applications out there that I could run a hard drive test to see if there is anything wrong with my hard drive. Because on the MAC OS X Install of the operating system I get a error message which I cannot repair or fix.

So I was wondering if it could be me Install CDS. because now I have Ubuntu Linux install and I have not had any problems with my hard drive and so far now error messages I see.

If there is any Hard drive testers out there please let me know, Thank you so much!

You all have a great Friday!
I had a similiar experience with my 1.5ghz pc laptop when i attempted a clean install of dapper (6.06)).  For some reason it refused to let me boot back into windows, and then it refused to let me erase the hard drive.  End result being that my hard drive crashed, and the computer refused to boot up.  Sent it back to the manufacturer, and they replaced the hard drive, and everything works.  

have you tried booting up from your mac os CDs.  Restart, hold the "C" Key.  Then select Disk tools from the menu.  Not sure exactly which menu, but its there on the 1st screen. (haven't had access to a computer for 2 yeears.  My skillz are getting rusty.)

Once in disk tools, you should be able to select your Hard drive, and then verify/repair it.  I'm thinking that maybe your boot sector is messed up.  not sure how to fix that.  Do macs use grub? 

Make sure you back up your important data before you run the repair, because if you're not careful, you could destroy it.  

Also, reformatting the entire drive SHOULD fix any problems with the drive, and allow you to install a fresh copy of OS X on it.

---

### Post by AlphaMack on 2006-11-13
MOL does run in Edgy and runs quite well, although I found that the fullscreen key combo is a bit different (Ctrl+Opt+F9 on my PowerBook G4 instead of F8 ).  It's still Ctrl+Cmd+F7 to exit fullscreen.

Even with 1.25 GB of RAM on my system, I found that running MOL alongside Kubuntu is a disaster waiting to happen if you give MOL 512 MB RAM as KDE is very RAM hungry.  If you're going to use MOL, stick with Ubuntu (GNOME) or better yet Xubuntu (XFCE).  IMO of course.

---

### Post by barryhen on 2006-11-13
so Mac-on-Linux would not run on a Macbook Pro?  just PPC hw?  and would anyone know of any emulator or way to run any osx apps on Ubuntu?

Thanks again!!!

---

### Post by chadeusmaximus on 2008-04-18
You might need to reformat the hard drive to get it to install osX.  if its ext2, I don't think osX reads that out of the box, but I could be wrong...   I think it needs to be mac os extended , or something like that.  Not near a mac to look it up.

Chad

---

