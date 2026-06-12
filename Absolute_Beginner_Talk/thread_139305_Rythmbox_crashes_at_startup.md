---
title: "Rythmbox crashes at startup"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by PeopleEater on 2006-03-03
Hi, I installed Ubuntu on my computer about a week ago and have so far been really impressed with it. The few problems I've had with it I was able to find fixes for quit quickly but this one has got me stumped. Every time I try to start Rhythmbox it crashes and gives me the message "The Application "rhythmbox" has quit unexpectedly."

I tried running it from the terminal and got this:

> Attempt to remove filter function 0xb7fb3721 user data 0x836d848, but no such filter has been added
Attempt to remove filter function 0xb7fb3721 user data 0x836d848, but no such filter has been added

GLib-ERROR **: gmem.c:141: failed to allocate 1882140476 bytes
aborting...


Can someone please tell me how to fix this?

---

### Post by Pragmatist on 2006-03-04
Can you consistently duplicate this error?  Even after rebooting the machine?  How about trying to start the program as root ```
sudo rhythmbox
```

---

### Post by PeopleEater on 2006-03-05
Thanks for your help but I think I figured out how to fix my problem. Since I noticed there was a line mentioning glib I went into synaptic and reinstalled all the packages that had something to do with glib and it seems to be working fine now. This also seems to have fixed a problem I was having with banshee.

---

### Post by PeopleEater on 2006-03-05
I've found the reason it was crashing. Both rhythmbox and banshee won't work when I have my iPod connected. Is there any way to fix this?

---

### Post by Pragmatist on 2006-03-05
> Both rhythmbox and banshee won't work
Specifically what happens.  Do you get an error message?  Try running the programs from a terminal instead of a menu and check for error messages.
```
rhythmbox
```
```
banshee
```

Also try running those in a terminal as root:
```
sudo rhythmbox
```
```
sudo banshee
```

---

### Post by PeopleEater on 2006-03-05
Sorry for not being specific enough. When I try to run rhythmbox it starts but then gives me the same error from my first post aswell as the same entry in the  terminal.

> (rhythmbox:14906): Rhythmbox-CRITICAL **: couldn't connect to session bus: No reply within specified time
Attempt to remove filter function 0xb7f37721 user data 0x836b078, but no such filter has been added
Attempt to remove filter function 0xb7f37721 user data 0x836b078, but no such filter has been added

GLib-ERROR **: gmem.c:141: failed to allocate 1882140476 bytes
aborting...


When I try to run banshee it says starting banshee in my window list but then just disapears and nothing happens. I get the following in the terminal.

> 
** (<unknown>:14866): WARNING **: Symbol file /usr/lib/mono/gac/dbus-sharp/0.36.2.0__9eef2692033670f5/dbus-sharp.dll.mdb has incorrect version (expected 39, got 38)
Warning: [05/03/2006 4:47:02 PM] (Cannot connect to NetworkManager) - An available working network connection will be assumed
Debug: [05/03/2006 4:47:03 PM] (Changed active playback engine) - GStreamer
Debug: [05/03/2006 4:47:03 PM] (Loaded primary playback engine) - GStreamer
Debug: [05/03/2006 4:47:03 PM] (Loaded Audio CD playback engine) - GStreamer
Debug: [05/03/2006 4:47:03 PM] (Audio CD Core Initialized) -

Unhandled Exception: System.DllNotFoundException: libdbus-1.so.2
in (wrapper managed-to-native) Hal.DBusError:dbus_error_init (intptr)
in [0x00033] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/hal-sharp/DBusError.cs:39) Hal.DBusError:.ctor ()
in [0x00000] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/hal-sharp/HalDevice.cs:191) Hal.Device:set_WatchProperties (Boolean value)
in [0x0008f] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:178) Banshee.Dap.DapCore:AddDevice (Hal.Device device, System.Type type)
in [0x0001e] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:161) Banshee.Dap.DapCore:AddDevice (Hal.Device device)
in [0x0001b] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:154) Banshee.Dap.DapCore:BuildDeviceTable ()
in [0x0002b] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Dap/DapCore.cs:126) Banshee.Dap.DapCore:Initialize ()
in [0x00091] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Banshee.Base/Globals.cs:71) Banshee.Base.Globals:Initialize ()
in [0x001b3] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Main.cs:91) Banshee.BansheeEntry:Startup (System.String[] args)
in [0x00001] (at /tmp/buildd/banshee-0.10.4-2~filefind.net/src/Main.cs:57) Banshee.BansheeEntry:Main (System.String[] args)


I get the same results if I try to run them as root.

---

### Post by Pragmatist on 2006-03-05
go into synaptic and do a search for **libdbus**
```
sudo synaptic
```

I would try installing: **libdbus-1-dev**  Sometimes problems are solved when you install the corresponding development library.

See what that does and let us know.

---

### Post by PeopleEater on 2006-03-05
Thanks for the suggestion but I already have that installed.

---

### Post by Pragmatist on 2006-03-05
Is dbus running? What is the output of:
```
ps -ef |grep dbus
```

---

### Post by PeopleEater on 2006-03-05
Hope this helps.

> 105       7881     1  0 20:06 ?        00:00:00 /usr/bin/dbus-daemon --system
garrett   8843  8800  0 20:21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
garrett   8846     1  0 20:21 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
garrett   8847     1  0 20:21 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
garrett  11791 11780  0 22:02 pts/0    00:00:00 grep dbus


---

### Post by Pragmatist on 2006-03-05
Just found this and I think it will help:
[http://patches.ximian.com/Troubleshooting/iPod](http://patches.ximian.com/Troubleshooting/iPod)

---

### Post by PeopleEater on 2006-03-06
Thanks for the suggestion but I'm don't think I'm having problems with the programs recognizing the iPod because if I start rhythmbox with it plugged in the main screen I can see the ipod in the side list under radio of coarse it also gives me the error message and forces me to quit it. I tryed installing the to things it recommended and once I finnaly got them installed there was still no change in my errors.

---

### Post by Pragmatist on 2006-03-06
So does this mean that you tried running ```
hal-device-manager
``` and ```
ipod
``` commands??

---

### Post by Pragmatist on 2006-03-06
Also have you tried running **gtkpod**  Even if that isn't your favorite app, it could help in troubleshooting the others.

---

### Post by PeopleEater on 2006-03-06
Yes i have tryed both commands and they work fine my ipod is mounted and gtkpod works fine it's just these other 2 programs that won't work when I have my iPod connected.

---

### Post by Pragmatist on 2006-03-06
Two questions:
1.) What happens if you run ```
sudo ldconfig
``` and then try opening the programs (particularly banshee)

2.) How much memory does your ipod hold?  How much of that memory is being used?

---

### Post by PeopleEater on 2006-03-06
1) Nothin changes they do the same thing both when ran as root and a normal user.

2)It's a 30GB video with about 5GB on it.

---

### Post by Pragmatist on 2006-03-07
1. Is there any difference between starting the programs with the ipod connected and starting the program and only then connecting the ipod?

2. Is there any difference if you boot your computer with the ipod connected or if you connect the ipod after the computer is already booted?

See the problem your having is unusual for these reasons:

1.) both programs (banshee and rhythmbox) both work, just not with the ipod connected.
2.) the ipod works, just not with banshee and rhythmbox
3.) the error messages are totally different for rhythmbox and for banshee

So the problem is not inherently with either the programs or the computer's recognition of the ipod.  It is some weird interaction of the two. And, because the error messages are different, it easily could be that there is one reason why it isn't working in rhythmbox and another why it isn't working in banshee.  A missing library would definitely explain it which is why I mentioned that library early on and why I also suggested ldconfig.

Also, the error message you got for rhythmbox is very unusual (I typed it in on linux google and got only about 2 hits and both had to do with libraries)

I'll try and see if I can find some mailing-list archives for both programs.

---

### Post by PeopleEater on 2006-03-07
1.There is no difference between starting the program with it connected or connecting it while it's running if it's banshee it will just close and rhythmbox will give me the error message then close.

2.There is no difference between botting with the it connected or disconneted.

---

### Post by Pragmatist on 2006-03-07
Ok, finally I got smart and checked the ubuntu bug database.  This person has exactly the same problem you have with rhythmbox:
[https://launchpad.net/distros/ubuntu/+source/rhythmbox/+bug/3763](https://launchpad.net/distros/ubuntu/+source/rhythmbox/+bug/3763)

For banshee I didn't check all of the bugs (there are like 40).  However, at least two of them were solved by updating to a newer version.  This is the key one and it mentions a very recent upgrade:
[https://launchpad.net/distros/ubuntu/+source/banshee/+bug/31462](https://launchpad.net/distros/ubuntu/+source/banshee/+bug/31462)

 Your running 0.10.4-2  you need to upgrade. Here is the .deb file:

[http://librarian.launchpad.net/1573304/banshee_0.10.6-0ubuntu1_i386.deb](http://librarian.launchpad.net/1573304/banshee_0.10.6-0ubuntu1_i386.deb)

To read more about banshee to a search here (all of ubuntu forums) using the search term "banshee dbus"  You could do the same at the bug database: [https://launchpad.net/malone/distros/ubuntu](https://launchpad.net/malone/distros/ubuntu)

---

### Post by PeopleEater on 2006-03-08
Thanks for the suggestion but im having a very hard time finding the dependancies for banshee and was wondering if you knew of an easier way of finding them.

> Selecting previously deselected package banshee.
(Reading database ... 96528 files and directories currently installed.)
Unpacking banshee (from .../banshee_0.10.6-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of banshee:
 banshee depends on libbonobo2-0 (>= 2.13.0); however:
  Version of libbonobo2-0 on system is 2.10.1-0ubuntu1.
 banshee depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.
 banshee depends on libdbus-1-2 (>= 0.60); however:
  Package libdbus-1-2 is not installed.
 banshee depends on libdbus-glib-1-2 (>= 0.60); however:
  Package libdbus-glib-1-2 is not installed.
 banshee depends on libglib2.0-0 (>= 2.9.3); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 banshee depends on libgnomeui-0 (>= 2.13.0); however:
  Version of libgnomeui-0 on system is 2.12.0-0ubuntu1.
 banshee depends on libgnomevfs2-0 (>= 2.13.4); however:
  Version of libgnomevfs2-0 on system is 2.12.1-0ubuntu2.
 banshee depends on libnautilus-burn3; however:
  Package libnautilus-burn3 is not installed.
 banshee depends on libpango1.0-0 (>= 1.11.5); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 banshee depends on libxml2 (>= 2.6.23); however:
  Version of libxml2 on system is 2.6.21-0ubuntu1.
 banshee depends on libbonobo2-0 (>= 2.13.0); however:
  Version of libbonobo2-0 on system is 2.10.1-0ubuntu1.
 banshee depends on libdbus-1-2 (>= 0.60); however:
  Package libdbus-1-2 is not installed.
 banshee depends on libdbus-1-cil (>= 0.60); however:
  Version of libdbus-1-cil on system is 0.36.2-0ubuntu7.
 banshee depends on libdbus-glib-1-2 (>= 0.60); however:
  Package libdbus-glib-1-2 is not installed.
 banshee depends on libglib2.0-0 (>= 2.9.3); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 banshee depends on libipoddevice0 (>= 0.4.1); however:
  Version of libipoddevice0 on system is 0.3.5-0filefind.net-breezy0.
 banshee depends on libmusicbrainz4c2a (>= 2.1.2); however:
  Package libmusicbrainz4c2a is not installed.
 banshee depends on libnautilus-burn3; however:
  Package libnautilus-burn3 is not installed.
 banshee depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Version of gconf2 on system is 2.12.0-0ubuntu1.
dpkg: error processing banshee (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 banshee

---

### Post by Pragmatist on 2006-03-08
try this:
 ```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```
This will upgrade your packages to the newer versions.  There might be more dependencies but the list won't be that big :)

---

