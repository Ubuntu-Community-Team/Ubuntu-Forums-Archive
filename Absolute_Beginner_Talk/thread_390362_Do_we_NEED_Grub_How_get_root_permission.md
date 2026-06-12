---
title: "Do we NEED Grub? How get root permission?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by brit0n on 2007-03-21
1. Do we NEED Grub? First time I ever installed a GUI version of Linux and I don't want Grub! I boot load happily from XOSL and can put it back on any of our machines in a few moments after an install messes with the MBR or even partition table. But the way Ubuntu 6.10 is set up (from the download iso) is that it installs Grub like it or not. So I have to point XOSL at Grub which is a somewhat ludicrous way to move forward technically with an OS, wouldn't you think?

So, can I get rid of Grub and if so how? And can I then just point XOSL at the native partition (as it is now)?

2. In the meantime, I went in and read up enough to do two things: a. Auto-login with a hidden login. b. Make Grub start Ubuntu by default after a 0 second timeout. Now this will be a dumb question to those of you who only know Linux (or Unix), but it seems odd to me that on a single PC with only one user, the default is that I do NOT have root permission. Without it, I cannot edit menu.lst to get the Grub defaults changed. Help misses this point entirely.

So, how do I get permissions for root and then everything else?

---

### Post by tzulberti on 2007-03-21
> **brit0n said:**
> 1. Do we NEED Grub? First time I ever installed a GUI version of Linux and I don't want Grub! I boot load happily from XOSL and can put it back on any of our machines in a few moments after an install messes with the MBR or even partition table. But the way Ubuntu 6.10 is set up (from the download iso) is that it installs Grub like it or not. So I have to point XOSL at Grub which is a somewhat ludicrous way to move forward technically with an OS, wouldn't you think?

So, can I get rid of Grub and if so how? And can I then just point XOSL at the native partition (as it is now)?

I think you need grub, because with every kernel update, a new option in the grub menu should appear
> 
2. In the meantime, I went in and read up enough to do two things: a. Auto-login with a hidden login. b. Make Grub start Ubuntu by default after a 0 second timeout. Now this will be a dumb question to those of you who only know Linux (or Unix), but it seems odd to me that on a single PC with only one user, the default is that I do NOT have root permission. Without it, I cannot edit menu.lst to get the Grub defaults changed. Help misses this point entirely.

So, how do I get permissions for root and then everything else?

You can get root permissions by running from console:
sudo comandToRun... in you case:
sudo nano|vim|gedit /boot/grub/menu.lst

---

### Post by dfreer on 2007-03-21
> Do we NEED Grub? So I have to point XOSL at Grub which is a somewhat ludicrous way to move forward technically with an OS, wouldn't you think?

You DO need some way of booting the OS, whether that OS is linux, OSX, windows, whatever. You don't need to use GRUB to boot, you could even use windows NTLDR and boot.ini (after a *lot* of hard work) to boot Linux. It is just so much easier to use GRUB, which is why Ubuntu installs it by default. 

GRUB works amazingly well, I do not see any advantage of using XOSL instead of GRUB, but that, as always, is your choice, which is what Linux is all about. If you don't want to have it install GRUB, you can use the Alternate Install CD (should have options to install GRUB, LILO, or nothing at all) or use a different distribution. 

Well, it's ludicrous if you want to use XOSL to boot instead of GRUB. It's great for everyone else who likes GRUB.

So, can I get rid of Grub and if so how? = Use Alternate Install CD
And can I then just point XOSL at the native partition (as it is now)? = Yes

> Now this will be a dumb question to those of you who only know Linux (or Unix), but it seems odd to me that on a single PC with only one user, the default is that I do NOT have root permission. Without it, I cannot edit menu.lst to get the Grub defaults changed. Help misses this point entirely.


It seems odd because you are coming from an insecure OS viewpoint (probably windows). You can (and should) read up on this online. To answer your question though, you can gain root permission by issuing the *sudo* command as a normal user. You can even set a password for root by *sudo su* and then *passwd*. From there you can edit your /etc/gdm/gdm.conf and enable root login, so that you will always have root permissions. THIS IS NOT RECOMMENDED, I am simply telling you because it's your choice. It's also your choice to have someone hack your machine and hose up your ubuntu install by a mistyped command. 

> ```
sudo nano|vim|gedit /boot/grub/menu.lst
```

In case you are confused...
```
sudo nano /boot/grub/menu.lst
sudo gedit /boot/grub/menu.lst
sudo vi /boot/grub/menu.lst
```

Any of those commands will work, but if you aren't using GRUB anymore it's kind of a moot point.

> I think you need grub, because with every kernel update, a new option in the grub menu should appear

This is another good point. Everytime you update to a new kernel, you will have to modify your XOSL bootup to point to the new kernel.

---

### Post by brit0n on 2007-03-22
> **tzulberti said:**
> I think you need grub, because with every kernel update, a new option in the grub menu should appear


You can get root permissions by running from console:
sudo comandToRun... in you case:
sudo nano|vim|gedit /boot/grub/menu.lst

Thanks for that second part, great answer. Now I know what tonight's project is! :D

Now if I understand the first part, you aren't actually saying I CANNOT get rid of Grub but that without it I can't update Ubuntu? Sounds rather like Microsoft Windows Updates to me. Did you mean that? Or did you just mean that I can't SELECT to boot with an older kernel after an update? Because I have a feeling that, even without Grub I could adjust some settings in a configuration file if I wanted to backtrack.

Which?

If I CAN do without Grub, how do I dump it?

In the meantime, I'll work on getting the permissions which allow me to not even see Grub in passing for which thanks.

---

### Post by brit0n on 2007-03-22
> **dfreer said:**
> You DO need some way of booting the OS, whether that OS is linux, OSX, windows, whatever. You don't need to use GRUB to boot, you could even use windows NTLDR and boot.ini (after a *lot* of hard work) to boot Linux. It is just so much easier to use GRUB, which is why Ubuntu installs it by default.

No work at all, but thanks for the comment. I could do that but I prefer XOSL because I can manipulate it manually in no time at all across a bunch of PCs as I do the partition tables and MBRs which is IMMENSELY easier than what you mentioned (don't ice the cake and sour the pie lol). You said "You DO need some way of booting the OS" - yep, but I already mentioned I already have one I like thanks and I already fought through XP and Vista attempting to change it so I wasn't happy to find OSS doing that!

But my question was "Do I ALSO need Grub?". I mean, my boot loader doesn't point at XP/Vista and then XP/Vista ask which version I want to run - I already told them I am in charge!

> **dfreer said:**
> GRUB works amazingly well, I do not see any advantage of using XOSL instead of GRUB, but that, as always, is your choice, which is what Linux is all about. If you don't want to have it install GRUB, you can use the Alternate Install CD (should have options to install GRUB, LILO, or nothing at all) or use a different distribution. 

Grub does NOT work amazingly well for the configuration of PCs I am working on. But I doubt you would want me to quote the sources of why not because it works for you! Choice? Hmmm! So far, I haven't found a reference which answers that I can dump Grub and put it back later if I want it. By tomorrow, I will boot Ubuntu without seeing Grub but that's not a choice. If I can remove it, I can always put it back from within a Windows partition but editing the files there!

> **dfreer said:**
> Well, it's ludicrous if you want to use XOSL to boot instead of GRUB. It's great for everyone else who likes GRUB.

Sorry. You are rather overstating your case. Everyone who likes GRUB can use it. Why would it be ludicrous for someone to want choice?

> **dfreer said:**
> So, can I get rid of Grub and if so how? = Use Alternate Install CD That gets rid of it? Or you mean I have to install again? I can't believe there isn't a way to get rid of it!

> **dfreer said:**
> And can I then just point XOSL at the native partition (as it is now)? = YesThanks. If I can find what you mean by "an alternat install CD" I might try it. Or I might read up to find out how to get rid of Grub which would allow me to put it back from outside Linux.

> **dfreer said:**
> It seems odd because you are coming from an insecure OS viewpoint (probably windows).What seems odd?

> **dfreer said:**
> You can (and should) read up on this online.I am and have! But I don't expect to install the latest version of a brand new OS and then ASK to change the rights I have to change the files. I mean, my biggest complaint against Microsoft is that they assume we are all idiots and are going to make mistakes and then blame them. But if I mess Ubuntu up, I will simpyl learn and then put it back how it should have been. Not a lot to ask. So on the way in, I would at least have expected to be given options WITH STRONG GUIDANCE to give myself permissions.

Let me try to give you an analogy: in Windows, the DEFAULT setting for Explorer (after Win 3.1 WFW if my failing memory serves me correctly) was that you couldn't view hidden and system files and folders. Again, I would have preferred the choice with STRONG guidance not to change it (which it gives).

OSS is about me messing with my own stuff isn't it?

Thanks for the further detail of the configuration.

> **dfreer said:**
> This is another good point. Everytime you update to a new kernel, you will have to modify your XOSL bootup to point to the new kernel.

You think? But if I get rid of Grub (or bypass it), there will only be one OS on that partition won't there? I thought the point of having a choice was that Grub would allow me to GO BACK to an earlier version of the kernel, not that it would allow me to GO FORWARD to the one I just updated to. I guess I am wrong again :(

---

### Post by tonyr1988 on 2007-03-22
> **brit0n said:**
> That gets rid of it? Or you mean I have to install again? I can't believe there isn't a way to get rid of it!

To get rid of it, just install something else in your MBR.

> **brit0n said:**
> Thanks. If I can find what you mean by "an alternat install CD" I might try it. Or I might read up to find out how to get rid of Grub which would allow me to put it back from outside Linux.

When you downloaded the LiveCD, there is also an option to get the "Alternate Install CD" instead. The LiveCD isn't perfect for everyone, but for most users it works perfectly. Obviously,  your case is one in which you *don't* want the LiveCD, as it installs GRUB by default.

> **brit0n said:**
> I am and have! But I don't expect to install the latest version of a brand new OS and then ASK to change the rights I have to change the files. I mean, my biggest complaint against Microsoft is that they assume we are all idiots and are going to make mistakes and then blame them. But if I mess Ubuntu up, I will simpyl learn and then put it back how it should have been. Not a lot to ask. So on the way in, I would at least have expected to be given options WITH STRONG GUIDANCE to give myself permissions.

It's not that Ubuntu is protecting your computer from yourself, but from outside threats. There's a reason that Microsoft (finally) made the default user a non-Administrator in Vista. It's a HUGE security advantage, as you would have to literally type your user password and grant access to an unwanted program to edit your important configuration files.

Of course, it's all about choice. If you want, you can gain root access. It's strongly recommended against (unless your box isn't going to be online), but it's possible.

> **brit0n said:**
> You think? But if I get rid of Grub (or bypass it), there will only be one OS on that partition won't there? I thought the point of having a choice was that Grub would allow me to GO BACK to an earlier version of the kernel, not that it would allow me to GO FORWARD to the one I just updated to. I guess I am wrong again :(

I'm not sure how XOSL works, so I'm not going to speculate on that. However, GRUB simply allows you to specify which kernel you wish to boot for a particular Linux OS. They aren't actually listed as separate operating systems. After you do an Ubuntu kernel upgrade, it will automatically throw the new (and old) kernels into GRUB. It's simply an extra feature. I'm not sure if XOSL can boot multiple kernels or not...

---

### Post by macogw on 2007-03-22
Just edit XOSL to boot directly to your Linux kernel instead of telling it to chainlink GRUB.  It can completely ignore GRUB's installation, but you can apt-get remove grub, I believe.  

When you update, the new kernel is ADDED to /boot/grub/menu.lst.  If you don't have GRUB, it can't add it to there :p  You'll have to manually add it to XOSL's configuration.  XOSL should allow you to have a list of the old ones as well too though.

Many distros have a root password that you can set and root password you can log in with.  The problem with this is that if someone tries to hack your box, they already know that "root" is the username, so they just need the password.  If "root" is completely disabled, they can't h4x0r your box without guessing BOTH your username AND your password.  It's a security measure.  Think of "sudo" as Simon Says.  If you don't say "Simon says..." the kids don't do it.  Also, sudo is a physical-security thing.  It's a lot easier to revoke sudo rights from a user than to magically make them forget the root password, AND you have the added advantage of being able to see which user issued the command that caused the problem and reprimand them accordingly.  Add to that the fact that if you are only popping into admin mode for short bursts while you do things, there is less time spent with someone (like a cracker) being able to manipulate your computer.  It's a lot easier/faster to password-authorize an action than to log out, log in as root, do it, and then log out of root, and log back in as yourself.  This way, you can do it without logging out.

---

### Post by brit0n on 2007-03-22
> **macogw said:**
> Just edit XOSL to boot directly to your Linux kernel instead of telling it to chainlink GRUB.  It can completely ignore GRUB's installation, but you can apt-get remove grub, I believe.Well, removal of grub would be a prerequisite if I understand it correctly. XOSL points at a bootable partition's boot sector (on any partition on any disk but it can set that disk to "act" as if it is the first disk and it can make the partition the active one, which means of course that a non-Unix type OS can be conned into believing that it is where it "should" be and also means that the booted OS can be on C: in all cases - all this appears to be a foreign language here of course). For now, I have no earthly idea how to point ANYTHING at one specific kernel, but as that ignorance and the failure of well-meaning people to actually show they KNEW the boot process of Linux was the reason why I started getting a more up to date version of Linux on every box on the net so that I can, at any time, find out for myself. But until it's easy to get INTO that OS without feeling like I never wrote a partition table, an MBR, a C++ or machine language program etc etc, it's kind of hard to leave it running on a machine which I need to USE between times.

So now I add "kernel booting" to my reading list :|

> When you update, the new kernel is ADDED to /boot/grub/menu.lst.  If you don't have GRUB, it can't add it to there :pFor now (and maybe forever), it seems best to automate the login invisibly and set Grub to boot default with 0 timeout which will allow any changes in the future without much of a problem. It just seemed strange that, in supposedly moving forward, I have to chain the boot loaders AS THE DEFAULT condition - neither XP nor Vista expected me to do that if I tore their bootloaders out after installation so I wasn't expecting it! (I am VERY glad I am not doing this in the days when disk space was previous and boot time could be immense - take me back to a mainframe mill time or later an Apple IIe and ask me again lol)

Thanks for the note about sudo. Since tzulberti's post, I've added sudo to do some reading up on.

Thanks also for the security brief. Actually, I am still not sure how you think someone is going to get inside one of the boxes, but I'll read up on that too based on what you say. You're making me wonder if Linux is really as secure as the pundits have suggested or if it was never so much of a target - never before had this much "worry" thrown at me within 36 hours of installing an OS and never had insecurity that wasn't a hole I dug for myself!

The thing i am NOT getting is that Ubuntu is, above all, supposed to be for "everyman". Now, the everyman I met had one PC. I may have a bunch of boxes strung around the place, but each one has, at any one time, an owner. So to stick something as useful as Ubuntu into a box - if you only had one, say - and then find you have to work out how to allow yourself to do all sorts of little tweaking - seems strange to say the least. Maybe I'll get used to it, but given that I am stuck with at least 2 varieties of Windows (because many people out there use them so writing programs rather requires the use of the OS one is writing it for) and at least one DOS per box (because administering the detail is useful and quick from that) in addition to any Linux distributions we test, Ubuntu would have to work harder at the installation options to persuade us to recommend it as a switchover from other OSs.

OK. I have enough to read on from and I just realised this is some kind of debate so maybe some moderator can shove it where it ought to be because I don't find the layout of these forums so intuitive - if you don't believe me, see that one of the first stickies an "absolute beginner" hits is "looking for Beryl?" which would make one wonder who much one was supposed to know before being an absolute beginner! Never mind. More reading for me....

---

### Post by igknighted on 2007-03-22
For the issue of new kernels causing issues with XOSL, there is a symlink to the latest kernel in the / partition called vmlinuz.  Also there is a link to the initrd file, I think called initrd.  Point to these and you shouldn't have to worry about it again.

As for the XOSL/GRUB debate: I think both will suit your needs fine.  I personally think grub can handle what you describe (tricking windows and other OS's that want to be on the primary bootable partition to think they are), but grub is something I understand very well.  You know XOSL better, so I am not going to try to convince you to change.  From what I saw on the  XOSL website, you do need grub.  But it can be installed locally.  When  installing from the live CD (not dapper, but edgy/fiesty do this) in the last step before install it shows you that it assumed grub goes to the MBR - (hd0) in grub speak.  Change that to (hd0,#) where # is the number of the partition linux is on, minus one (number starts at 0, so if its on the first partition (hd0,0) would be used).  Then turn XOSL loose on that partition and grub will take over.  Point grub to the vmlinuz and initrd files above, then set the timeout to "0" and it wont make you wait.

If this computer is not online, or you aren't afraid of being hacked, try this: Go to System->Administration->Login Screen.  On one of the tabs there is an option to enable local administrator login.  Set a password for this account and the username should be "root".  you can login as this user and have free reign.  Note: most linux distro's have this enabled as default but tell you not to use it except when absolutely needed.  Ubuntu takes a different approach.  As stated before, be cautious as you are now god... and be aware that this is a VERY unconventional approach.  However if it suits your needs better, it is what you should do.

EDIT: Linux security is partially because it is lesser known... but consider that 60+% of the web is on Linux servers.  I feel these are big targets for hackers/virus makers.  Same with the servers belonging to corporations, many of which run linux.  There are lots of targets that would be worthy.  Linux is inherently more secure, but in realizing what it does to be more secure, remember that in windows you were not secure without ever realizing why.  Take for example: you open an email or visit a shady website.  A script runs (or an activeX control) that tried to mess up some important files.  In linux, it wouldn't have permission and would ask for your password.  You would say 'hey, im not doing any admin level work, no way!".  In windows, it could run in the background without your knowledge, possibly installing a backdoor, trojan, or anything else it pleases.  Most linux attacks that are successful are password cracks.  A hacker (cracker I guess is more accurate... many legitimate programmers are considered "hackers", it doesn't mean anything malicious, except in the public eye) would attempt a net login to the "root" account millions of times (automated) trying to break the password.  A long, alphanumeric random password is resistant to these attacks, as many attempts use common words and phrases as their guesses.

In Ubuntu, as root is disabled, there is an extra layer of security.  Any attempt to break into your system would require the cracker to guess both your username AND password to get in, and then use sudo.  The odds of such an attack are low.  Therefor most distro's use root as an acceptable login.  (note, if you are logged in as root and ran a browser and that script I mentioned above ran, it could install, like in windows, and open backdoors into your system).  Obviously there is no guarantee you won't get hacked, but the odds of catching anything are very low, mostly thanks to linux's security.

---

### Post by dfreer on 2007-03-22
If you want to use XOSL, that's fine. Although I'm curious to know exactly why you think that XOSL is better than GRUB, and why GRUB will not work in your enviroment (what are you trying to do?). It sounds like all you are running is Windows XP, Windows Vista, DOS (just for XOSF I assume?), Ubuntu, and possibly more linux distributions.

So this is how XOSL would have to load things.
```
BIOS > MBR > XOSL > NTLDR (XP)                     > XP
                  > Bootmgr.exe (Vista)            > Vista
                  > GRUB (Ubuntu)                  > Ubuntu
                  > foobar bootloader (fooLinuxOS) > fooLinuxOS
```

This is how GRUB would load things.
```
BIOS > MBR > GRUB > Ubuntu
                  > NTLDR (XP)                     > XP
                  > Bootmgr.exe (Vista)            > Vista
                  > fooLinuxOS
```

Sure, you can edit either NTLDR, Bootmgr.exe, or GRUB to boot any of the other OS's but that would complicate things further. You seem to think that by wiping out the MBR and having it load XOSL that you have gotten rid of windows bootloader. Nope.

Not only that, but the difference between the Ubuntu GRUB install and Windows install. Windows gives you no choice when wiping the MBR, it simply does it. If Ubuntu Desktop 6.10 detects a windows install it will prompt you before overwriting the MBR, and you can always simply install the Stage 2 GRUB in the root (or /boot) partition without overwriting the MBR at all, no alternate CD required.
It sounds like XOSL cannot boot linux kernels directly, so you will have to use the stage 2 GRUB at least.

> if you don't believe me, see that one of the first stickies an "absolute beginner" hits is "looking for Beryl?"
That is because ubuntu forums see tons of people new to linux who see a video of beryl in action on youtube and come running here when they can't get it working.

> Ubuntu would have to work harder at the installation options to persuade us to recommend it as a switchover from other OSs.
It's one thing for you to want to use XOSL, but for the average windows user fresh to linux XOSL would just be a major bump in the road, requiring extra configuration for it to run.

---

### Post by louieb on 2007-03-22
> **brit0n said:**
> 1. Do we NEED Grub?
Any Linux distro need a boot loader. The two most common are GRUB and LILO. Don't confuse a boot load with a boot manager  GRUB and LILO are both. What about XOSL don't know anything about it. Does it do both or is it just a boot manager like GAG or SBM. 
> **brit0n said:**
> 
So, can I get rid of Grub and if so how? And can I then just point XOSL at the native partition (as it is now)?
The short answer is no you can't get rid of GRUB. But you don't have to install it to the MBR of the hard drive. If you look closely its install location can be changed to the MBR of Ubuntu's install partition.    
> **brit0n said:**
> 
but it seems odd to me that on a single PC with only one user, the default is that I do NOT have root permission.
Linux is by design a multi user system. You don't want every Tom, Dick and Harry logging on as a super user and doing what ever they want to the system. Linux doesn't know or care that its only Tom on your computer.
> **brit0n said:**
> 
So, how do I get permissions for root and then everything else?
In Ubuntu use sudo. or jump through some hoops and enable root login or Fedora has the root account enabled by default.
> **brit0n said:**
> 
But until it's easy to get INTO that OS without feeling like I never wrote a partition table, an MBR, a C++ or machine language program etc etc
Installing Linux is just as easy and a lot of distros are easier to install and configure that windows. It when a person decides to put multiple OS's on a computer that the fun begins. That when partitions, boot loaders, boot managers, whats an MBR? and all that good stuff come up. 

I've come to the conclusion that dual booting is a big pain in the as. I have switched to using multiple computers, a KVM switch for keyboard, mouse and display sharing. A router for networking, internet and printer sharing. 

And last my take on VISTA. Bought the wife a new laptop last month w/VISTA installed. It took almost 2 days to get the damn thing to become a part of the home network and use the network printer. Took another day to get it to print in color on the network printer. These are things it takes me about 5 minutes to do in Ubuntu or XP. > **brit0n said:**
> The thing i am NOT getting is that Ubuntu is, above all, supposed to be for "everyman".

 Linux may not be ready for use by everybody. But neither is VISTA.

---

### Post by brit0n on 2007-03-23
OK. I feel I ought to answer my own question in case someone else comes across this with Ubuntu, but then I will check the XOSL forums at Yahoo when I have time to make sure the answer is there and see if it is the same.

As always with Linux, my ignorance led me to believe it was an OS similar to any other operating system. The whole idea of "replaceable or swappable kernels" (I am sure the Linux community has a term for this, but if I have seen it so far, it wasn't intuitively understandable as such to an outsider lol) means that XOSL (up to v1.1.5 before it came over to OSS development) had a "booting different Linux kernels" workaround included in it. (Yes, I feel that was a workaround which Guert Vos then included in the code to get the solution out quickly because of the shortage of development time).

In the XOSL documentation - if anyone has XOSL v1.1.5 downloaded, they can read this in the User Manual (html) and I believe it is also in the XOSL site online documentation - it clearly states as follows (check the site for the latest):

[FONT="Arial Narrow"][I]6.2 Booting Linux
Because XOSL cannot yet boot Linux directly, you need to have Lilo installed in either the boot record of a (Linux) partition, or in the master boot record of an HD other than the first. 

6.2.1 Booting single-kernel Linux systems
As you will notice, when Linux is booted, the Lilo-prompt is still shown. The simplest way to bypass this prompt, and make XOSL boot Linux directly, is to edit the /etc/lilo.conf file, and comment or remove the ‘prompt' line. Now the Lilo prompt will not be shown anymore, and the first item will be booted directly. 

6.2.2 Booting multi-kernel Linux systems
By default, Lilo will drain the keyboard buffer on start-up. This way it will not be possible to let XOSL control Lilo through the Additional Keys feature. To make XOSL control Lilo, you have to re-compile Lilo, with NODRAIN defined. This can be done as following: 

Edit the Makefile and find the CONFIG line. This line will look something like:
CONFIG=-DIGNORECASE -DVARSETUP -DREWRITE_TABLE 
Add -DNODRAIN to the CONFIG line. 
Execute ‘make' 
Replace the existing boot.b (most likely located in /boot/) with the new one. 
Execute ‘lilo' 

If, for instance, you have two options defined in /etc/lilo.conf: LinuxNew and LinuxOld, you can now make XOSL boot these options by defining as additional keys: L.i.n.u.x.N.e.w.ret and L.i.n.u.x.O.l.d.ret respectively. 

NOTE: make sure ‘prompt' is present in /etc/lilo.conf, or else the first item will be automatically booted. 

NOTE: this solution of course also works for a single-kernel system.[/I][/FONT]

In my humble opinion, this means that the workaround I suggested is probably better - to point XOSL at the "Linux Native" partition, then change the configuration of Grub to show or not so whatever the user wants to show - in my case, auto-boot it with 0 or else very small timings - and hide the other (non-Linux) OSs which XOSL is already taking care of.

To answer the question of "why use XOSL at all?" - well, for two main reasons:

1. Anyone who has already handled the installation of multiple-versions of Windows can already handle the changes, reinstallation etc of XOSL to replace the Windows bootloaders. Why learn a new loader and its foibles when you can throw the old one around without problems?

2. For other users of machines that I set up, a graphical (pretty?) boot loader WHICH NEVER SEEMS TO CHANGE when new OSs are installed or old ones updates or extra ones added is a darned useful thing to have. If Grub had been around way back in the dark ages, it might have been the one I used, but I haven't seen much pretty about it yet so maybe not :D Just kidding.

Back to testing the OS rather than probing its boot sequence. Thanks for the help.

---

### Post by macogw on 2007-03-23
> **brit0n said:**
> 

2. For other users of machines that I set up, a graphical (pretty?) boot loader WHICH NEVER SEEMS TO CHANGE when new OSs are installed or old ones updates or extra ones added is a darned useful thing to have. If Grub had been around way back in the dark ages, it might have been the one I used, but I haven't seen much pretty about it yet so maybe not :D Just kidding.

Back to testing the OS rather than probing its boot sequence. Thanks for the help.

You can always turn the pretty colors on ;)

---

### Post by dfreer on 2007-03-23
Not only that but you *can* set a background image, [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) has a how-to I believe :)

---

### Post by brit0n on 2007-04-16
Thanks for all the great info. I hadn't realised that Grub sits in the partition so it remains when I put XOSL back in charge (as I have to for any Windows install). When i point XOSL at the partition, Grub collects the pointer and does what it needs to do. All great.

I am not sure that I need to put Grub front end for other users as I can set it to move on unless I go and manually change tha setting. I also don't know that Grub handles the disk number which stupid FAT32 needs. If you want to boot from a FAT32 partition, Windows expects the disk number to be 128 which is normally on HD0 (hda). XOSL handles that so I am done and it is all great. Someday, I'll look at Grub and LILO more closely but for now I have plenty of Linux stuff to study! (And I am trying to appear less critical - I love the idea of Linux, but I became the standard "well-intentioned troll" by mistake).

Thanks.

---

