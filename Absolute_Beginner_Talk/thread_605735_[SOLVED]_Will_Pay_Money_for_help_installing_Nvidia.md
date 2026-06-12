---
title: "[SOLVED] Will Pay Money for help installing Nvidia driver (in Australia)"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by barney66 on 2007-11-07
Hi all,

i have spent the last week reading an amazing collection of hints tips and tricks for installing the latests nvidia drivers into v7.10. there are those who say use the restricted driver manager, there are those who say d/l the driver and install via the terminal, there are those who say this and those who say that.... hmmm none of which seems to work and at best creates more problems. I would have thought (and i know now i am wrong) that one of the largest (if not the largest) video card manufacturer/supplier nVidia and the folks at Ubuntu could have come up with a way to install a simple video card driver so as to allow the graphical features of the OS to be used. It would appear that the folks at microsoft can do this with ease. If you live in Brisbane QLD Australia I am happy to pay cash money for someone to come and install a working driver for my nVidia 6800GS card as it is now totally beyond me. Alternatively does anyone know of a video card (make and model) that works with v7.10 that does not require the installation of a separate driver as I am more than happy to trash the nVidia crap that does not work with the OS and put something in that does.

regards,
barney66

---

### Post by Inxsible on 2007-11-07
I live way on the other side of the world to come and help you personally. But I have a Nvidia 7600 GeForce Go card and it worked out of the box after I enabled the restricted driver through the restricted driver manager.

6800 has also been successfully configured by many. 

Hopefully you will get help for it. :)

---

### Post by Inxsible on 2007-11-07
It seems this is your first post.....have you tried starting a thread detailing what your problem is.

I know you tried a bunch of guides, but maybe if you tell everyone what errors you get specifically, people could help you out (free of charge ;) )

---

### Post by MaDeX on 2007-11-07
Sir,

I feel your pain, my beloved 8800 GTS is going to waste - and dare I say this, i'm going back to Vista.

I have been unbuntu for around 15 hours now, and going back.... 

I loved the look and feel of this OS however its not something the average windows "fanboy" can use. Trust me, if choices was there I would choose this over anything mr bill gates threw at me.

The community for unbuntu is nothing ive ever seen - keep up the fight.

---

### Post by Inxsible on 2007-11-07
> **MaDeX said:**
> Sir,

I feel your pain, my beloved 8800 GTS is going to waste - and dare I say this, i'm going back to Vista.

I have been unbuntu for around 15 hours now, and going back.... 

I loved the look and feel of this OS however its not something the average windows "fanboy" can use. Trust me, if choices was there I would choose this over anything mr bill gates threw at me.

The community for unbuntu is nothing ive ever seen - keep up the fight.

15 hours is WAYYYY too less for anyone to get accustomed to a completely new OS.

But then again, you do call yourself a Windows "fanboy" so I wouldn't blame ya :)

Linux is NOT Windows and people who come to Linux with that assumption are going to be "dis-satisfied" (damn, I can't remember the correct word here..need to hit the dictionary ;) )

---

### Post by KhaaL on 2007-11-07
Barney, since the restricted driver manager should handle it automatically, did you try the guides  *before* installing the driver through restricted driver manager? Because that could have messed up something. Just a guess from my side...

MaDeX, sounds like you're giving up too early! 15 hours is not enough to see all the goodies of Ubuntu :) and besides, you're not stating whats driving you *away*...

---

### Post by MaDeX on 2007-11-07
Stealing someone elses thread FTW...

8800 gts, I'm trying this "restricted driver" tonight, but it usually crashes ubuntu and says cannot start x server?!

Also tried nvidias own driver - but dont know what the hell i'm doing lol.

---

### Post by perlluver on 2007-11-07
Have you all tried envy?  I used envy to install the drivers for my Nvidia Geforce FX 5200, and it worked fine, when the restricted drivers, and other things wouldn't work.  If you haven't tried it I would highly recommend it.

---

### Post by Inxsible on 2007-11-07
if you want a clean slate to start with do this:

1) First make a backup of the xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
2) Then reset it```
sudo dpkg-reconfigure -phigh xserver-xorg
```After you do this, you will need to re-enable the restricted drivers and whatever other changes you had made to the xorg.


WTF help:
if, in case your X doesn't start after performing step 2 above then you can copy your backup(that you created in step 1) like so```
sudo cp/etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```Of course if you used a different name for the backup, you will need to appropriately change that.

---

### Post by MaDeX on 2007-11-07
Ok I will try this tonight, I suggest Barney does the same!

---

### Post by Six_Digits on 2007-11-07
-

---

### Post by Six_Digits on 2007-11-07
Inxsible's post should do the trick. 
> Have you all tried envy? I used envy to install the drivers for my Nvidia Geforce FX 5200, and it worked fine, when the restricted drivers, and other things wouldn't work. If you haven't tried it I would highly recommend it.
I personally used envy on 7.04 and it worked great. 
I also installed through restricted drivers on 7.10 and that worked. 

Try Envy if the restricted drivers don't work. I had to use it on 7.04 because my hardware wasn't even listed in the restricted drivers.

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

> I am more than happy to trash the nVidia crap that does not work with the OS and put something in that does.
-Don't do that... ATI can be just as hard to install.

---

### Post by PmDematagoda on 2007-11-07
While I realise that I have a card that is not exactly like yours I have an Nvidia 6200 and it works fine, and one thing, Nvidia is one of the best supported in Linux, if you cannot get that working(Especially a VGA card like the 6800), then you won't have much luck with other brands, especially with ATi.

Try what was suggested by Inxsible and see if that can help you out.

---

### Post by poudin on 2007-11-07
Envy is the answer to all your 3D woes....giving it another recommendation on top of the other 2 posts so far in this thread.

it will installed the ATI or NVidia drivers so easily...save your linux skills for other problems that don't have an easy fix like this one...

good luck

---

### Post by scriptsales on 2007-11-07
> **Inxsible said:**
> if you want a clean slate to start with do this:

1) First make a backup of the xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
2) Then reset it```
sudo dpkg-reconfigure -phigh xserver-xorg
```After you do this, you will need to re-enable the restricted drivers and whatever other changes you had made to the xorg.


WTF help:
if, in case your X doesn't start after performing step 2 above then you can copy your backup(that you created in step 1) like so```
sudo cp/etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```Of course if you used a different name for the backup, you will need to appropriately change that.

This is exactly why the windows fanboy is giving up after 15 hours. If you saw a news posting on a website that told you that windows users had to do the steps shown above just to get their graphics card to work the howls of derision would be heard half way round the world! (Another windows fanboy, although I am warming to Ubuntu after spending (considerably) more than 15 hours getting my head round it :) )

Cheers
Andy

---

### Post by bobpur on 2007-11-07
I have the answer!
You send me a round-trip ticket to Australia (1st Class no less) and I'll give you my tower complete with 2 XFX 6800 GT XXX in SLI. You do that and both our problems will be solved. It's getting cold here:) :)

---

### Post by markharding557 on 2007-11-07
> **MaDeX said:**
> Sir,

I feel your pain, my beloved 8800 GTS is going to waste - and dare I say this, i'm going back to Vista.

I have been unbuntu for around 15 hours now, and going back.... 

I loved the look and feel of this OS however its not something the average windows "fanboy" can use. Trust me, if choices was there I would choose this over anything mr bill gates threw at me.

The community for unbuntu is nothing ive ever seen - keep up the fight.

i suggest dual booting for you this way you will suffer no loss of pc use and you can boot ubuntu when you feel ready again.
i did this for 18 months before switching completly

---

### Post by Inxsible on 2007-11-07
> **scriptsales said:**
> This is exactly why the windows fanboy is giving up after 15 hours. If you saw a news posting on a website that told you that windows users had to do the steps shown above just to get their graphics card to work the howls of derision would be heard half way round the world! (Another windows fanboy, although I am warming to Ubuntu after spending (considerably) more than 15 hours getting my head round it :) )

Cheers
AndyI am sure that a regular windows fanboy would not be able to install the drivers of the graphics card even in a Windows machine if they were to install a new graphics card themselves. Even Windows would ask for some input from the user. 

People think everything works in windows only because "most" use the OEM versions. The manufacturer pre-installs everything depending on what you have in your machine.

You gotta get your hands dirty to learn something new and again Linux is NOT Windows :D

---

### Post by PmDematagoda on 2007-11-07
> **poudin said:**
> Envy is the answer to all your 3D woes....giving it another recommendation on top of the other 2 posts so far in this thread.


Not always, I know one time, Envy not only failed me but it broke the entire X-server so that I had to do everything manually, it took me two weeks to even consider it as I was asking questions everywhere but got no proper answers, so I did some experiments here and there and I got it to work, gained a lot of experience along the way as well.

But I'm not saying Envy is entirely bad since it set-up my Nvidia VGA card perfectly the first time I used it, but you cannot rely on it for solving every GUI problem you have concerning the VGA card since it could be the source of the problem itself.

---

### Post by Inxsible on 2007-11-07
I am not a fan of external softwares like Envy, Automatix. I don't know why, but I think  the installation methods available as standard in Ubuntu have always worked for me.

I'd much rather compile from source than use envy or automatix. But that's just me :)

---

### Post by PmDematagoda on 2007-11-07
> **Inxsible said:**
> I am sure that a regular windows fanboy would not be able to install the drivers of the graphics card even in a Windows machine if they were to install a new graphics card themselves. Even Windows would ask for some input from the user. 

People think everything works in windows only because "most" use the OEM versions. The manufacturer pre-installs everything depending on what you have in your machine.

You gotta get your hands dirty to learn something new and again Linux is NOT Windows :D

If that happened to a Linux fanboy, then he himself would have trouble trying to get used to Windows since, as Insxible says, Linux is NOT Windows(And vice versa);).

So the reason that many first-time Linux users find it so hard to use Linux at the beginning is because they were so used to Windows that they cannot accept another OS instantly, so be patient, take your time and you will get it and find out in the end that it was simpler than you thought:).

---

### Post by PmDematagoda on 2007-11-07
> **Inxsible said:**
> I am not a fan of external softwares like Envy, Automatix. I don't know why, but I think  the installation methods available as standard in Ubuntu have always worked for me.

I'd much rather compile from source than use envy or automatix. But that's just me :)

Same here, I try to keep away from stuff like Envy and Automatix(Especially Automatix) because in the end you wasted so much time solving your problems while using such software that it would have been faster and less painful to do the installations manually. For now, the only "Automatic" installation method I fully trust and have never failed me is the repository way (or apt-get way, whatever you like to call it):).

---

### Post by qamelian on 2007-11-07
> **scriptsales said:**
> This is exactly why the windows fanboy is giving up after 15 hours. If you saw a news posting on a website that told you that windows users had to do the steps shown above just to get their graphics card to work the howls of derision would be heard half way round the world! (Another windows fanboy, although I am warming to Ubuntu after spending (considerably) more than 15 hours getting my head round it :) )

Cheers
Andy

Actually, this suggestion is pretty tame compared to some of the troubleshooting procedures on the Windows Knowledgebase website. I've had to do far worse on Windows to resolve issues at work.

---

### Post by aysiu on 2007-11-07
> **barney66 said:**
> If you live in Brisbane QLD Australia I am happy to pay cash money for someone to come and install a working driver for my nVidia 6800GS card as it is now totally beyond me. Contact these folks. I'm sure they'll help you for free:
[http://www.humbug.org.au/](http://www.humbug.org.au/)

> HUMBUG is a Unix (for example, Linux, *BSD, OSX, Solaris etc) users group that meets fortnightly at the University of Queensland, Brisbane, Australia.

---

### Post by MaDeX on 2007-11-07
Help - i've tried installing restricted drive - X server cannot start graphics card

This has resulted me in booting from the CD!!!

I dont know the next step.

---

### Post by PmDematagoda on 2007-11-07
This is very interesting aysiu, I never knew there were people like this, but it seems like I have learned something just now, if only there were some people like that in Sri Lanka.

---

### Post by MaDeX on 2007-11-07
Sod this, going to install vista lol

o/ thanks guys anyway.

---

### Post by PmDematagoda on 2007-11-07
> **MaDeX said:**
> Help - i've tried installing restricted drive - X server cannot start graphics card

This has resulted me in booting from the CD!!!

I dont know the next step.

Did you try going through Recovery Mode? When you start your PC up you must reach a menu where you can select various choices, select Recovery Mode and when you get to a terminal, do:-

```
sudo dpkg-reconfigure xserver-xorg
```

If you cannot reach Recovery Mode, you can do that normally as well, just get to the terminal and type the command given above, in both cases after configuration is complete, do:-

In Recovery Mode:-
```
startx
```

In normal mode:-
```
sudo startx
```

And see if your problem gets solved.

---

### Post by MaDeX on 2007-11-07
Im currently using the live CD, can I do that from here?

---

### Post by aysiu on 2007-11-07
> **PmDematagoda said:**
> This is very interesting aysiu, I never knew there were people like this, but it seems like I have learned something just now, if only there were some people like that in Sri Lanka.
You mean like this?
[http://www.linux.lk/](http://www.linux.lk/)

---

### Post by PmDematagoda on 2007-11-07
> **aysiu said:**
> You mean like this?
[http://www.linux.lk/](http://www.linux.lk/)

Thanks aysiu, that was exactly I was looking for, but sadly it seems that they had no activity for about 1 and a half years:(, I wonder when they will have their next exhibition or event as I would really like to attend it, but thanks anyway aysiu:).

By the way, how did you find this web site?

To MaDeX:- No, do not use the Live CD, use the old Ubuntu installation itself.

---

### Post by stchman on 2007-11-07
> **MaDeX said:**
> Sir,

I feel your pain, my beloved 8800 GTS is going to waste - and dare I say this, i'm going back to Vista.

I have been unbuntu for around 15 hours now, and going back.... 

I loved the look and feel of this OS however its not something the average windows "fanboy" can use. Trust me, if choices was there I would choose this over anything mr bill gates threw at me.

The community for unbuntu is nothing ive ever seen - keep up the fight.

WOW, a whole 15 hours!!!!!

After that time period you should be a master of Ubuntu.  It takes the average user about 20 hours to become grand master.

---

### Post by MaDeX on 2007-11-07
I've tried those commands - says something about stating more or less?!

any more suggestions?

---

### Post by mali2297 on 2007-11-07
> **MaDeX said:**
> I've tried those commands - says something about stating more or less?!

any more suggestions?

If you want to get back to the starting point, use your backup. (You did follow the advice to make a backup, didn't you?)

> 
if, in case your X doesn't start after performing step 2 above then you can copy your backup(that you created in step 1) like so
Code:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Of course if you used a different name for the backup, you will need to appropriately change that.


:!: Note that it should be a space after cp.

---

### Post by MaDeX on 2007-11-07
wow - er - your right no backup

It's a reinstall then lol..

Also now I have two drives with two os's I use f12 in the bios setup to choose what os I want to boot from right?

or is there a different way?

---

### Post by Inxsible on 2007-11-07
> **MaDeX said:**
> wow - er - your right no backup

It's a reinstall then lol..

Also now I have two drives with two os's I use f12 in the bios setup to choose what os I want to boot from right?

or is there a different way?No wonder you got frustrated in 15 hours. You don't seem to follow instructions carefully. Making backups is very very important when mucking with stuff. I cannot stress its importance !!!!

---

### Post by edwardLS on 2007-11-07
I happen to have the nVidia 6800GS card in my system at home.  I have successfully installed the Proprietary drivers for that card in Ubuntu (Dapper, Feisty, and now Gutsy).  I also have had an nVidia 6200 card and was able to install and configure the Proprietary drivers for it under Dapper only.  I did not try it on other ubuntu releases.  I have installed the nVidia Proprietary drivers by several means, including Synaptic, Envy, and Restricted Drivers Manager.  

I can't offer you any help, but I do want you to know that your nVidia card does work with ubuntu in at least one case.  Good luch and hang in there.  I believe that the effort will be worth it.

---

### Post by mali2297 on 2007-11-07
> **MaDeX said:**
> wow - er - your right no backup

It's a reinstall then lol..

Also now I have two drives with two os's I use f12 in the bios setup to choose what os I want to boot from right?

or is there a different way?

If you haven't done a reinstall yet...

Sometimes the system makes backups of xorg.conf before changes, check
```

ls /etc/X11/xorg.conf*

```
If it list some file besides xorg.conf, you can try to use that (with *sudo cp ...*).

Otherwise, you can run
> 
sudo dpkg-reconfigure xserver-xorg

There will be a list of drivers to choose from, try *vesa* if you don't find any better.

---

### Post by barney66 on 2007-11-07
Hi everyone,

thanks for the replies.

firstly the restricted driver manager does not work. it clearly shows the nVidia card unchecked however when it is checked to enable it returns the following error - 'the software source for the package nvidia-glx-new is not enabled'.

secondly d/l the nVidia driver from nVidia and following their own install instructions results in the error stating I need to find a development 'libc' package so as to allow me to rebuild the kernel.

thirdly I could go on and on and on. In fact I have now become the millionth person to start a thread on a linux forum regarding this problem. There is an OBVIOUS problem in the manner in which the video card driver is installed to the OS.

It is incredibly frustrating. why? well from an idiots point of view (and i am an idiot) the OS is never going to be accepted mainstream if driver installation is so difficult to achieve. I was under the impression that Ubuntu was hoping for some form of market place acceptance especially since DELL has been shipping it on certain laptops. I LOVE the operating system, I had no problems installing it on a new machine. I had no problems hooking it up to my VISTA home network. I had no problems hooking it up to my wireless 'N' adsl2+ router. But bugger me if it is near on impossible to install the correct Linux driver to run the video card.

Again a lot of people have offered advice and it is probably good advice but is does not work. Would it not be better to try and write a paper on the exact steps to take to install the driver. The people offering assistance are other users. Would it not be more appropriate for the folks at nVidia and Ubuntu to sit down and have a look at how the driver is installed and produce a correct install guide. I do hate windows but one could only praise the way in which they have conquered the problems associated with video card installation.

Again I would like to thank everyone for their input.

regards,
barney66

---

### Post by aysiu on 2007-11-07
> **barney66 said:**
> 
It is incredibly frustrating. why? well from an idiots point of view (and i am an idiot) the OS is never going to be accepted mainstream if driver installation is so difficult to achieve. You're assuming your experience (while still valid) is typical. It is not typical.

---

### Post by justsomedude on 2007-11-07
> **barney66 said:**
> 

Firstly the restricted driver manager does not work. it clearly shows the nVidia card unchecked however when it is checked to enable it returns the following error - 'the software source for the package nvidia-glx-new is not enabled'.

Enable it. System --> Administration --> Software Sources

-You will be prompted to reload.
-Reload.
-Install your driver with the Restricted Drivers Manager

---

### Post by mivo on 2007-11-07
> **MaDeX said:**
> I feel your pain, my beloved 8800 GTS is going to waste - and dare I say this, i'm going back to Vista.

I have exactly the same card (the 640 MB model from Gainward) and it worked right out of the box with the restricted drivers that Gutsy offered for installation after the first boot-up. The card itself is certainly compatible with 7.10. Puzzled as to why you are having trouble, though. :(

---

### Post by barney66 on 2007-11-07
justsomedude... THANK YOU!!! it was a simple step that worked perfectly. It is a shame that this simple step is not annotated in nVidia's install instructions. Again thank you very much it was greatly appreciated ! \\:D/\\:D/

regards,
barney66

---

### Post by Inxsible on 2007-11-07
> **barney66 said:**
> justsomedude... THANK YOU!!! it was a simple step that worked perfectly. It is a shame that this simple step is not annotated in nVidia's install instructions. Again thank you very much it was greatly appreciated ! \\:D/\\:D/

regards,
barney66I am glad its working for you. If you clearly tell everyone what the problem is, someone will definitely be able to help you out.

---

