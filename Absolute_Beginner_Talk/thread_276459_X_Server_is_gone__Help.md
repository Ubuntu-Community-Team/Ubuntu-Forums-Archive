---
title: "X Server is gone ?? Help"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-12
I have had this OS up and running for about a month and this is the first wall I have come up against. I turned on the computer and the boot up started as normal, then the Ubuntu screen and the drivers all start loading, this goes on for about 5 seconds more then I get the message:

_Failed to start the X server - Likely that it is not set up correctly. Would you like to view the Xserver output to diognose the problem?_

I say YES and get the following:

_X Window System Version 7.0.0
Release date: 21 December 2005
X Protocol Version II, Revision 0, Release 7.0
Build Operating system: Linux ubuntu 2.6.15-27-386 #1PREEMPT Sep 16 01:51:59 UTC 2006 i686
Build date: 16 March 2006
Modular Loader present
Markers: (--)probed, (**) from config file,
(==)default setting,
(++) from command line, (!!) notice,
(II) informational, (WW) warning,
(EE) error, (NI) not implemented,
(??) unknown
(==) Log file: "/var/log/Xorg.0.log"
Time Thur Oct 12 19:15:11 2006
Using config file: "/ect/X11/xorg.conf"_


Then select <OK> and get this message:

_The X server is now disabled. Restart GDM when it is configured correctly._

I tried rebooting using the recovery mode but I was afraid to make things worse in there as root.

Any ideas?

---

### Post by PriceChild on 2006-10-12
Have you installed nvidia drivers from a binary package

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

for example?

---

### Post by kindafunnylookin on 2006-10-12
Yes, I was doing a HOW TO from the forum and at the end when the reboot was required this started.

---

### Post by blendmaster on 2006-10-12
To temporarily restart x type :

```
startx
```

I don't know why, but it works. Though it doesn't look very nice, at least it provides a GUI.

---

### Post by PriceChild on 2006-10-12
> **kindafunnylookin said:**
> Yes, I was doing a HOW TO from the forum and at the end when the reboot was required this started.Could you tell us what HowTo please?

---

### Post by kindafunnylookin on 2006-10-12
OK.
Do I do that as root using the rescue boot?

---

### Post by kindafunnylookin on 2006-10-12
This is the really embarrasing part, I was hopeing that you would not be asking that question.

NO I cannot rember the HOW TO. I have been back there for over an hour trying to figure it out.

---

### Post by blendmaster on 2006-10-12
Well, I mean use startx if your still not in any GUI.

If you're still in command-line mode, then use startx, you don't need to use sudo, just startx.

I don't get how it works, considering when you are doing this, you usually don't have correct x files on your system. But I tried it with broken files, and it works fine.

---

### Post by blendmaster on 2006-10-12
Is [this]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") the site?

---

### Post by kindafunnylookin on 2006-10-12
That is not it

---

### Post by Crashmaxx on 2006-10-12
> **kindafunnylookin said:**
> Yes, I was doing a HOW TO from the forum and at the end when the reboot was required this started.

Did you backup the xorg.conf file? If you did, then just type this in the root terminal:
```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
Replace xorg.conf_backup with whatever you named the backup. If you don't know what you called it, then try to find it like this:
```
ls /etc/X11
```
And another tip, if you type part of a code and press TAB, it will auto complete it if there is only one option. And if not, either continue typing and hitting TAB or press TAB twice to see a list of possibilities.

Once you get the backup in place, press CTRL+ALT+BACKSPACE to restart the X server. Then I recommend using Automatix or EasyUbuntu to install the driver. But regardless, you at least have the GUI back. And automatix can now be found in synaptic.

Hope that helps.

---

### Post by blendmaster on 2006-10-12
Darn!:rolleyes: 

I know of another that broke my x, but I can't remember where it is...:-k

---

### Post by kindafunnylookin on 2006-10-13
OK just got back from ny broken ubuntu---

From the command line I tried:
```
startx
```
I got:
Fatal server error
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server "0.0" after 0requests (0 known processed) with 0 events remaining.
Xauth: error in locking authority
file /home/peter/.Xauthority


When I tried:
 
```
cp /ect/X11/xorg.conf_backup /ect/X11/xorg.conf
```
I got:
No such file or directory

When I tried:
```
ls /ect/X11
```

I got:
no such file or directory

Now I'm starting to panic.

---

### Post by confused57 on 2006-10-13
Here's a site for reconfiguring your xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

You might be able to change your video driver to "nv" for now, which should work until you can get things worked out with the "nvidia" drivers.

---

### Post by Crashmaxx on 2006-10-13
> **kindafunnylookin said:**
> OK just got back from ny broken ubuntu---

From the command line I tried:
```
startx
```
I got:
Fatal server error
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server "0.0" after 0requests (0 known processed) with 0 events remaining.
Xauth: error in locking authority
file /home/peter/.Xauthority


When I tried:
 
```
cp /ect/X11/xorg.conf_backup /ect/X11/xorg.conf
```
I got:
No such file or directory

When I tried:
```
ls /ect/X11
```

I got:
no such file or directory

Now I'm starting to panic.
Sorry, my bad. Typo there, somehow misspelled etc. All the ect should be etc.

Anyway, best bet is just to do this;
```
dpkg-reconfigure xserver-xorg
```
Then just go through the interface and select nv for driver. Should get you going.

Sorry for the typo, lol.

---

### Post by kindafunnylookin on 2006-10-13
> 
Anyway, best bet is just to do this;
Code:

dpkg-reconfigure xserver-xorg

Then just go through the interface and select nv for driver. Should get you going.

THAT WORKED! Sorry about the volume but I'm a pretty happy noob.

This forum rocks.

---

### Post by kindafunnylookin on 2006-10-13
Crashmax--
I went back and checked the code and you did not make the typo. I did, thank you for the help.

---

### Post by Amackera on 2006-10-13
I too had this problem, and how whenever I try to boot Ubuntu, it tries to "check the kernel" (I think.. i could be wrong!)

It does the loading bar with the % to the right.. gets somewhere about 55-65% and finds an error.

I cannot boot any Ubuntu now (not any of my backups at all).

I'm just going to reinstall I think.](*,)

---

### Post by almahtar on 2006-10-13
Perhaps it's "checking the filesystem"?  Does it talk about something like "/dev/hda"?

---

