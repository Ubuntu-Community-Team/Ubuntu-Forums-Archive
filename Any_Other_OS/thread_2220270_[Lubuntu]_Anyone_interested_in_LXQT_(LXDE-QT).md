---
title: "[Lubuntu] Anyone interested in LXQT (LXDE-QT)?"
date: 2014-04-27
forum: Any Other OS
---

### Post by ibjsb4 on 2014-04-27
[http://lxqt.org/](http://lxqt.org/)

If there is an community interest in this, maybe a mega-thread could be started.

[COLOR=#ff0000]EDIT[/COLOR]

Anyone needing help with LXQT, no matter what skill level you are, please post here.

---

### Post by vasa1 on 2014-04-27
I'm interested because this is the future of Lubuntu, AFAICT. Why don't you just post here for now?

---

### Post by sudodus on 2014-04-27
> **vasa1 said:**
> I'm interested because this is the future of Lubuntu, AFAICT. Why don't you just post here for now?
+1

---

### Post by Iowan on 2014-04-27
> **vasa1 said:**
> Why don't you just post here for now?

> Forum: Forum Feedback & Help

Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.Is it a forum-related problem?

---

### Post by vasa1 on 2014-04-27
> **Iowan said:**
> Is it a forum-related problem?
**Oops**! I should have said just have a regular thread (rather than a "mega" one).

---

### Post by ibjsb4 on 2014-04-27
> **Iowan said:**
> Is it a forum-related problem?

I was thinking about the cafe, should of went with the cafe :D

How bout moving it somewhere more better :)

Be nice to be able to tag it.

---

### Post by Elfy on 2014-04-27
*Thread moved to **Other OS/Distro Support**.*

---

### Post by ibjsb4 on 2014-04-27
Duh, no wonder you make the big bucks :)

---

### Post by ibjsb4 on 2014-04-27
> **vasa1 said:**
> I'm interested because this is the future of Lubuntu, AFAICT. Why don't you just post here for now?

Yes, my interest too.  Lu; Ku; Razor, all working together sounds real good to me.

---

### Post by vasa1 on 2014-04-27
So as it stands, if someone wants to use Firefox (or Chrome/Chromium) and LibreOffice, then a bunch of gtk stuff will come along.

---

### Post by ibjsb4 on 2014-04-27
> **vasa1 said:**
> So as it stands, if someone wants to use Firefox (or Chrome/Chromium) and LibreOffice, then a bunch of gtk stuff will come along.

Yes, this is a very young project with many hurdles ahead.  Right now I'm waiting for a release of 14o4.  A working version of 13.10 is available.

---

### Post by vasa1 on 2014-05-03
Long reddit thread on qt: [http://www.reddit.com/r/linux/comments/18bk2u/why_do_so_many_big_applications_like_firefox_and/](http://www.reddit.com/r/linux/comments/18bk2u/why_do_so_many_big_applications_like_firefox_and/)

---

### Post by ibjsb4 on 2014-05-05
Well, I got myself on some mailing list and sign up to a few bogs.  The developer chat is mostly over my head, but there seems to be a push going on with QT5.

I have humbly asked about lxqt 14o4 in a few locations, but no reply.

---

### Post by vasa1 on 2014-05-08
[Next-Gen Linux Desktop LXQt Makes First Public Release]("http://www.omgubuntu.co.uk/2014/05/next-gen-linux-desktop-lxqt-makes-first-public-release")
:)

[http://lxqt.org/](http://lxqt.org/)

I get rather high CPU usage on lxqt.org :(

---

### Post by ibjsb4 on 2014-05-08
> **vasa1 said:**
> I get rather high CPU usage on lxqt.org :(

Yes, I have seen other reports of this.

Seems that the compton-conf package is now resolved (fingers crossed) and is ready for testing.

Thanks for the heads up :)

---

### Post by ibjsb4 on 2014-05-08
For those interested, a package discription and other stuff is located here.

[http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/dists/trusty/main/binary-amd64/Packages)

---

### Post by ibjsb4 on 2014-05-08
OK :) Build #1
Installed lubuntu daily build and lxqt-metapackage.  A 700M+ install.  It booted right up and to my amazement, works nicely so far.  Running it in virtualbox, one processor and 1G ram.

Build #2 A lxqt addition on a existing lxde install.  This is NOT a VM, but on a physical partition.  On one 12 year old P4 and half a gig of ram.

This build is using startx.
I want to get startx working instead of lightdm.

I have tried both 
~/.xinitrc>  exec lxqt-session 
and 
exec startlxqt  

Both exist in /usr/bin 
Both come back with 'invalid argument'

---

### Post by vasa1 on 2014-05-08
> **ibjsb4 said:**
> OK :) Build #1
Installed lubuntu daily build and lxqt-metapackage.  A 700M+ install. ...
What was "700M+"? The distro plus the ppa or just the ppa? Sorry, but it isn't clear to me.

---

### Post by ibjsb4 on 2014-05-08
> **vasa1 said:**
> What was "700M+"? The distro plus the ppa or just the ppa? Sorry, but it isn't clear to me.

Hi vasa1 :)

I first installed a CLI (terminal only install) using the mini iso.

Then I manually installed the PPA to software sources (and updated) and then with one command

```
sudo apt-get install lxqt-metapackage
```
And then received the 700M+ install.

---

### Post by vasa1 on 2014-05-08
Okay, so part of the 700M+ would be going from mini.iso to vanilla Lubuntu and the rest maybe be due to the lxqt package?
Did you have things like Abiword, Pidgin, Sylpheed, etc installed during the process?
I'm curious because the OMG article has this:> A number of Qt dependencies will be pulled in as part of the installation process. Those wrestling with a particularly pathetic internet connection should plan accordingly.

---

### Post by ibjsb4 on 2014-05-08
> [COLOR=#000000]Okay, so part of the 700M+ would be going from mini.iso to vanilla Lubuntu and the rest maybe be due to the lxqt package?[/COLOR]
[COLOR=#000000]Did you have things like Abiword, Pidgin, Sylpheed, etc installed during the process?[/COLOR]

I will post a list tomorrow.

> [COLOR=#000000]*A number of Qt dependencies will be pulled in as part of the installation process. Those wrestling with a particularly pathetic internet connection should plan accordingly.*[/COLOR]

This install is done over the internet.  I recommend fast internet.

---

### Post by sudodus on 2014-05-09
> **ibjsb4 said:**
> OK :) Build #1
Installed lubuntu daily build and lxqt-metapackage.  A 700M+ install.  It booted right up and to my amazement, works nicely so far.  Running it in virtualbox, one processor and 1G ram.

Build #2 A lxqt addition on a existing lxde install.  This is NOT a VM, but on a physical partition.  On one 12 year old P4 and half a gig of ram.

This build is using startx.
I want to get startx working instead of lightdm.

I have tried both 
~/.xinitrc>  exec lxqt-session 
and 
exec startlxqt  

Both exist in /usr/bin 
Both come back with 'invalid argument'

Maybe this post (and some other posts in the same thread) is interesting

[http://ubuntuforums.org/showthread.php?t=2222849&p=13018219#post13018219](http://ubuntuforums.org/showthread.php?t=2222849&p=13018219#post13018219)

---

### Post by vasa1 on 2014-05-09
I installed the daily ppa ([https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily](https://launchpad.net/~lubuntu-dev/+archive/lubuntu-daily)) and now am installing lxqt-metapackage from there.```
0 upgraded, 81 newly installed, 0 to remove and 18 not upgraded.
Need to get 59.7 MB of archives.
After this operation, 164 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```
I don't understand (or like) the **18 not upgraded** and if you guys never hear from me again you know why.

---

### Post by vasa1 on 2014-05-09
I installed everything, and did an apt-get update/upgrade for good measure and this time saw that two packages, gpicview and pcmanfm, "have been kept back". Anyway, did the upgrade and rebooted.

At the login screen, I got the lxqt-desktop option but logging into that just returns me to the login screen again :(

So now I'm writing this from the regular Lubuntu session.

---

### Post by vasa1 on 2014-05-09
BTW, I also got this:```
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up elementary-icon-theme (2.7.1-0ubuntu6) ...
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/elementary
Setting up qtcore4-l10n (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Setting up libqtcore4:amd64 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
```
After another apt-get update/upgrade, gpicview has been updated and 
```
The following NEW packages will be installed:
  libjpeg62
```
pcmanfm is still being held back.

---

### Post by vasa1 on 2014-05-09
I see something called *JuffEd text editor* which is described as an *Advanced text editor* but I get:
```
[01:01 PM] ~ $ juffed
juffed: error while loading shared libraries: libjuff.so.0.9: cannot open shared object file: No such file or directory
[01:01 PM] ~ $ 

```Maybe it would only work in the lxqt session?

---

### Post by ibjsb4 on 2014-05-09
> Maybe this post (and some other posts in the same thread) is interesting
Thanks sudodus.  I have not yet tried to boot with ~/.xsession, but will look into that today.

@vasa1
You can't boot, I can't boot. And we are set up in similar sutuations. You with Lu and me with lxde.  Makes me wonder if something else is going on.  This is going to take some research.  Let you know what I find :)

Pcmanfm, the ppa was updated 5 hours ago.

---

### Post by vasa1 on 2014-05-09
I don't know if this is material or not but this is what I see in */usr/share/xsessions*:
```
[07:16 PM] /usr/share/xsessions $ ll
total 32
drwxr-xr-x   2 root root  4096 May  9 11:46 ./
drwxr-xr-x 231 root root 12288 May  9 11:46 ../
-rw-r--r--   1 root root   385 Nov  1  2013 Lubuntu.desktop
-rw-r--r--   1 root root   238 Nov  1  2013 Lubuntu-Netbook.desktop
-rw-r--r--   1 root root    98 May  8 04:49 lxqt.desktop
-rw-r--r--   1 root root   198 Dec 22 16:56 openbox.desktop
[07:16 PM] /usr/share/xsessions $ 
```
Then I looked at lxqt.desktop:
```
[Desktop Entry]
Type=Application
Exec=startlxqt
Name=LXQt Desktop
Comment=Lightweight Qt Desktop
```Very brief. Especially the **Exec=startlxqt** line.

The other .desktop files in that folder have longer **Exec= lines**:
Lubuntu: *Exec=/usr/bin/lxsession -s Lubuntu -e LXDE*
Openbox: *Exec=/usr/bin/openbox-session* and *TryExec=/usr/bin/openbox-session*
Lubuntu Netbook: *Exec=/usr/bin/lxsession -s Lubuntu-Netbook -e LXDE*

So I'm wondering ...

By the way, if your intention is to keep this thread about Lubuntu, why not ask the mods to move it to *Desktop Environments*?

---

### Post by vasa1 on 2014-05-09
I made a longer Exec= line but with the same result:
```
[Desktop Entry]
Type=Application
Exec=/usr/bin/startlxqt
Name=My LXQt Desktop
Comment=Lightweight Qt Desktop
```
Maybe the content of startlxqt has something to do?
```
[09:06 PM] ~ $ cat /usr/bin/startlxqt
#!/bin/sh

if [ -z "$XDG_CONFIG_HOME" ]; then
	export XDG_CONFIG_HOME="$HOME/.config"
fi

# Ensure the existance of the 'Desktop' folder
if [ -e "$XDG_CONFIG_HOME/user-dirs.dirs" ]; then
	. "$XDG_CONFIG_HOME/user-dirs.dirs"
else
	XDG_DESKTOP_DIR="$HOME/Desktop"
fi
mkdir -p "$XDG_DESKTOP_DIR"

# Clean up after GDM (GDM sets the number of desktops to one)
xprop -root -remove _NET_NUMBER_OF_DESKTOPS -remove _NET_DESKTOP_NAMES -remove _NET_CURRENT_DESKTOP 2> /dev/null

# Enable Qt integration for OpenOffice.org, if available.
export SAL_USE_VCLPLUGIN=kde

# Launch DBus if needed
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
	eval "$(dbus-launch --sh-syntax --exit-with-session)"
fi

# load lxqt Qt platform plugin
# FIXME: the plugin is not yet ready
export QT_PLATFORM_PLUGIN=lxqt

export XDG_MENU_PREFIX="lxde-"

export XDG_CURRENT_DESKTOP="LXQt"

# Start the LXQt session
exec lxqt-session
[09:06 PM] ~ $ 

```

---

### Post by vasa1 on 2014-05-10
No joy after today's updates which included lxqt metapackage.

Now there are:
[LIST=1]
[*]LX Games
[*]LXQt Desktop
[*]Lubuntu
[*]Lubuntu Netbook
[*]Lubuntu Nexus 7 session
[*]Lubuntu QT session
[*]Openbox
[/LIST]I tried 2 and 6.

---

### Post by ibjsb4 on 2014-05-10
Yesterday I took the time to compare the above files (and other files relating to startup) between my working and non-working install.  They are both the same.

I can find nothing helpfull on the internet.  I have search razor, lxqt, lxde and lubuntu.  It would seem that we are the only two in the world with this problem :)

I have convinced myself that 'startlxqt' is correct.  What I will now look at is my install method.  I did not use the meta-package on this build in a attempt to avoid gtk.

---

### Post by Tar_Ni on 2014-05-10
I've just looked at their website ,lxQt.org and from the screenshotand at first glance at the desktop it looks more polished than LXDE used to be, it's getting closer to XFCE.

---

### Post by vasa1 on 2014-05-10
Take a look at this closed issue: [https://github.com/lxde/lxde-qt/issues/70](https://github.com/lxde/lxde-qt/issues/70)

First post there mentions **x-0-greeter.log**. See if you can spot anything in /var/log/lightdm. It's all too high for me.

And this comment ([https://github.com/lxde/lxde-qt/issues/70#issuecomment-42523451](https://github.com/lxde/lxde-qt/issues/70#issuecomment-42523451)) talks of having the latest version of libqtxdg. I don't even have that installed.

I think I'll stay with my knitting which is trying to get a higher score at 2048 ;)

---

### Post by ibjsb4 on 2014-05-11
Good find vasa1; your googleFu is strong :)

I have libqtxdg0 and libqtxdg-data 0.5.3 installed on my working install.  Will take a look at my non-working build later.

I am currently on a working install of lxqt that I installed yesterday on my desktop machine.

I would suggest to anyone wanting to install lxqt to do a full (700M) install (on its own partition).  I have two installs working now on different computers.

---

### Post by vasa1 on 2014-05-11
> **ibjsb4 said:**
> ...
I have libqtxdg0 and libqtxdg-data 0.5.3 installed on my working install. ...
I have:```
[07:45 PM] ~ $ apt-cache policy libqtxdg0
libqtxdg0:
  Installed: 0.5.3+bzr111+201405092020~ubuntu14.04.1
  Candidate: 0.5.3+bzr111+201405092020~ubuntu14.04.1
  Version table:
 *** 0.5.3+bzr111+201405092020~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.5.2-4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
[07:45 PM] ~ $ apt-cache policy libqtxdg-data
libqtxdg-data:
  Installed: 0.5.3+bzr111+201405092020~ubuntu14.04.1
  Candidate: 0.5.3+bzr111+201405092020~ubuntu14.04.1
  Version table:
 *** 0.5.3+bzr111+201405092020~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
[07:46 PM] ~ $ 
```
But still no joy. 

Anyway, let's see what happens.
[www.youtube.com/watch?v=WlBiLNN1NhQ](www.youtube.com/watch?v=WlBiLNN1NhQ) ;)

---

### Post by ibjsb4 on 2014-05-11
> But still no joy. Nuts

Maybe you should try it in a virtualbox.

I will also watch your youtube later.  Restricted-extras installed; youtube broke.

Edit:  I am using Qupzilla for a web browser.

---

### Post by vasa1 on 2014-05-11
Meanwhile, please read [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007536.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007536.html)
It looks like 14.10 will still be gtk.

---

### Post by ibjsb4 on 2014-05-11
Excellent reading, thanks for the link.  We are on the bottom basement floor and can only go up from here :D

---

### Post by vasa1 on 2014-05-11
BTW, the Youtube vid is *Always look on the bright side of life*. Nothing to do with LxQt ;)

---

### Post by ibjsb4 on 2014-05-12
There were 15 updates today, all went well.

I have changed things around yet again.

I have my working install and now have lxqt on a lubuntu-core install.  The later install still will not boot from lightdm :(  This is going on the back burner as I just want to play with my working system :)

[COLOR=#ff0000]Edit[/COLOR]
There has been some video glitching going on.  Todays updates seem to have fixed it.  There were a couple of xorg updates installed today, that could of been the fix.

---

### Post by vasa1 on 2014-05-12
Finally got it going!
[https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206](https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206)

---

### Post by ibjsb4 on 2014-05-12
NICE!  I will try this in the morning.

---

### Post by vasa1 on 2014-05-13
> **ibjsb4 said:**
> NICE!  I will try this in the morning.
Now to move the goal posts ;)

One of my obsessions is to have the majority of the screen (including application windows, panels, dropdowns, whatever) dark with light text.

Obviously, my gtk-fu isn't going to be of much use for the qt stuff :(

So if you have some pointers, they'll be most appreciated!

---

### Post by vasa1 on 2014-05-13
I'm looking at [https://github.com/lxde/lxqt-common/blob/master/themes/a-mego/lxqt-panel.qss](https://github.com/lxde/lxqt-common/blob/master/themes/a-mego/lxqt-panel.qss)

Seems promising.

But I want to do it per user and **not system-wide**. The file is here: */usr/share/lxqt/themes/a-mego/lxqt-panel.qss*. If it's possible, where would it go?

*~/.local/share/lxqt/themes/a-mego/lxqt-panel.qss* was suggested but I couldn't get the changes to take effect.

---

### Post by ibjsb4 on 2014-05-13
> **vasa1 said:**
> Now to move the goal posts ;)
One of my obsessions is to have the majority of the screen (including application windows, panels, dropdowns, whatever) dark with light text.
Obviously, my gtk-fu isn't going to be of much use for the qt stuff :(
So if you have some pointers, they'll be most appreciated!

LoL

I am clueless.

I can see my priorities are different from yours :)  Right now I am just a user, but yes I know that a custom desktop is in order.  I think that customizing will change when qt5 comes to play.  Like going from gtk2 to 3, or thats what I'm thinking.

I am seeing what the packages have to offer and what I want them to do.  Right now its a qt4 world with few qt5 packages.

[http://qt-apps.org/](http://qt-apps.org/)

I will reply to your PM later today.  I have some thoughts.

[COLOR=#ff0000]Edit  [/COLOR]There are 21 updates today

---

### Post by sudodus on 2014-05-13
> **vasa1 said:**
> Finally got it going!
[https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206](https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206)


Thanks a lot :KS

It works for me too :-D

See the attached file

---

### Post by vasa1 on 2014-05-13
Hah! Using "Ambiance" solves my problem. I have everything else sorted out. It's just that the default panel (or at least the one I started off with) was too white for my liking.

By the way, does the JuffEd text editor work for anyone using LXQt on Lubuntu?

---

### Post by sudodus on 2014-05-13
Yes, juffed was started by default, when I opened a text file via pcmanfm, and I could edit and save.

---

### Post by vasa1 on 2014-05-13
I get:```
[11:53 PM] ~ $ juffed
juffed: error while loading shared libraries: libjuff.so.0.9: cannot open shared object file: No such file or directory
[11:53 PM] ~ $ 
```

---

### Post by sudodus on 2014-05-13
I noticed that pcmanfm was held back. So an old version is used in my system. Could it be, that juffed works, when called from there.

The computer is busy with other things now, but I will try it from a terminal window later and edit this post.

*Edit*: juffed works also from lxterminal, for example

```
juffed .bashrc
```

*Edit 2*: I installed LXQt in 32-bit Lubuntu

---

### Post by vasa1 on 2014-05-13
Juffed bug: [https://bugs.launchpad.net/ubuntu/+source/juffed/+bug/874479](https://bugs.launchpad.net/ubuntu/+source/juffed/+bug/874479)

---

### Post by ibjsb4 on 2014-05-14
5 updates today, 3 of them were for pcmanfm-qt.

So I fired pcmanfm-qt up and seems to be working fine.

I wanted to use gksudo this morning and installed 'gksu'

When using the gksudo command to open 'synaptic pm' I get
> (gksudo:11761): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failedBut it will still open and is usable.

Gksudo works with pcman-qt (no gconf-critical).

There are old bug reports on this (gksu).  Maybe it is nothing to be concerned about.

---

### Post by parker-hugh on 2014-05-14
Hi, I wonder if you could help me here, I installed LXQt on Ubuntu 14.04 but missing default window manager

intalled LXQt by following commands...

sudo apt-get install software-properties-common
sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
sudo add-apt-repository ppa:gilir/q-project
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lxqt-metapackage
sudo apt-get install lxqt-panel

reboot and click small circle to chose LXQt login option

message displayed:
please select your default window manager
other... chose your favourite one.
you will be able to change this at any time through
Preferences > Session settings > Basic Settings

Unable to select window manager, is system looking for openbox or PCManFM-Qt ? not sure what to do here.

I am completely new to linux so if someone could explain how to fix this I would be grateful. is there an easy command line I can use in the terminal?

any help would be appreciated

---

### Post by sudodus on 2014-05-14
> **vasa1 said:**
> Finally got it going!
[https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206](https://github.com/lxde/lxde-qt/issues/84#issuecomment-42913206)

Since the link above works, you can start with Lubuntu 14.04. Maybe it will also work if you install ***lubuntu-desktop*** at an early stage into Ubuntu, and then follow the instructions above.

> **parker-hugh said:**
> Hi, I wonder if you could help me here, I installed LXQt on Ubuntu 14.04 but missing default window manager

intalled LXQt by following commands...


---

### Post by parker-hugh on 2014-05-14
thanks [**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021") for your prompt reply, I also got a reply from [http://forum.lxde.org](http://forum.lxde.org) where Rex suggested  install the default Window Manager for Lubuntu  (which is Openbox) by following command line....

**sudo apt-get install openbox obconf**

after restart I was able to select LxQt from the login screen.

cheers, Hugh

---

### Post by vasa1 on 2014-05-15
[http://www.linuxbsdos.com/2014/05/14/lxqt-desktop-environment-screenshots/](http://www.linuxbsdos.com/2014/05/14/lxqt-desktop-environment-screenshots/)

---

### Post by vasa1 on 2014-05-15
Interesting thread here: [https://bbs.archlinux.org/viewtopic.php?id=181207](https://bbs.archlinux.org/viewtopic.php?id=181207) because I'm seeing```
Theme: Cannot open file for reading: "/home/vasa1/.local/share/lxqt/themes/a-mego/lxqt-session.qss"
```and that's related to what they're going on about. But in my case, everything seems to be working just fine (other than that line popping up in ~/.xsession-errors).

---

### Post by vasa1 on 2014-05-15
Learned something new!

In regular Lubuntu, I made a few custom notifications. As an example I have a script that is just:```
#!/usr/bin/env bash
      notify-send "$(date)"

```and when I run it, I get the time and date as an onscreen notification.

The thing is that with LXQt, in addition to the time and date I got a line with "notify-send". To avoid that I must use **notify-send --app-name"" "$(date)"**. That prevents "notify-send" appearing as a separate line.

Thanks to **jleclanche** here: [https://github.com/lxde/lxde-qt/issues/121#issuecomment-43206514](https://github.com/lxde/lxde-qt/issues/121#issuecomment-43206514) 

Now I'm off to fix the rest of my custom notifications.

---

### Post by oldrocker99 on 2014-05-15
The Razor-qt dev team has been working with the LXDE team, and the fruits of their labor can be found here:

[http://lxqt.org/](http://lxqt.org/)

I have installed LXQT on two machines, and it works very well, with a slightly smaller footprint than LXDE. 

Note: If you have razor-qt installed, remove it before installing LXQT, which is a big improvemt over razor-qt.

---

### Post by oldrocker99 on 2014-05-15
I had razor-qt installed, and had to remove it befor LXQT would start. Smooth sailing since then.

---

### Post by ibjsb4 on 2014-05-16
Hay oldrocker99
I read your post.  Sniffing around for another game :)

That may be it.  Got razor installed on it.  When I break my current working install I will keep this in mind.

---

### Post by walterorlin on 2014-05-16
I have a virtualbox 32 bit installed. I seem to try to find which kind of apps to use and qpdfview seems to just work and does what I want in a pdf editor. 

I also find using openbox to have the setting for the lxqt-runner to have desktop all property in lxqt config but don't have the small xml changes to ~/.config/openbox/rc.xml to make it show up on all desktops so I don't leave it open and then switch desktops and wonder why it does not come up.

---

### Post by vasa1 on 2014-05-16
From a Facebook page:

---

### Post by ibjsb4 on 2014-05-17
I have tried to change my clock font size from here:
> /usr/share/lxqt/themes/light/lxqt-panel.qss
```
* Clock
 */
#Clock #TimeLabel {
    font-size: 10pt;
    color: #606060;
}
#Clock #DateLabel {
    font-size: 8pt;
    color: #606060;
```
Also rebooted and no change (the above is default).

Any thoughts

---

### Post by vasa1 on 2014-05-17
Alt+F1 > Preferences > LXQt System Settings > Appearance > LXQt Theme: here, go back and forth a couple of times but make sure you have the light theme selected when you close that window.

For me, changes to *#TimeLabel* work but changes to *#DateLabel* have no effect.

BTW, I prefer to alter files for each user rather than system-wide. I have given the location for lxqt-panel.qss earlier.

For me, the changes are visible as soon as I save the file; no need to switch themes or log out or reboot.

---

### Post by vasa1 on 2014-05-18
My next aim is to have Conky blend in well with the lxqt panel because I like to have a temp reading which LXQt doesn't yet provide. And the LXQt applet to provide info on RAM seems a bit heavy so I've got Conky to give me those two. Now I'll fiddle a bit to make my LXQt panel and Conky appear seamless. stinkeye had given me some pointers before he left: [http://ubuntuforums.org/showthread.php?t=2199804](http://ubuntuforums.org/showthread.php?t=2199804)

---

### Post by bapoumba on 2014-05-18
@oldrocker99 : moved one of your post in here (#59 if I looked correctly).

---

### Post by ibjsb4 on 2014-05-18
> **vasa1 said:**
> Alt+F1 > Preferences > LXQt System Settings > Appearance > LXQt Theme: here, go back and forth a couple of times but make sure you have the light theme selected when you close that window.

For me, changes to *#TimeLabel* work but changes to *#DateLabel* have no effect.

BTW, I prefer to alter files for each user rather than system-wide. I have given the location for lxqt-panel.qss earlier.

For me, the changes are visible as soon as I save the file; no need to switch themes or log out or reboot.

Guess I will have to play with it some more.  I have the right theme and I can set things up system wide as I am the only user.  I have set other fonts, sizes, icons, panel by using one  or most of the many configuration GUI's.  The clock is all that remains.

---

### Post by ibjsb4 on 2014-05-18
Changing time and date with the qss file works in the 'green' and 'a-mego' themes.  So I went with the green theme.

---

### Post by vasa1 on 2014-05-19
> **ibjsb4 said:**
> ... I can set things up system wide as I am the only user. ...
So am I. There's a bit of a tradeoff.

System-wide needs elevated privileges but that's no big deal for some people depending on their karma.

Using the system-wide means an update *may* write over changes. On the other hand, we know something changed. All the same, since what I'm modifying is mainly cosmetic, I'd rather not have an update affect me and by having the corresponding file in my home folder that isn't a problem.

---

### Post by vasa1 on 2014-05-19
> **ibjsb4 said:**
> Changing time and date with the qss file works in the 'green' and 'a-mego' themes.  So I went with the green theme.

If you're sure of that you may like to raise an issue @ GitHub!

---

### Post by ibjsb4 on 2014-05-19
> **vasa1 said:**
> If you're sure of that you may like to raise an issue @ GitHub!

Why would I not be sure?  And really don't think this is worth raising an issue.  We need to wait for qt5.  Till then, all my issues shall remain here.

---

### Post by vasa1 on 2014-05-19
> **ibjsb4 said:**
> Changing time and date with the qss file works in the 'green' and 'a-mego' themes.  So I went with the green theme.
Works with the light theme as well

---

### Post by ibjsb4 on 2014-05-19
> **vasa1 said:**
> Works with the light theme as well

For you yes, for me no.  As stated, green theme is good for now.

[ATTACH=CONFIG]253288[/ATTACH]

---

### Post by gmunioz on 2014-05-19
My experience.
I use a VirtualBox virtual machine.
1024 megs of Ram.
64 megs of video with 3D acceleration.
Dynamic virtual drive 8 gigs.
Network card as a bridge.
In Trusty Tahr Xubuntu 32 bit
I installed the system with the Trusty Tahr mini.iso of 32 bits.
The system started in a terminal.
I added the repositories.
> sudo su
apt-get update
apt-get install  software-properties-common
add-apt-repository ppa:lubuntu-dev/lubuntu-daily
add-apt-repository ppa:gilir/q-project
I upgraded from Trusty Tahr to Utopic Unicorn:
> sudo su
nano /etc/apt/sources.list
I changed trusty by utopic
I saved the file and execute
> sudo su
apt-get update
apt-get dist-upgrade
apt-get autoremove
apt-get clean
reboot
sudo su
apt-get install xserver-xorg xserver-xorg-core xfonts-base xinit x11-xserver-utils x11-apps x11-session-utils x11-utils xinput xorg lxqt-metapackage lxqt-policykit  lxqt-runner lxqt-config lxrandr-qt obconf-qt lxqt-session pcmanfm-qt lxqt-powermanagement openbox lightdm lightdm-gtk-greeter oxygen-icon-theme firefox flashplugin-installer gstreamer0.10-ffmpeg libcurl3 libnotify4 libtag1-vanilla dkms gvfs gvfs-backends policykit-1 udisks2 synaptic gnome-system-monitor gdebi smplayer system-config-samba system-config-printer cups virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
dpkg --configure -a
apt-get autoremove
apt-get clean
reboot
Works like silk.
Uses only 168 megs of Ram, running system monitor
and 392 megs of Ram with Firefox accessing the forum.
From PCManFM I connected to the host, to another PC on the network and shared printer.

[B]I am Spanish user.
For the text I used translate.google.com[/B]

---

### Post by ibjsb4 on 2014-05-20
I rebooted (its been 3 days since last reboot) and my lxqt session has turned into a openbox session.  I have restored the panel, desktop background is missing.  Works ok, I am on it now.

I think there are six sessions to choose from (at login).  Only openbox and lxqt session has worked from the start.  Now this ..

I have been playing with xml, css, qss files.  This could be self inflected.

My lxqt flag ship is sinking :(

---

### Post by sudodus on 2014-05-21
Tough guys never back up their data. They do the work twice instead.

I'm not tough, so I have several life-boats ;-)

---

### Post by ibjsb4 on 2014-05-21
I have life-boats :) but will try to fix this first.

I am new to the inner workings of these types of files and need to learn more.  Its tough being a gnome guy in a qt world.

I will first fire up my virtual machine and fully update it.  Just to be sure this is not a update problem.  But its 6:30 am here, on my second cup of coffee and I'm in no mood for this.  So ..

---

### Post by sudodus on 2014-05-21
Yeah, like learning a new language it's tough. I've tested LXQt, and it runs for me, but I'm not ready to do any major tweaks.

Good luck :-)

---

### Post by slooksterpsv on 2014-05-21
Trying out LXQT on Xubuntu 14.04 - dang that was the fastest I've seen my computer log in in a while.

---

### Post by slooksterpsv on 2014-05-21
That was quick, installed LXQT on Xubuntu 14.04 - my desktop appeared quicker than Lubuntu desktop - a lot faster.

---

### Post by ibjsb4 on 2014-05-22
> **slooksterpsv said:**
> That was quick, installed LXQT on Xubuntu 14.04 - my desktop appeared quicker than Lubuntu desktop - a lot faster.
Hi slooksterpsv
What install method did you use?

---

### Post by oldrocker99 on 2014-05-22
> **ibjsb4 said:**
> I rebooted (its been 3 days since last reboot) and my lxqt session has turned into a openbox session.  I have restored the panel, desktop background is missing.  Works ok, I am on it now.

I think there are six sessions to choose from (at login).  Only openbox and lxqt session has worked from the start.  Now this ..

I have been playing with xml, css, qss files.  This could be self inflected.

My lxqt flag ship is sinking :(

The same Openbox thing happened to me, then there was an update, and all is fine.

---

### Post by slooksterpsv on 2014-05-22
```

sudo apt-get install software-properties-common

sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily 

sudo add-apt-repository ppa:gilir/q-project

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install lxqt-metapackage

```

---

### Post by ibjsb4 on 2014-05-22
> **oldrocker99 said:**
> The same Openbox thing happened to me, then there was an update, and all is fine.

Your spot on, updated and problem is gone :)

---

### Post by ibjsb4 on 2014-05-22
@slooksterpsv

Thanks

---

### Post by servimo on 2014-05-23
I could not install ppa:gilir/q-project says package not found

---

### Post by ibjsb4 on 2014-05-23
> **servimo said:**
> I could not install ppa:gilir/q-project says package not found

Post #84 :)
```
sudo apt-get install software-properties-common
```
Then try the ppa again.

---

### Post by Rob Sayer on 2014-05-26
I just installed LXQT yesterday on my 1Gb netbook, after a new install of xubuntu 14.04.  Previously it had Lubuntu 13.10, though I tried LXQT first before installing 14.04.

So far I definitely like LXQT more than LXDE.  The latter is pretty fast in 1GB but I find LXDE kind of clunky.  And as far as I can see its development seems pretty stagnant.

Plus a lot of my favorite apps use the Qt toolkit.  The machine I use at home mostly runs Kubuntu 12.04, and I don't want to use any file manager other than dolphin nowadays.  So I was running lubuntu with dolphin and konsole installed, and I think I should also install ark on this machine now.  IME Qt apps run a lot better in a Qt environment.

For example, dolphin loads *way* faster in LXQT than LXDE.

Something I find interesting is that LXQT is using its own native power manager, which seems to work pretty well ... the machine runs quite cool, as much as LXDE.  But when I ran Lubuntu 13.10, it installed the XFCE power manager rather than the native LXDE one.

When I first tried LXQT in lubuntu, that was the last alternative DE I was going to try before installing Xubuntu.  When I realized that you have to enable the lubuntu daily build repo I figured I'd have to try it and then install Xubuntu as quickly as possible.

I figure I can live with a bleeding edge perpetual beta DE as long as it's installed over a stable one.  Y'know, in case an update borks it.

But enabling lubuntu daily builds would seem to make ALL my desktops unstable in lubuntu.  I'm actually rather conservative with this stuff.  I don't use 3rd party conkys.  I won't even use 3rd party skins for app software.

Basically I think installing LXQT in Lubuntu is just plain NUTS.  But I like LXQT a lot.  Definitely more than LXDE.

---

### Post by oldrocker99 on 2014-05-26
I had (as seen above) had some problems with a pure Openbox session when logging into lxqt-desktop (had to log in to LXDE at that point), but an update fixed that, and I have had zero problems with lxqt since. I'm very impressed with the work done by the devs on this next-generation desktop.

---

### Post by ibjsb4 on 2014-05-26
> **oldrocker99 said:**
> I'm very impressed with the work done by the devs on this next-generation desktop.
Agree on that :)

I have not yet installed the qt5-default (5.2.1) package.  Has anyone else tried it?

---

### Post by Rob Sayer on 2014-05-28
Anyone know if you can autohide panels in LXQT?  Obviously the docs are limited.  There isn't any way I can find.  AFAIK it's on the to-do list.

I have lxqt installed over a 3 day old Xubuntu 14/04 install, and if you can't autohide panels I'll be using XFCE until you can.  I'm using it on a netbook ... which is where this sort of DE is particularly relevant ... and it's kind of a deal breaker.

I have lxqt-panel, installed when I put LXQT on.

Overall, though, for a development release LXQT is remarkably good.

---

### Post by bytheskylight on 2014-05-29
I absolutely am loving LXQT!!! I have it installed on ubuntu 14.04 and its blazing fast!! Faster than LXDE or XFCE could ever be. Im just waiting for it to be shipped on Lubuntu or whatever they are gonna put it on. LXQT will be my DE of choice!

---

### Post by ibjsb4 on 2014-06-16
I installed 14.10 today and tried to install LXQt on it.  Seems to be a lot of missing depends.  Anyone else get this to work or is it a work in progress?

---

### Post by gmunioz on 2014-06-16
Use the repositories  ppa:lubuntu-dev/lubuntu-daily and ppa:gilir/q-project for Trusty Thar in Utopic Unicorn.

---

### Post by ibjsb4 on 2014-06-17
Thanks, but I have a working TrustyT.  Just wanted to see if 14.10 had anything new to offer.  Think I will wait a few days (weeks?) and try again :)

---

### Post by gmunioz on 2014-06-17
If you want the newest of the new, look here:
[http://ftp.spline.de/mirrors/siduction/iso/paintitblack/lxqt/amd64_2014-05-08_17-04/siduction-14.1.0-paintitblack-lxqt-amd64-201405081704.iso](http://ftp.spline.de/mirrors/siduction/iso/paintitblack/lxqt/amd64_2014-05-08_17-04/siduction-14.1.0-paintitblack-lxqt-amd64-201405081704.iso)

---

### Post by ibjsb4 on 2014-06-18
> **gmunioz said:**
> If you want the newest of the new, look here:
[http://ftp.spline.de/mirrors/siduction/iso/paintitblack/lxqt/amd64_2014-05-08_17-04/siduction-14.1.0-paintitblack-lxqt-amd64-201405081704.iso](http://ftp.spline.de/mirrors/siduction/iso/paintitblack/lxqt/amd64_2014-05-08_17-04/siduction-14.1.0-paintitblack-lxqt-amd64-201405081704.iso)

Not so sure of what I'm getting into, but thanks, I will give this a try :)

---

### Post by ibjsb4 on 2014-06-29
PCmanFM-QT will open xterm from the tool bar, but I want qterminal to open instead.

I went to ~/.config/pcmanfm-qt and changed line #4 from Terminal=xterm to Terminal=qterminal, but this did not have any effect.

Any thoughts?

---

### Post by ibjsb4 on 2014-07-02
I booted up one of my lxqt installs today.  It did not go well.  I have lost a major amount of functions.

Autoremove wants to remove about 300 packages, everything related to lxqt.  So I did ..
I then reinstalled lxqt-metapackage.

Autoremove now shows nothing to remove, but this install is still totally hosed.  Function keys not working, panel icons missing and will not reinstall, main menu gone.  I was able to get a terminal thru pcmanfm (one of the three remaining launchers in my panel), but F4 will not pull it up.

Apt-get -f install shows nothing to repair and --configure -a yeilds nothing.

Unless someone has an idea; it looks like I will have to reinstall.
This is 14o4.

---

### Post by ibjsb4 on 2014-07-02
Well I reinstalled the 11 packages pertaining to panel and it seems to work again.  I have my main menu back. Drag and drop of panel launchers is not working.  Theme and background restored.  Function key are working again, don't really know why that is.  This was my backup install, but I think I will start using it daily.

---

### Post by Portaro on 2014-07-05
Thanks for test the new lxde, I use Openbox and LUbuntu 14.10 distro baseds.
Hum the performance of lubuntu 14 increases much, I hope that new qt maintain a good light distro.

Thanks for your feedbacks I think this thread is very important for the Lubuntu users.

---

### Post by ibjsb4 on 2014-07-06
Thanks for the reply :D

---

### Post by ka0pmd on 2014-07-13
I'm using LXQt, and it's simply amazing.  It's actually faster than the bog-standard Lubuntu.

So far, the only bug I've encountered is the inability to drop application icons onto what I'd call the taskbar (Actually, I believe it's called a "Panel."

FWIW, I'm using 0.7.  I'm blown away!

-Steve in Chicago

---

### Post by ibjsb4 on 2014-07-13
> So far, the only bug I've encountered is the inability to drop  application icons onto what I'd call the taskbar (Actually, I believe  it's called a "Panel."

Drag and drop to panel works on my Qt4 install, but not in Qt5.

---

### Post by bapoumba on 2014-07-23
Looks like it is a no go on Utopic for now, broken dependencies..

---

### Post by bapoumba on 2014-07-24
Anyone being able to work with Software Updater ? Waits for half a second for password input, I can enter the first few char and then it complains the authentication has failed, the dialog box remains unresponsive. I'll file a bug report unless there is already one around that I missed.

---

### Post by ibjsb4 on 2014-07-24
Hi

> **bapoumba said:**
> Looks like it is a no go on Utopic for now, broken dependencies..
I also tried a few weeks back with same results.  Early talk was a 14.10 lubuntu-qt release, but me wonders if it will happen.

> **bapoumba said:**
> Anyone being able to work with Software Updater ? Waits for half a second for password input, I can enter the first few char and then it complains the authentication has failed, the dialog box remains unresponsive. I'll file a bug report unless there is already one around that I missed.
Software updater?  What software updater?  I never noticed until you brought the subject up, but it seems lxqt does not have one.  I installed synaptic in the beginning and never noticed it was missing.  Are you using the lubuntu updater?

---

### Post by bapoumba on 2014-07-24
Thanks ibjsb4 :)
Yeah, installed lxqt on top of lubuntu (not enough room on this laptop to have more than 2 releases side by side). So that closes the question. No wonder I found nothing on the subject..

May be one point to consider in the future. I guess people will install both environments for the same user, even if it is not recommended. That allows to try out and test without too much hassle. The dialog box is quite funny, asking for the password of my other admin account as unix:user. Once I reboot into 14.04, I'll post a screenshot.

When I booted into 14.04-lxqt yesterday, got myself with 3 versions of the same panel, that I fixed editing /home/.config/lxqt/panel.conf. To note, adding mainmenu to a panel adds the icon but it does not work (have not inverstigated yet).

---

### Post by ibjsb4 on 2014-07-24
> **ka0pmd said:**
> So far, the only bug I've encountered is the inability to drop application icons onto what I'd call the taskbar (Actually, I believe it's called a "Panel."

-Steve in Chicago

I do not update daily, but my update today has fixed drag and drop to panel.

---

### Post by bapoumba on 2014-07-24
Yes, the quicl launch applet where you can drag and drop can be small and it wont work outside of its space.
[https://github.com/lxde/lxde-qt/issues/235](https://github.com/lxde/lxde-qt/issues/235)

---

### Post by Elfy on 2014-08-16
Closed at request.

---

