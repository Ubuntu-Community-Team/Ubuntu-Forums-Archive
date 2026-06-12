---
title: "Sound Gone!!!Urgent help required."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-11-26
Hi,
I use Ubuntu 7.10.
I read the undermentioned thread.
> [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)
Then I followed the instructions and got the alsa-driver, lib, utils (1.0.15 version) and installed them.
After Reboot my sound is gone. The volume control icon in the panel shows a cross(X red in colour).
My sound was working perfectly before installing 1.0.15 version.
Please help me to either uninstall it and get my previous ver or make this work.
(Synaptic manager still shows 1.0.14 as installed - which was default with LiveCD.)
Urgent help needed please.
My card is Intel ICH6 and model type is ALC880.
many thanks in advance.
:confused::confused::confused:

---

### Post by kpkeerthi on 2007-11-26
Go into the directory of the program(s) you compiled and type
```

make uninstall

```

And install the below using synaptic:
```

alsa-base
alsa-utils
alsa-tools
alsa-oss

```

Just curious. Did your sound ever work? Then why did you compile from the sources? And did you not back up your system?

---

### Post by Slakker on 2007-11-26
Did you maybe just hit a mute key on your keyboard or something?

---

### Post by gupta_sumesh63 on 2007-11-26
yes kpkeerthi. My sound was working absolutely fine before i tried to get the newer als version. trying to do what you advised. will be back. Thanks.

---

### Post by gupta_sumesh63 on 2007-11-26
I did the make uninstall but now my desktop is gone. help please. helpppppppppp!

---

### Post by Sef on 2007-11-26
> I did the make uninstall but now my desktop is gone. help please. helpppppppppp!

From the terminal or command line:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by gupta_sumesh63 on 2007-11-26
I have already installed ubuntu-desktop after the problem. During login it says something like could not load Gtk session.
could not locate libasound.so.2.
I have to perforce login in failsafe terminal.
What could be the problem please.
Thanks for any help.

---

### Post by gupta_sumesh63 on 2007-11-26
Whenever I login it says try failsafe method for logging.
The xsession-errors file is thus:
> (process: 5266): Gtk-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details see : [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)
refusing to initiate GTK+.

[QUOTE](process: 5270):  Same warning as above.

/etc/gdm/xsession: Begining session setup..............
x-session-manager: error while loading shared libraries: libasound.so.2:cannot open shared object file: No such file or directory.


When I run sudo startx from the terminal I get the following:
Fatal server error:
server is already active for dispaly 0.
if this server is no longer running, remove /tmp/.XO-lock and start again.[/QUOTE]

What should I do. Someone please guide me so that I dont have to reload Ubuntu again.

thanks in advance.

---

### Post by nnamdi on 2007-11-26
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

check that first simply do this

 lspci -v | grep Audio

and i got this
pradeep@pradeep-laptop:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

then click the above link and follow the instructions ok

---

