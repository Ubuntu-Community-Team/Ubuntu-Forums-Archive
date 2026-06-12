---
title: "How to install shockwave and flash into firefox on Ubuntu PPC ?"
date: 2008-03-16
forum: Apple PPC Users
---

### Post by spystyle on 2008-03-16
Hello from Maine, USA.

This is my first Linux experience, excluding "live CDs"

I was given (2) Imac G3 (the CRT with built in computer) and researched what OS can run FireFox and OpenOffice on it, which brought me to Ubuntu, I installed it successfully - it appears to have detected all hardware, I am using it to type this message :)

But I can not install Adobe Flash and Shockwave, I will need this to have the full FireFox experience, and my daughter will need it to play games like NickJr and ClubPenguin, not to mention YouTube.

1. So.. How can I install Flash and Shockwave?

2. Also, how do I set the resolution to 800x600 ? I can't get the dropdown menu to show anything but 1024x768 (in : system/pref/screen res)

3. Lastly, is there a way to speed Ubuntu up?

Thank you,
Craig

---

### Post by spystyle on 2008-03-16
Hey I did some searching:

1. No Flash for PPC Linux, use Gnash

----------------------------------------------------------------------
from the FAQ, [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
----------------------------------------------------------------------
Flash, Flash video and Gnash

There is no Adobe Flash for PowerPC Linux but there is a free open source project named Gnash as an alternative.
Feisty

Feisty includes Gnash 0.7.2, however there has been a recent major update to Gnash. We recommended that you install the new 0.8.0 version which plays youtube.com, lulu.tv, revision3.com, and perhaps other video in the browser. Gnash 0.8.0 is also more compatible with Flash webpages in general.

To install Gnash 0.8.0, you must enable Feisty Backports.

Go to Applications>Add/Remove>Preferences>

Updates> Check 'unsupported updates' Feisty Backports

Close and reload if it asks. Now search in Add/Remove for gnash and install Gnash 0.8.0.

---

### Post by spystyle on 2008-03-16
Oh h3ll I give up, I installed Gnash 0.8.0 and still firefox won't display youtube and clubpenguin.

I tried restarting and also went to reinstall (to maker sure I really did install it)

*sigh*

---------------------------

4. Is there a way to set it up so I don't have to type username and password at each startup?

---

### Post by ristosu on 2008-03-16
2. Is it the older (tray-loading) or newer (slot-loding) model? At least the slot-loaders are very picky about the horizontal scan frequency; it must be around 60 KHz.  Otherwise the screen remains black. This corresponds to 75 (1024x768), 95 (800x600), and 117 (640x480) Hz vertical frequency. So, you should take a look at /etc/X11/xorg.conf and set HorizSync to 58-62 and VertRefresh to 75-117. Check also that the Screen section contains Modes "1024x768" "800x600" "640x480".

---

### Post by ristosu on 2008-03-16
1. There is another possibility: swfdec-mozilla. I cannot promise it will work, but it may be worth a try. Looks to me like these free flash players are still a bit behind.

---

### Post by stream303 on 2008-03-16
With your backports enabled, you'll probably want to install

youtube-dl

as well.

---

### Post by BladeMelbourne on 2008-03-16
You can also get the "DownloadHelper" plugin for Firefox at their add-ons site.
Apparently it works with many sites, not just YouTube. Unfortunately it doesn't work on some popular ones that appear on Digg Video.

Also ensure you have VLC (videolan client) installed so you can play the FLV (flash video) files you download.

---

### Post by spystyle on 2008-03-16
Thanks for all the replies fellas, I will follow your advice :)

I have another question, this one should be easy.

In reference to jy query about making Ubuntu faster, I did some reading and came up with Xubuntu. So I downloaded and went to install it but it gave an error, Xubuntu did not want to overwrite Ubuntu and gave an error about "ext 3" por something, it lead me to belive that the Ubuntu partition was write protected.

How do I delete Ubuntu so I can install Xubuntu?

Thank you,
Craig

---

### Post by spystyle on 2008-03-16
> **ristosu said:**
> 2. Is it the older (tray-loading) or newer (slot-loding) model? At least the slot-loaders are very picky about the horizontal scan frequency; it must be around 60 KHz.  Otherwise the screen remains black. This corresponds to 75 (1024x768), 95 (800x600), and 117 (640x480) Hz vertical frequency. So, you should take a look at /etc/X11/xorg.conf and set HorizSync to 58-62 and VertRefresh to 75-117. Check also that the Screen section contains Modes "1024x768" "800x600" "640x480".

It is a slot loading imac G3, as far as I know. To be quite honest it's my first experience with a Mac, I am really savvy with building and fixing Windows PCs, but know nothing of Macs or Linux.

It looks like this:

[IMG]http://bestyardsaleever.files.wordpress.com/2007/06/bondi-blue-imac-g3.jpg[/IMG] 

and the bottom reads M5521, using that I Googled the specs and apparently it's 400mhz, I know the hard drive is 10GB. I don't know how to check the amount of RAM.

Thanks,
Craig

---

### Post by 3rdalbum on 2008-03-17
You could try installing Miro (formerly known as Democracy Player) in order to search Youtube.

---

### Post by stream303 on 2008-03-17
> **spystyle said:**
> and the bottom reads M5521, using that I Googled the specs and apparently it's 400mhz, I know the hard drive is 10GB. I don't know how to check the amount of RAM.

When you boot the install cd, at the boot: prompt, type rescue

This will eventually get you to a shell and you can issue
```
free -m
```

and look at the total amount of memory in megabytes.  My quick search showed that this machine came with 64mb of memory.  You'll probably want more, although depending on your needs, you could do a very minimal server install and install just enough X and a simple window manager for a simple cli-type environment.

If you have more ram than that,  I think you'll have the best results with the "alternate" installers, rather than the desktop live-cd.

---

### Post by spystyle on 2008-03-17
Well, after some reading it seems like I'd be better off with Mac OS 9  and iCab web browser, which apparently can have flash.

So, as I said this is my first experience with Mac and Linux, but I am a PC/Windows tech of over 10 years.

*Here is what I dislike so far:*

Ubuntu makes me "log in" every time I boot, this level of security is not practical for many environments.

Ubuntu claims the hard drive has not been scanned in 43000 days or something like that and scans it for several mins at every boot.

Ubuntu does not let me change the res to 800x600 easily.

Ubuntu does not display the amount of RAM in a easy to view way like Windows does. (as far as I know)

Ubuntu's web browser is not up to par "out of the box"

I am not able to format the Ubuntu partition with the Xubuntu installer easily, it appears as if it's write protected or something.

*What I like about Ubuntu:*  

It's "add / remove" feature is really neat! 

It's interface is very intuitive

Ubuntu seemed to recognize all hardware in the G3, I was impressed that no additional drivers were required.

---------------------------

Is there any way to benchmark one Linux against another?

Is there any way to benchmark Linux against Mac OS 9 ?

Cheers,
Craig

---

### Post by ristosu on 2008-03-17
It is a slot-loader, looks like the original 350 MHz model, with 6 GB HD and without firewire. AFAIK, all 400 Mhz models with 10 GB HD did have firewire connectors between analog audio and modem. Someone has probably replaced some parts.

I'm not sure, but I think some kind of auto-login should be available on Ubuntu. Look at the administrative menus.

That 43000 days makes me suspect that the battery on your iMac is empty and it looses the time when it's been shut off. Unfortunately, replacing the battery requires opening the case.

I think that when you've done the necessary changes to /etc/X11/xorg.conf, changing the resolution should work easily.

I cannot imagine a better way of viewing the amount of RAM than 'free -m'. (It's the first value that gives the total amount. And it's very easy to see the usage as well.) Mac OS and Mac OS X are both ok (intuitive), but Windows is hopeless, at least I have not learned to find that information.

I agree about the browser. Maybe the problem is more web itself, but I have not seen any OS where the browser always works a expected.

That write protection thing sounds strange, maybe a bug.

BTW, depending on the amount of RAM, I see no reason why you couldn't run Mac OS X (10.3 or 10.4) on your iMac. And adding RAM is not difficult, 2 modules á 128 MB is enough, and won't cost much. Before trying to install OS X, you should check that your firmware is up-to-date. You will need to install OS 9 to update it.

The amount of RAM can be crucial to Ubuntu's speed as well. How much do you have?

---

### Post by driven1 on 2008-03-17
as far as watching streaming video try

```
sudo apt-get install mozilla-plugin-vlc
```

I use vlc to watch almost any media format.

to get the stand-alone player

```
sudo apt-get install vlc
```

---

### Post by spystyle on 2008-03-17
Thank you for the reply, see below

> **ristosu said:**
> It is a slot-loader, looks like the original 350 MHz model, with 6 GB HD and without firewire. AFAIK, all 400 Mhz models with 10 GB HD did have firewire connectors between analog audio and modem. Someone has probably replaced some parts.

Oops, I should have mentioned that picture was "stock". This iMac has firewire and a 10GB HDD. 

> **ristosu said:**
> I'm not sure, but I think some kind of auto-login should be available on Ubuntu. Look at the administrative menus.

I'll have to look at that, an auto-login would make this comnputer more kid friendly. I intend to fix it up and give it to a kid.

> **ristosu said:**
> That 43000 days makes me suspect that the battery on your iMac is empty and it looses the time when it's been shut off. Unfortunately, replacing the battery requires opening the case.

That's a good deduction! However the computer clock is always correct in desktop...

> **ristosu said:**
> I think that when you've done the necessary changes to /etc/X11/xorg.conf, changing the resolution should work easily.

I'll have to look into that, but since I am a Linux n00b I am like a baby in the woods and don't understand... It's all Greek language to me.

> **ristosu said:**
> I cannot imagine a better way of viewing the amount of RAM than 'free -m'. (It's the first value that gives the total amount. And it's very easy to see the usage as well.) Mac OS and Mac OS X are both ok (intuitive), but Windows is hopeless, at least I have not learned to find that information.

In Windows it is st00pid-easy to view RAM, simply click start > settings > control panel > system and it tells total RAM and CPU speed.

I opened a terminal a typed "free -m", it reports "565 total"

> **ristosu said:**
> I agree about the browser. Maybe the problem is more web itself, but I have not seen any OS where the browser always works a expected.

I find FireFox in Windows to be silly easy, all add-ons are a double click affair.

> **ristosu said:**
> That write protection thing sounds strange, maybe a bug.

I am not able to install Mac OS 9 or Xubuntu over the existing Ubuntu installation...

> **ristosu said:**
> BTW, depending on the amount of RAM, I see no reason why you couldn't run Mac OS X (10.3 or 10.4) on your iMac. And adding RAM is not difficult, 2 modules á 128 MB is enough, and won't cost much. Before trying to install OS X, you should check that your firmware is up-to-date. You will need to install OS 9 to update it.

The amount of RAM can be crucial to Ubuntu's speed as well. How much do you have?

"Total 565" 

Does that translate to (2) 256 MB DIMMS ?

Cheers,
Craig

---

### Post by ristosu on 2008-03-17
There might be an NTP client running on Ubuntu that sets the time from the net.

That 565 sounds like enough, it probably consists of 512 and 64 MB modules. Maybe

```
dmesg | head
```

would tell the truth.

---

### Post by spystyle on 2008-03-17
Hey! I found how to auto-login:

How to auto login in Ubuntu and Xubuntu

This howto does not apply for Kubuntu, which uses KDM, the KDE Display manager.

How to auto-login into your Desktop environment:

    sudo gdmsetup

Select the Security Tab,
Flag the “Enable Automatic Login”,
Select your name from the drop down menu,
Select Close.

From now on your pc wil auto login to your username.

---

### Post by spystyle on 2008-03-17
> **ristosu said:**
> 1. There is another possibility: swfdec-mozilla. I cannot promise it will work, but it may be worth a try. Looks to me like these free flash players are still a bit behind.

I found swfdec-mozilla but when I install it the package manager thing says "error : dependency is not satisfiable : libc6"

I still can not go on Youtube :(

---

### Post by stream303 on 2008-03-17
> **spystyle said:**
> Well, after some reading it seems like I'd be better off with Mac OS 9  and iCab web browser, which apparently can have flash.

Yep, that is a sticking point - all we have right now is to use gnash and youtube-dl if you enable the backports repository in software sources.

> So, as I said this is my first experience with Mac and Linux, but I am a PC/Windows tech of over 10 years.

No problem.  It takes a bit of getting used to.  Just remember that the boys in Cupertino don't do lunch with the Linux developers, so the distros try the best they can at this sometimes quirky hardware. :)

> Ubuntu makes me "log in" every time I boot, this level of security is not practical for many environments.

No sweat.  Just go to System > Administration > Login Window > Security and check "Enable Automatic Login".  At least this is on Gutsy, should be similar on other versions.

> Ubuntu claims the hard drive has not been scanned in 43000 days or something like that and scans it for several mins at every boot.

Sounds like the on-board battery is dead, even though it later gets updated to the right date.  You can get the battery online, or even at Radio Shack part #23-037 I believe.  Should be a Tadiran 3.6v lithium

Check this out for the date problem and funky battery:
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

> Ubuntu does not let me change the res to 800x600 easily.

For the G3's we have to do an intervention. :)  Check your /etc/X11/xorg.conf file and edit it as root temporarily, ie sudo nano /etc/X11/xorg.conf.  This should really help:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

I think the native resolution is 1024x768.  Have you tried running:
```

sudo dpkg-reconfigure xserver-xorg
```

Although you may have already done that.  Those G3's need a little tlc, so you might end up editing manually.  Let's see how far we get..

> Ubuntu's web browser is not up to par "out of the box"

A lighter-weight alternative, yet still based on the Firefox Gecko engine, is Epiphany-browser.  (don't just try to download Epiphany - look for Epiphany-browser)

> I am not able to format the Ubuntu partition with the Xubuntu installer easily, it appears as if it's write protected or something.

Probably running out of free space from your first install.  The easiest way to to reinstall after you do it once, is to blow the whole thing away again, but this time, when you reach the partitioning step, allow the partitioner to use the "whole disk".  I do this routinely on my external firewire drive.  It is rare for a disto to last more than a week. :)

If you like your current partitioning scheme, you could just go in and use manual-partitioning at first, delete the existing ubuntu partitions, then *go-back*, and let guided partitioning take over again.

Hang in there - it'll be worth it.  The big issue is flash, agreed.

---

### Post by ristosu on 2008-03-18
> **spystyle said:**
> I found swfdec-mozilla but when I install it the package manager thing says "error : dependency is not satisfiable : libc6"

I still can not go on Youtube :(

Libc6 should be always there, so it must be the version. Maybe you could try to update the package manager's database. There should be a menu selection for that.

---

### Post by themailman05 on 2008-04-12
> **spystyle said:**
> Thanks for all the replies fellas, I will follow your advice :)

I have another question, this one should be easy.

In reference to jy query about making Ubuntu faster, I did some reading and came up with Xubuntu. So I downloaded and went to install it but it gave an error, Xubuntu did not want to overwrite Ubuntu and gave an error about "ext 3" por something, it lead me to belive that the Ubuntu partition was write protected.

How do I delete Ubuntu so I can install Xubuntu?

Thank you,
Craig

I had the same problem myself. It says "you do not have permission to write to ext3" or something of that nature. I had to srew it and use an altogether different Hdd. Is the one you are using now big or valuable, because i dont have any other info to give you there. all i know is putting a new HDD in works.

---

### Post by i.am.technofreak on 2008-04-12
howdy
dont install xubuntu over ubuntu.  just install xubuntu-desktop in synaptic.  this will give you the option to log into a xfce4 desktop environment, rather that gnome.
technofreak

---

### Post by frankgee57 on 2008-04-13
Why, that's a blueberry iMac.  I have a strawberry-flavored one...

Got a Mac OS install CD for that bad boy?  If so, you could use it to for employing what we olde-time Mac users referred to as "nuke-and-pave," which WILL get rid of the ext3 partition, leaving a Mac partition in its place.  Which will leave you free to install Xubuntu.

Good luck!

---

### Post by ssam on 2008-04-13
hardy has a youtube plugin in totem (Movie player in the menu). this has better search than miro.

you have to enable the plugin in the edit menu, and the first time you use it it will take you though installing the needed codecs.

---

