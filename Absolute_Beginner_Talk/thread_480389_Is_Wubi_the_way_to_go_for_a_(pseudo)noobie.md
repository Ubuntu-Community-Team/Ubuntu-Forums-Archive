---
title: "Is Wubi the way to go for a (pseudo)noobie"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by arielb_86 on 2007-06-21
Hi
So after getting the intense response on my own Ubuntu review somewhere in this forum, i ready to get back to the linux(id rather eat a bird flu sandwitch before turning my pc and getting the XP logo again)
Since last time i went into so much trouble to uninstall Ubuntu(due to the dual boot), i heard of Wubi that it install/uninstalls easily.

I was wondering if the performance is really that sacrifized since it is installed in WXP? Also once i decide to uninstall wubi(IF) would it restore the dual boot that it creates?(dont feel like struggling again with it)

Any good tutorial apart from the one in the main website of Wubi?
btw, i would sacrifice performance for now until i get a hand on linux again. Im just afraid of the uninstall process.

Thanks!

---

### Post by Nekiruhs on 2007-06-21
There is no sacrifice in speed. Only downsize is you get abouta 15 gig HD for Ubuntu. Thats plenty of space for most but I use lots of large files so Wubi was not for me. If you uninstall Wubi, Ubuntu is uninstalled as well. Wubi treats Ubuntu like a program.

---

### Post by arielb_86 on 2007-06-21
i know that Wubi would create a virtual drive that will be detected by the boot load and it will appear as a dual boot.
Once i uninstall it will it restore the normal windows boot?
Thanks!

---

### Post by Nekiruhs on 2007-06-21
Yeah, when you uninstall Wubi, it will restore windows boot to normal.

---

### Post by arielb_86 on 2007-06-21
Sweet!:p
How interesting to see that Linux seems to be so hard(well part of it i guess) yet it is much more easier than XP.

Any recomendations for Wubi? apart from a normal back up? defrag?
Thanks!

---

### Post by abn91c on 2007-06-21
> **arielb_86 said:**
> Sweet!:p
How interesting to see that Linux seems to be so hard(well part of it i guess) yet it is much more easier than XP.

Any recomendations for Wubi? apart from a normal back up? defrag?
Thanks!

when the windows install part is done it will ask to reboot, allow the pc to do it by it self. DONOT use reset button or power off,or hard boot. It will mess up the remainder of the installation process. be patient, when it reboots, select ubuntu from the boot screen and just follow the prompts to finish the installation.

---

### Post by arielb_86 on 2007-06-21
I heard Wubi will download a special ISO that is special (some lacking of programs). I also heard that if i get the original ISO and put it on the same directory where wubi is installed it will detect it and use that one instead of download it.

Can anyone confirm this?

---

### Post by abn91c on 2007-06-21
you can do that, however when wubi is finished you get the full functionality of ubuntu, any program "missing" you can install by  doing sudo apt-get dist-upgrade in a terminal window or by using the Adept Manager to install any packages that are availlable with a clean install. By default it install moust of the progams available on a live cd-OpenOffice, amarok,kaffeeine, gimp etc...

---

### Post by arielb_86 on 2007-06-21
and one more question, Wubi creates partitions for swap and such, will they get destroyed and merge back to the original drive IF i decide to uninstall it?

---

### Post by mengfei on 2007-06-22
Yes, don't worry, you'll be absolutely fine.

Normally, Ubuntu partitions your hard drive, and then installs its own boot loader.

Basically, you have a split hard drive, and then your Windows XP won't have a boot loader if you decide to remove Ubuntu. Not saying it's impossible, but it's certainly not a click away.

Wubi, on the other hand, makes an image file on your Windows partition. Pretty clever, huh? Therefore, your WIndows XP keeps its boot loader. Actually, Wubi uses that boot loader itself to boot. Also, when you uninstall Wubi, that image file is deleted, meaning you get back all the space that was used up by Wubi.

So, aside from any possible leftover registry entries and such (no biggie, most programs do when they uninstall in XP), Wubi will leave your XP installation the same exact way if you decide to uninstall.

Hope that helps!

---

### Post by arielb_86 on 2007-06-22
I read around that Wubi still does some have some problems(hibernation and stuff like that) which im willing to sacrifice for now. 

What would happend when Ubuntu 7.10 comes up? do i need to reinstall Ubuntu with the new Wubi version?
should i wait until 7.10 comes out?

Thanks!

---

### Post by open2linux on 2007-06-22
Hello,
I am a windows user who just started to use Ubuntu thanks to Wubi.
Just saw your posting here. I am new in Ubuntu so I can't give -yet;) any technical assistance.
But you can get ALL questions about Wubi in the dedicated Wubi forum here:
[http://ubuntuforums.org/forumdisplay.php?f=234]("http://ubuntuforums.org/forumdisplay.php?f=234")

There you will find the frienly makers of Wubi, which by the way has a new web site here
[http://wubi-installer.org/]("http://wubi-installer.org/")

Do not worry. If you are new like me and are a bit afraid of partitions and all that,
then Wubi is for you.
I have installed and uninstalled it already four times and always Windows comes as if was before.

Hope this helps

---

### Post by abn91c on 2007-06-22
> **arielb_86 said:**
> I read around that Wubi still does some have some problems(hibernation and stuff like that) which im willing to sacrifice for now. 

What would happend when Ubuntu 7.10 comes up? do i need to reinstall Ubuntu with the new Wubi version?
should i wait until 7.10 comes out?

Thanks!

That is probably because individual hardware/video card issues, I have it on my Dell 2400 desktop(standard factory setup, no fancy addons!),Beryl runs normally the soud card and 3d effects same, I have a screensaver running and never had any problems getting the CRT monitor to come out of sleep.

---

### Post by abn91c on 2007-06-22
when 7.10 comes out just do the upgrade with adept or sudo apt-get, only thing you may have to worry about is the size of the virtual drive wubi creates and the size of the upgrades. My kubuntu drive has about 1.7 gig out of 4.5 free space since I installed with default settings.

---

### Post by ubromtoo on 2007-06-22
Right now I have a dual-boot with Dapper 6.06 and Windows XP .

  Question : can I use Wubi to run Feisty Fawn, without messing up Dapper , so that I'll

  have three options on one computer ( Dapper, and XP / Feisty  ) ?   :-k

  Free disk space is not a problem.

---

### Post by ubromtoo on 2007-07-24
Decided to take the plunge , and just do it .

  That was three days ago, and so far it is 99.9% perfect !!  :)    There are two minor problems

which may not be connected to Wubi at all (who knows ?) ; they are :

    1)  There is no way I can see to get Evolution email going;  F1 does nothing at all, ditto for

 "Help > contents " .     Edit > Preferences  is all filled out nicely , but it rejects my  password

as Invalid , when in fact it's the correct password.  There is no sign of an Install Wizard.

 Uninstalling and Reinstalling Evolution would involve so many other things, till I'd rather not.

 In the meantime, Thunderbird email is working fine , but still I'd like to solve this problem.

    2)  On the Desktop is an Icon "HP_PAVILLION"   which will not go away :  if I right-click , the Delete and Move to Trash  options are greyed out,

and the Unmount option yields a warning which says the icon " was probably mounted 

manually on the Command Line "   but icon doesn't show up as a hidden file .  Even tried

the "force quit " option, but no luck.


    But otherwise , the Wubi setup is very satisfactory so far !  The installation went very

smoothly (although it took a good while), and there has been no trouble at all switching from

Wubi-Feisty to Dapper to Windows XP.

---

### Post by ubromtoo on 2007-08-11
trouble in paradise:

      the (wubi) Feisty 7.04 began behaving erratically, then I had to pull the plug in order

to exit Feisty, then feisty would not start up, "error 17" .

      Searching the web led me to try defragmenting Windows as a way to bring 

Wubi/Feisty back , and it worked- feisty started up again, but misbehaved and I could

shutdown only by pulling the plug again.

       After that, neither Windows XP Home nor  (Wubi) Feisty will start up :mad:

    So I'm limited to Dapper which is on its own partition , and which still starts

and operates o.k..

     I can get into the recovery module , but going that route will wipe

all my files so I'm hesitating to do that.

      Will using the recovery module also kill my Dapper partition ?

I don't yet know.   Woe is me :(

---

