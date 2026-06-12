---
title: "Convert Ubuntu to Xubuntu"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-09-21
I installed Ubuntu Feisty on an old Gateway all in one desktop.  The computer has 256 meg ram, and just seems rather sluggish.  I can't add memory to this.  So I want to convert to Xubuntu in hopes of improving performance.  I downloaded and installed Xubuntu-desktop through Synaptic.  Somewhere in these forums somebody mentioned about session editor to have it run Xubuntu when I boot, but I don't know how to do that.  Can I just uninstall Ubuntu-desktop through Synaptic?  Would it then default to Xubuntu?

---

### Post by Wiebelhaus on 2007-09-21
Just install clean is my advice , I've tried it and it really messes stuff up.

But to answer your question...


> sudo aptitude update && sudo aptitude install xubuntu-desktop

---

### Post by oilchangeguy on 2007-09-21
> **dndrich said:**
> I installed Ubuntu Feisty on an old Gateway all in one desktop.  The computer has 256 meg ram, and just seems rather sluggish.  I can't add memory to this.  So I want to convert to Xubuntu in hopes of improving performance.  I downloaded and installed Xubuntu-desktop through Synaptic.  Somewhere in these forums somebody mentioned about session editor to have it run Xubuntu when I boot, but I don't know how to do that.  Can I just uninstall Ubuntu-desktop through Synaptic?  Would it then default to Xubuntu?

why make life hard? just create an xubuntu cd and do a freash install.

---

### Post by overdrank on 2007-09-21
> **dndrich said:**
> I installed Ubuntu Feisty on an old Gateway all in one desktop.  The computer has 256 meg ram, and just seems rather sluggish.  I can't add memory to this.  So I want to convert to Xubuntu in hopes of improving performance.  I downloaded and installed Xubuntu-desktop through Synaptic.  Somewhere in these forums somebody mentioned about session editor to have it run Xubuntu when I boot, but I don't know how to do that.  Can I just uninstall Ubuntu-desktop through Synaptic?  Would it then default to Xubuntu?

Hi if you will just log out and then at the login screen in the lower left hand corner select xfce as session then enter user name and password and there you go. :popcorn:

---

### Post by dndrich on 2007-09-21
I have the computer with an automatic login.  So, do I need to re-enable the login in order to do that?

---

### Post by oilchangeguy on 2007-09-21
> **overdrank said:**
> Hi if you will just log out and then at the login screen in the lower left hand corner select xfce as session then enter user name and password and there you go. :popcorn:

this is not a downgrade. it's just running an xubuntu desktop, on ubuntu. this will not solve the users problem. a clean install of xubuntu will.

---

### Post by Wiebelhaus on 2007-09-21
> **oilchangeguy said:**
> this is not a downgrade. it's just running an xubuntu desktop, on ubuntu. this will not solve the users problem. a clean install of xubuntu will.

You feel that a clean install of whatever desktop you want is the only way to achieve the desired effect? Please explain , I'm not trying to argue - I'm interested in hearing your opinion.

---

### Post by st33med on 2007-09-21
If you want to keep GNOME and all your files, just do this:
```
sudo apt-get install xfce4
```
Change your session and log in.

Yes, you can have multiple WMs.

---

### Post by Mud.Knee.Havoc on 2007-09-21
> **sx66gns said:**
> You feel that a clean install of whatever desktop you want is the only way to achieve the desired effect? Please explain , I'm not trying to argue - I'm interested in hearing your opinion.

I also want in on this. :)  I would also like to make it very clear that I'm not trying to argue either - I'm honestly interested in learning about how a clean Xubuntu install performs better than an Ubuntu install logged in with XFCE.

---

### Post by oilchangeguy on 2007-09-22
> **Mud.Knee.Havoc said:**
> I also want in on this. :)  I would also like to make it very clear that I'm not trying to argue either - I'm honestly interested in learning about how a clean Xubuntu install performs better than an Ubuntu install logged in with XFCE.

because the op has explained that installing ubuntu is causing his/her computer to run slow. the advise the user has been given is to install xfce, on top of ubuntu. this changes nothing. it's still ubuntu under the skin, just dressed up to look like xubuntu. the computers performance will not be affected. which is what the user is trying to achive, a faster computer. and the only way to do this is to use an os that requires less system resources, not by simply changing the way ubuntu looks. if i'm wrong about this, please let me know. it just seems logical, to downgrade the os you do a clean install, not reskin it.

---

### Post by whistlingtony on 2007-09-22
_Installing_ Ubuntu didn't make the computer run slow. 
_Running_ Ubuntu (Gnome really) is making the computer run slow.

Picking XFCE at the desktop manager should load all the XFCE libraries and such. He installed Xubuntu-desktop. That loads its own window manager and background stuff. Gnome is not running in the background. There should be no slowdown. Having Ubuntu-desktop stuff installed but not running should not impact the user beside taking up some disk space.

Xubuntu-desktop is not Gnome dressed up (or down if you prefer). It IS XFCE dressed up to look all... Ubuntu-y. Yeah.

---

### Post by Mud.Knee.Havoc on 2007-09-22
> **oilchangeguy said:**
> because the op has explained that installing ubuntu is causing his/her computer to run slow. the advise the user has been given is to install xfce, on top of ubuntu. this changes nothing. it's still ubuntu under the skin, just dressed up to look like xubuntu. the computers performance will not be affected. which is what the user is trying to achive, a faster computer. and the only way to do this is to use an os that requires less system resources, not by simply changing the way ubuntu looks. if i'm wrong about this, please let me know. it just seems logical, to downgrade the os you do a clean install, not reskin it.

This doesn't seem right to me.  Both Xubuntu and Ubuntu should have the same guts.  The OS is the same in either case.

---

### Post by Wiebelhaus on 2007-09-22
it would be nice if this got more attention , I'd really like to find an absolute as to which school of thought is correct.

---

### Post by dndrich on 2007-09-22
OK, I'm the guy that asked the original question.  I will probably do a clean install for the heck of it, since there is nothing on this computer, and it is used just for internet access.  But I bet that Ubuntu and Xubuntu are the same "under the hood" so to speak.  That is, they are running the same version of Linux, Debian.  Xubuntu uses a lighter desktop manager, or shell if you will, than Ubuntu.  So I would bet that the posters who claim that if I log in using XFCE, performance will be better.  Does anybody know the answer to this?  I thought that was the main difference between the Ubuntus, was simply the desktop manager.

---

### Post by Wiebelhaus on 2007-09-22
> **dndrich said:**
> OK, I'm the guy that asked the original question.  I will probably do a clean install for the heck of it, since there is nothing on this computer, and it is used just for internet access.  But I bet that Ubuntu and Xubuntu are the same "under the hood" so to speak.  That is, they are running the same version of Linux, Debian.  Xubuntu uses a lighter desktop manager, or shell if you will, than Ubuntu.  So I would bet that the posters who claim that if I log in using XFCE, performance will be better.  Does anybody know the answer to this?  I thought that was the main difference between the Ubuntus, was simply the desktop manager.

Maybe altering the title to reflect where this conversation has gone would increase the amount of attention this thread deserves?

---

### Post by rsambuca on 2007-09-22
Gnome is a heavier desktop environment than xfce.  As such, there are more libraries that need to be loaded in to memory in order for it to run.

If you select xfce at the gdm login screen, then the xfce desktop is loaded, and all of the extra gnome libraries are not, so you machine should run quicker if it has low resources.

The big however, is that as soon as you start running certain programs that require the full set of gnome libraries, your system will slow down as if it were running ubuntu.  It is critical for system performance on low resource machines that you do not run a bunch of programs requiring mixed set of libraries.  ie.  Don't run amarok on xubuntu, or you will have to load the kde/QT libraries.

---

### Post by ravenwere on 2007-09-23
I would agree with rsambuca. You do not only have to look at the windows manager but also what applications you need or want to run.

As a guide look at some of the minimal Linux installations such as DSL (Damn Small Linux) and Puppy Linux. Check out the applications they install as default.

Its no good installing openoffice in that environment and wondering why your machine grinds to a halt.

If you want to stick with an ubuntu distribution then xubuntu is the way to go but use the default applications that are suited to lower performance PC's.

---

### Post by kapkevin on 2007-09-23
Just my observations as a Newbie installing Ubuntu trying to decide if I should purchase a new desktop with Linux, Windows or purchase an Apple.

I started off with Ubuntu on a 256MB PC. Ran like a dog. So, I download the KDE environment using Synaptic package manager and started up in the KDE environment. It runs a lot, lot faster. Now, I'm going to try downloading and installing the XFCE environment for evaluation.

My first impressions of Linux (under Gnome)  was "I thought it was suppose to work on low spec machines. This is terrible". However, the performance under KDE has made Linux a viable desktop alternative. I'm hoping to be further convinced by XFCE. 

So, one Ubuntu install, two environment installs. My opinion based on these observations - it doesn't matter if you start off with Ubuntu and then install the KDE environment, the core/guts are still the same.  The performance issues seem to be in the environment and not the core. Same hardware, same Ubuntu, difference desktop environment, difference performance. 

In both cases, OpenOffice runs like a dog on my limited hardware. I've moved to KOffice because of the better user experience. OpenOffice may be a great piece of software with lots of functionality but I don't want to wait 2 minutes for software to start up.

---

### Post by t4thfavor on 2007-09-24
I have the same issues, I run a pIII 500 with 384Megs of RAM. It ran like crap with ubuntu, runs slightly slower under kubuntu, and I haven't tried xubuntu. My question is can one remove ubuntu (gnome based environment) in favor of kubuntu, or is there always going to be some ubuntu left inside there?

I don't do much with it, Email, web browse, etc. But i did notice that while running kde, there are gnome processes running in the background. My goal is to get rid of those processes to free some resources.

---

### Post by overdrank on 2007-09-24
> **t4thfavor said:**
> I have the same issues, I run a pIII 500 with 384Megs of RAM. It ran like crap with ubuntu, runs slightly slower under kubuntu, and I haven't tried xubuntu. My question is can one remove ubuntu (gnome based environment) in favor of kubuntu, or is there always going to be some ubuntu left inside there?

I don't do much with it, Email, web browse, etc. But i did notice that while running kde, there are gnome processes running in the background. My goal is to get rid of those processes to free some resources.

Hi maybe this link will help, and yes you can remove gnome or kde or Xfce. 
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by djchandler on 2007-09-24
If your computer is that sluggish, maybe you ought to consider another distribution. Damn Small Linux is made just for your purpose.

---

### Post by reset3x on 2007-09-24
You may also want to check out antiX... antiX uses fluxbox and works quite well in my P2-450 w/256

Home: [http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

Forum: [http://antix.freeforums.org/](http://antix.freeforums.org/)

Peace!!

---

### Post by t4thfavor on 2007-09-24
This one would work for my situation
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Cause I like KDE and can put up with mild slowness. 

The only problem is that I did not realize that gaim, and evolution were Gnome only(requiring the gdm libs). I also forgot that I had apache2, and mySql running from when I tested out phpbb2 :) removing them seemed to help. Also using the Konquerer browser would probably help reduce some of this firefox-memoryfootprint-hog.

Thats about what it runs at most of the time.
5545 chance    15   0  179m  78m  26m S  8.6 20.7  13:12.41 firefox-bin

---

### Post by RedSquirrel on 2007-09-25
In my opinion, the best way to a light system with Ubuntu is to install the base system and build up from there:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)

As mentioned above, try not to add applications that are linked to a particular desktop environment or you'll end up loading libraries that come with that desktop environment. Have a look at the dependencies of programs before you install them. 

For example, if you're trying to keep things as light as possible and you see the words "gnome" or even "xfce" in the list of dependencies of a particular program, you might want to think twice before installing it. ;)

---

### Post by PhilJ on 2007-09-25
What about an Xubuntu install then using icewm or fluxbox is that any faster/quicker? Are there any benefits to this?    Philj

---

### Post by dptxp on 2007-09-25
With 256 MB RAM, a clean install of Xubuntu seems the best option to me.
Puppy, if suits, shall be one of the fastest. But then he can run Puppy from Live CD too
with other OS installed.

---

### Post by t4thfavor on 2007-09-25
Note that I stopped using Firefox for anything but youtube, and I have a much more responsive system. Now if I could just get my hands on some cheap pc100x512MB I would be in heaven.

---

### Post by RedSquirrel on 2007-09-25
> **PhilJ said:**
> What about an Xubuntu install then using icewm or fluxbox is that any faster/quicker? Are there any benefits to this?    Philj
Sure, that would be OK. It wouldn't be quite as fast or as small in size as a minimal installation.

The advantage, though, is that you get the work done for you: you don't have to hunt around for applications to install, you just get the ones Xubuntu has picked for you. For someone who needs to get used to Ubuntu (and linux in general) this might be a good way to go. (Which isn't to say that installing a minimal system and building up from there is all that hard, but maybe some people wouldn't be up for it (yet).)

Some time ago, I had Xubuntu installed and I used Fluxbox. It was quite a nice setup. For the past while I have been using minimal installations, which are just a little better. ;)

I would advise installing Xubuntu from a CD on a blank hard drive (or partition) rather than installing xubuntu-desktop on top of GNOME. That way, you are assured that you're only running the services that Xubuntu needs.

I've heard that Xubuntu is going to start including some GNOME applications in the future, which is certainly moving farther away from their goal of providing an Ubuntu distribution for older systems. Having said that, the current Xubuntu isn't really super-light by any means.

Another option is to do the minimal installation and then install the **xfce4 **metapackage. That installs the core of Xfce and then you can pick your applications later.

---

### Post by PhilJ on 2007-09-25
Thanks for the info RedSquirrel,  thats what I have now, xubuntu clean install and icewm / fluxbox as options
 Philj
 Athlon 2.2G 392Meg  ddr 80g hd Fiesty
 also on   
athlon 1.4 G 512Meg 40gig hd Fiesty

---

### Post by RedSquirrel on 2007-09-25
> **PhilJ said:**
> Thanks for the info RedSquirrel,  thats what I have now, xubuntu clean install and icewm / fluxbox as options

You're welcome. Have fun. :)

---

