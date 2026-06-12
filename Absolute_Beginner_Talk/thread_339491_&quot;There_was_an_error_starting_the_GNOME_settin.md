---
title: "&quot;There was an error starting the GNOME settings daemon&quot; in edgy"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by diverbelow on 2007-01-15
I have recently installed edgy on three different computers i.e. Compaq M700 (intel video card)  and Dell GX-50 (intel video card) and HP Pavilion (nvidia video card). All of these installs where a fresh install, with all updates. Here is the problem I am having. when I first boot up, I can login just fine, but once I logout and I go to relogin, I get the following error message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

The only way I can get to the deskstop is to reboot and log back in. I have search the web, but have not found a fix. Does anyone know how to solve this problem?

---

### Post by jimrz on 2007-01-15
> **diverbelow said:**
> I have recently installed edgy on three different computers i.e. Compaq M700 (intel video card)  and Dell GX-50 (intel video card) and HP Pavilion (nvidia video card). All of these installs where a fresh install, with all updates. Here is the problem I am having. when I first boot up, I can login just fine, but once I logout and I go to relogin, I get the following error message:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

The only way I can get to the deskstop is to reboot and log back in. I have search the web, but have not found a fix. Does anyone know how to solve this problem?

i occassionally (pretty rarely actualy) get this on my old laptop..not sure why

press 'control + alt + backspace' to restart Gnome without having to do a full reboot and has always taken care of the problem when i get that msg

---

### Post by diverbelow on 2007-01-16
I have restarted gdm that way, and also dropping to command line and stopping and restarting gdm that way. I input in my username/password, I either get a blank screen with a gray box in the upper left hand corner of the screen or it loaded once but that error dialog window appeared.

---

### Post by drawab on 2007-01-19
Well I would second the request for a solution to the same problem.  This error has NOT been since I upgraded to EDGY but was found literally a few days later.  It slows down my boot-up, only to recoever after seeing this error.  I was initially on manual log-in and switched to automated log-in but the problem persists.

The error is as follows

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

---

### Post by Pipone on 2007-01-19
1. 
/etc/hosts 

and make sure there's a line:

127.0.0.1 localhost 

2.
Make shure you have auto lo
/etc/network/interfaces

ifconfig to see if lo is active at startup.
ifconfig lo up to start it manually, restart gnome to see if this is the problem

---

### Post by stray1 on 2007-03-18
> **jimrz said:**
> i occassionally (pretty rarely actualy) get this on my old laptop..not sure why

press 'control + alt + backspace' to restart Gnome without having to do a full reboot and has always taken care of the problem when i get that msg

Did you find ANYTHING else about this problem? I'm trying to get this installed on an old laptop myself, (panasonic cf71 w/256mb ram). The sucker crashes with these problems. it wont even boot into the live CD long enough to install.

is there a command I can use to install from the Live cd boot dialog directly?

This is a pretty old laptop. PII 333, 256mb ram (maxed), and a 2mb vid card. <-- yeah 2 mb. The thing is a TANK though.

I know some people have had some success with this model so I know its possible.

---

### Post by linuxjerk on 2007-03-18
I have exactly the same problem. This version won't work with p2 systems for some reason.
It doesn't recognize my mouse either so I'm really stuck.
Works fine with my p4 though. What a shame.

---

### Post by Portable_Jim on 2007-03-26
> **drawab said:**
> Well I would second the request for a solution to the same problem.  This error has NOT been since I upgraded to EDGY but was found literally a few days later.  It slows down my boot-up, only to recoever after seeing this error.  I was initially on manual log-in and switched to automated log-in but the problem persists.

The error is as follows

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```
Same problem completely. Does anyone know a solution?

---

### Post by akoblentz on 2007-03-29
I'm having the same problem on a fresh install of edgy.  I do not have a p2, I have an amd64 fx2 NOT running the 64bit version of ubuntu.

---

### Post by surfnkid on 2007-03-29
Add me too, I unfortunately had to upgrade from Dapper to EDgy due to partitioning and resizing. When Edgy was installed I set nothing but my typical apps then after several apt-get updates, the system will begin to start correct and fast up to the login screen. Then right after login, it takes anywhere btw 3 to 5 minutes to load the desktop, grey square on the left top then Gnome Settings Daemon window shows error.

Reinstalled Edgy twice and both times I narrowed the problem down by not installing any other apps after the fresh install. So its not something I install, it just taints itself (my assumption). Deleted my only user acct and created a new one with root priv, still freezes on login, Help guys! please check this issue, it is starting to be seen everywhere! and its annoying, takes forever for the desktop to load.

corrected /etc/hosts file and /etc/network/interfaces 

no go. clueless. sumfn is hax0ring me computaz!!

---

### Post by surfnkid on 2007-03-29
Forgot to add System is Dell 8600 

Centrino 2.1Ghz  1024MB RAM  128MB M10 ATI Video. Bluetooth, TrueMobile 1300 Wifi

Never seen error on Dapper or Breezy, only on Edgy, Installed from DVD ISO

Also, panel icons are grey and fuzzy, but if you go to System/Pref/Themes, as soon as it loads the app, The Ubuntu theme starts to draw itself before your eyes, as if it is something with the themes, sounds or background settings as the error says.

---

### Post by ernstblaauw on 2007-03-29
I fixed it by starting KDE once. Read [here](http://ubuntuforums.org/showpost.php?p=2338605&postcount=4).

---

### Post by surfnkid on 2007-03-29
But I don't have KDE installed I'd have to install the ubuntu-kde desktop :( 

and Im already too involved in GNOME :P

I'm trying to see if deleting a bunch of ./xxx folders in /home/<user> could fix that problem

---

### Post by geraner on 2007-03-31
> **surfnkid said:**
> 

I'm trying to see if deleting a bunch of ./xxx folders in /home/<user> could fix that problem

I had the same problem.
Deleting all ./xxx folders in /home/<user> fixed the problem for me.
I just had to re-configure my task-list again with all short-cuts I had there.

Thanks

Geraner

---

### Post by deja on 2007-04-01
I had the same error mentioned in here.  The problem was my loopback interface.  It was actually set up correctly, which threw me through a loop, no pun intended (the auto lo was listed as it should've).  I removed duplicates of other interfaces and cleaned it up.  


The system breezed through the startup like I haven't seen it do since....I last tried to play with network configurations.  

Try resetting your interface configuration to "stock" values.

---

### Post by maccawolf on 2007-04-01
Great suggestion Deja, Problem is that NEtworking is probably the only thing I HAVEN'T played with yet...lol

I still have that problem too BTW.

---

### Post by cyrano24100 on 2007-04-01
Hello Guys, this is my third day on Ubuntu!

I actually got out of the house today -- it's my wife's birthday and we got her a pricy piece of jewelry (it's also our 5th wedding aniversary and Palm Sunday all in one!)... So yes this exact problem was plaguing me:

"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in."

I couldn't get the GNOME windows-like interface to come up, and when it did the icons were weird and everything was slow (literraly 1 hour for it to launch!)

I think the fresh air must have done something because I came back from the jewelry shop, tried a few things and voilà it's fixed.

Note 1. My machines:
Dell PowerEdge 1950
Broadcom NetXtreme II NICs

Note 2. The instalation:
Ubuntu 6.10 (Edgy) , LAMP install

Chonologically;
1. Changed my network card to use DHCP (not static)
I couldn't get static figured out, and I think that linux is suppose to take care of networking later, so during boot I pressed "ctrl+R" and changed the networking from "static" to "DHCP"

2. Installed Ubuntu from CD
! Got an error message during the "configure the network" phase:
"No network interfaces detected. You may still need to load a specific module blahblah"
I just pressed continue since I didn't know what to do -- and figured I get this one changed later
! made sure to have an actual asterisk "*" when selecting DHCP server or LAMP; my first installs just "highlighted" the option; you need to press spacebar to actually select it.

2. Finished install and got the prompt - but network didn't work
So I started playing right there with the network interface setting by typing:

sudo vi /etc/network/interfaces
(prompts for password)

This throws you in a linux text editor which is verry odd to work... look it up online it's got a couple commands: use "i" to insert text, and ":wq" to save & quit... or just ":q" to quit

I eddited the file as below:
#This has notes in here
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Note that on my previous tries I forgot the "auto lo" paragraph, and omitting it gave me networking, but for some reason gave me the dreaded error: "There was an error starting the GNOME settings daemon".

Once you edited the interfaces text above. you need to restart networking:

sudo /etc/init.d/networking restart

To see if everything went well take a look at the individual networks:

ifconfig eth0

and

ifconfig eth1

3. Ubuntu Desktop install
From now on no extra magic: just the desktop install:

sudo apt-get update

sudo apt-get install ubuntu-desktop

This takes a whyle, asks you a resize question, monitor resolutions, then gives you a prompt.

4. Reboot!
Now a simple:

sudo shutdown -r -now

or -h if you want to shutdown your machine.


Now three days later Wasn't that easy!

---

### Post by surfnkid on 2007-04-02
Obviously the loopback interface has to be initiated to for some local services to see  127.0.0.1. that's it, it has to be ON not OFF.
:shock: 
Now my problem is fixed once i added 
-auto lo
-iface lo inet loopback
(which means after login, it no longer freezes for a few minutes, times out and throws out error... it just breezes thru)


I've deducted that the GNOME error is due to some services requiring the loopback interface to be available so it replies to certain applets or scripts upon login and without loopback on it'll just freeze and time out after a few minutes or so.

I removed all interfaces from /etc/network/interfaces for the sole purpose of having an empty file, but not so fast, im not supposed to mess with that!!

Also note I didn't have to put any other interface except lo on to have the error disappear, this one interface (lo) did it

So going back to my doings, here's what I did... (even though I said I didnt touch one bit... well I appearently did)


I use dhclient a lot, but everytime i use it it has to start lo,eth0,eth1,ath,ppp etc.. so when I reinstalled Edgy all the times I did, I thought it was easy to remove everything in the /etc/network/interfaces file except wlan0 since this was the only interface I used, but wrong move, lo has to be on.

And now it seems like everything is back to starting normally and as a fresh install! 
If it returns I'll monitor it again

On a similar note, if starting Services or Firestarter without lo on, Firestarter takes a few minutes to load and Services never loads. Well now... right back to starting up normal. :) 

"The forum's ability to exchange ideas makes solutions exceptionally simpler to exchange"
:lolflag: 
Dell 8600 1.4Ghz Centrino, 1024MB, 60GB, ATI M10 128MB, 15.4" 1280x800
Ubuntu 6.10 / XP Windows

---

### Post by dsauxier on 2008-05-04
I ran into this problem after upgrading to Hardy Heron from Gutsy Gibbon.
Thanks, Pipone, your 2nd suggestion did the trick.

> **Pipone said:**
> 1. 
/etc/hosts 

and make sure there's a line:

127.0.0.1 localhost 

2.
Make shure you have auto lo
/etc/network/interfaces

ifconfig to see if lo is active at startup.
ifconfig lo up to start it manually, restart gnome to see if this is the problem

---

### Post by chris.simpson on 2008-05-05
OK, I also have this problem after upgrading from Gutsy to Hardy.
```

% cat /etc/network/interfaces
auto lo
iface lo inet loopback

% cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       Dunraven-PC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

% gnome-settings-daemon

** (gnome-settings-daemon:7055): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:7055): WARNING **: Could not acquire name

```
Adding auto eth0 in /etc/network/interfaces seems to make no difference. Any ideas anybody please?

---

### Post by dsauxier on 2008-05-06
Adding those first two lines worked for me ("auto lo" and "iface lo inet loopback")

After booting, <CTRL><ALT><F2> to get to a console.. sign in and run 
```
ifconfig 
```
Is the lo interface up and running?
If not, run 
```
sudo ifup lo
```
Any errors???

---

### Post by kacheng on 2008-05-07
I'm having the same problem, and I've tried the three suggested fixes I can find:

/etc/networking/interfaces
```
auto lo
iface lo inet loopback
```

/etc/hosts
```
127.0.0.1       localhost

```

/tmp
```
sudo chmod -R 0777 /tmp
```


None seem to be working for me.
```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

~$ cat /etc/hosts
127.0.0.1 localhost bigturtle
127.0.1.1 bigturtle

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:01:4b:00
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5853717 (5.5 MB)  TX bytes:12449039 (11.8 MB)
          Interrupt:18 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:195862815 (186.7 MB)  TX bytes:195862815 (186.7 MB)

~$ gnome-settings-daemon

** (gnome-settings-daemon:17444): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:17444): WARNING **: Could not acquire name

```

Any ideas appreciated!

---

### Post by grantwfuller on 2008-05-07
I am having the same problem. This is also causing keyboard lag. Here is what I get:
~$ gnome-settings-daemon

** (gnome-settings-daemon:7422): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-0aKGkHbkVY: Connection refused

(gnome-settings-daemon:7422): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-0aKGkHbkVY: Connection refused

(gnome-settings-daemon:7422): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:7429): WARNING **: Failed to register with the message bus

I am a beginner using Ubuntu 7.10 installed from CD purchased from Linux

---

### Post by jpete214 on 2008-07-23
adding localhost to my /etc/hosts file fixed this error for me in hardy.

thanks!

---

