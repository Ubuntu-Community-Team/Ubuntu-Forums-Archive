---
title: "How do I play online radio?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by chapmc on 2006-08-21
I have just installed ubuntu v6 and things seem to be working fine.  Even detected my usb wifi without any problem. I was surprised.  I am trying to play online radio. I click a station link and firefox downloads a file.  The first was *.rpm and when I tried to open it I got it used totem movie player which gave an error no url handler.  I tried another and got *.pls. It started rhythmbox but I couldn't figure out how to start the play.  Is there something simple that will just start playing? 

I will appreciate any help you can give. I am new to linux.

thanks.

---

### Post by taurus on 2006-08-21
I think you need a mplayerplug-in for your firefox...

---

### Post by chapmc on 2006-08-21
How do I get an mplayer plugin?

---

### Post by taurus on 2006-08-21
I am not sure but I think it's in the universe so you need to edit your /etc/apt/sources.list and remove the # sign in front of all the lines that have universe & multiverse at the end.  

```

gksudo gedit /etc/apt/sources.list

```
Now, update your list with

```
sudo aptitude update
```
At this point, use synaptic to search for mplayerplug-in then...

---

### Post by chapmc on 2006-08-21
Do you think I am going to mess something up if I start changing files and don't know what I am doing?

---

### Post by taurus on 2006-08-21
Then make a backup copy of it in case you screw something up.  Then, you can restore back to the original version...

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.org
```

---

### Post by CarpKing on 2006-08-21
The .pls one should work in VLC.

---

### Post by chapmc on 2006-08-21
Here is what I got.

chap@duron:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources [975kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Fetched 3453kB in 1m18s (44.2kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
E: Couldn't rebuild package cache
chap@duron:~$

Is this OK?

---

### Post by taurus on 2006-08-21
It looks like you have another apt-get/adept/synatic/or something running in the background.  You need to kill it first before you can run apt-get/aptitude again.  What is the output of this command then?

```
ps -A
```

---

### Post by chapmc on 2006-08-21
CarpKing.  What is VLC?  I am complete dummy.

---

### Post by chapmc on 2006-08-21
taurus

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  100 ?        00:00:00 pdflush
  101 ?        00:00:00 pdflush
  103 ?        00:00:00 aio/0
  102 ?        00:00:00 kswapd0
  690 ?        00:00:00 kseriod
 1821 ?        00:00:00 khubd
 1909 ?        00:00:00 kjournald
 2140 ?        00:00:00 udevd
 2923 ?        00:00:00 shpchpd_event
 2971 ?        00:00:00 kgameportd
 3856 ?        00:00:00 acpid
 3972 ?        00:00:00 dd
 3974 ?        00:00:00 klogd
 4293 ?        00:00:00 gdm
 4299 ?        00:00:00 gdm
 4327 tty7     00:01:57 Xorg
 4336 ?        00:00:00 hpiod
 4351 ?        00:00:00 python
 4423 ?        00:00:00 dbus-daemon
 4438 ?        00:00:03 hald
 4439 ?        00:00:00 hald-runner
 4445 ?        00:00:00 hald-addon-acpi
 4470 ?        00:00:00 dhclient3
 4519 ?        00:00:00 hald-addon-keyb
 4530 ?        00:00:00 hald-addon-stor
 4531 ?        00:00:00 hald-addon-stor
4618 ?        00:00:00 hcid
 4622 ?        00:00:00 sdpd
 4637 ?        00:00:00 krfcommd
 4650 ?        00:00:00 mdadm
 4684 ?        00:00:00 atd
 4697 ?        00:00:00 cron
 4771 tty1     00:00:00 getty
 4772 tty2     00:00:00 getty
 4773 tty3     00:00:00 getty
 4774 tty4     00:00:00 getty
 4775 tty5     00:00:00 getty
 4776 tty6     00:00:00 getty
 4791 ?        00:00:01 x-session-manag
 4833 ?        00:00:00 ssh-agent
 4836 ?        00:00:00 dbus-launch
 4837 ?        00:00:00 dbus-daemon
 4839 ?        00:00:01 gconfd-2
 4842 ?        00:00:00 gnome-keyring-d
 4844 ?        00:00:00 bonobo-activati
 4846 ?        00:00:02 gnome-settings-
 4848 ?        00:00:00 esd
 4853 ?        00:00:13 metacity
 4861 ?        00:00:09 gnome-panel
 4863 ?        00:00:06 nautilus
 4866 ?        00:00:00 gnome-volume-ma
 4874 ?        00:00:01 update-notifier
 4878 ?        00:00:00 trashapplet
 4881 ?        00:00:00 gnome-vfs-daemo
 4890 ?        00:00:04 gnome-cups-icon
 4896 ?        00:00:00 gnome-power-man
 4903 ?        00:00:01 mixer_applet2
 4905 ?        00:00:00 mapping-daemon
 4907 ?        00:00:00 clock-applet
 4932 ?        00:00:00 dhclient3
 4949 ?        00:00:01 gnome-screensav
 5192 ?        00:00:02 cupsd
 5276 ?        00:00:00 syslogd
 5317 ?        00:00:01 notification-da
 5343 ?        00:00:01 gksu
 5345 ?        00:00:05 update-manager
 5349 ?        00:00:00 gconfd-2
 5375 ?        00:03:04 firefox-bin
 6700 ?        00:00:10 gnome-terminal
 6701 ?        00:00:00 gnome-pty-helpe
 6702 pts/1    00:00:00 bash
 7116 pts/1    00:00:00 ps
chap@duron:~$

---

### Post by Gnuklear on 2006-08-21
> **chapmc said:**
> I have just installed ubuntu v6 and things seem to be working fine.  Even detected my usb wifi without any problem. I was surprised.  I am trying to play online radio. I click a station link and firefox downloads a file.  The first was *.rpm and when I tried to open it I got it used totem movie player which gave an error no url handler.  I tried another and got *.pls. It started rhythmbox but I couldn't figure out how to start the play.  Is there something simple that will just start playing?

Hi Chapmc,

Welcome to the GNU/Linux world. I'm not sure why you're getting a .rpm file, but the .pls file, as you may know, is a playlist that is being automatically opened in Rhythmbox. This is expected, the problem you are experiencing is probably that you do not have an MP3 codec installed. Due to software idea patent problems, Ubuntu cannot distribute a working MP3 codec with the operating system, it must be installed by the user. This is a very simple task, though. Here's how you can enable MP3 playback:

If you'd like to use a graphical interface to install MP3 playback, then do the following:
1. At the top left of your screen (assuming you are using Ubuntu and not Kubuntu) open the "System" menu by clicking on it. Scroll Down to "Administration" and then click on "Synaptic Package Manager". Your system will probably ask you for your password, go ahead and enter it.
2. You'll probably want to enable the "Universe" repositories if you haven't done so already. If you're unaware, a repository in the GNU/Linux world is basically an online directory of available software for your specific GNU/Linux distribution, in this case, Ubuntu. You can enable the universe repository by clicking on "Settings" and then "Repositories". From here, select "Ubuntu 6.06 LTS (Binary)" and click "Add" on the right. Another dialogue box should pop up. The check boxes for "Officially Supported" and "Restricted Copyright" should be checked. Go ahead and check "Universe", and if you like, "Multiverse" as well. Click OK or Close on the open dialogue boxes until you get back to the main Synaptic application.
3. In Synaptic, click "Reload" on the left. This will update your computers cache of what is available from the repositories.
4.Click "Search", which should be an option on the same toolbar as "Reload" and type in "fluendo-mp3". This will search for the Fluendo MP3 decoder, which is legal to use worldwide. Once you see a listing similar to "gstreamer0.10-fluendo-mp3" check the checkbox to the left of it. (ie. Mark for installation). Then click Apply from the Synaptic toolbar.
5. Close Synaptic, and try to play internet radio again. If it is successful, you're done, enjoy!

taurus suggested installing the mplayer browser plugin. This will enable multimedia to be played in your browser, instead of a seperate application like Rhythmbox. If you'd like to do this, search for "mozilla-mplayer" in Synaptic and check the box next to it for installation.

If you would like more information on multimedi playback on Ubuntu, I suggest checking the Ubuntu wiki at [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Gnuklear on 2006-08-21
Also, chapmc, I think the reason you can't open aptitude or synaptic is that you have update-manager running. If you can, close it, then try aptitude or synaptic again.

---

### Post by taurus on 2006-08-21
Maybe the "4874 ? 00:00:01 update-notifier" is the problem.  You can kill that process with

```

sudo kill -9 4874

```
Then, update it...

```
sudo aptitude update
```

---

### Post by chapmc on 2006-08-21
Thanks for all the help and suggestions!  I feel like I am in over my head at the moment and I am going to take a break for a while.  I will get back to it later.  Thanks again.
chapmc

---

### Post by abu-fatu on 2006-08-21
chapmc i am also a noob.
iam able to listen to online radio with real player. when i click on the listen live link real player opens up and plays the live stream no problems.
you should be able to get real player 10 thru automatix. good  luck.

---

### Post by chapmc on 2006-08-22
I got fluendo-mp3 installed and now I can listen ok.  Thanks for the help.  I might try to install realplayer. 
In my remarks about ubuntu I forgot to mention that it found my printer on windows xp box on the network and I can print!!  I've never installed a linux distro that I could get the printing to work.  GREAT!!

---

