---
title: "Problem installing the xserver on Ubuntu Server 7.10 (Gutsy)."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Bensky on 2007-11-11
I installed Ubuntu 7.10 server on vmware yesterday and everything is working fine, got apache and everything working. 

I'm fine with using terminal to do everything, but I want to install a very lightweight window manager (like fluxbox or xfce) as well, and my server is not going to have very much traffic, so I figured I could install one without performance problems. I figured I would install the xserver first and then go from there. So I got xfree86, then when I ran "startx" it appeared to work OK at first, but I got this error message soon after and it closed:

"Fatal server error:
No valid FontPath could be found."

I also noticed at the very top:
"X: Warning; process set to priority -1 instead of requested priority 0"

I read somewhere that that fontpath error message means that you're missing the misc. x11 fonts, but I couldn't find a package with the fonts in them to download (there was a package listed but it appears that it doesn't exist). :confused:

---

### Post by chunderbunny on 2007-11-11
The xfree86 xserver is deprecated in Ubuntu (and most other 'nix distros), what you really want is the *xserver-xorg-core* package. 

Probably the easiest way to fix your issue would be to uninstall xfree86, and then install fluxbox or xfce directly, using apt-get. The package manager should pull in all the necessary packages automatically. 

Once done you will need to run "sudo dpkg-reconfigure -phigh xserver-xorg" to make sure all the xorg config files are set up correctly.

---

### Post by Bensky on 2007-11-11
> **chunderbunny said:**
> The xfree86 xserver is deprecated in Ubuntu (and most other 'nix distros), what you really want is the *xserver-xorg-core* package. 

Probably the easiest way to fix your issue would be to uninstall xfree86, and then install fluxbox or xfce directly, using apt-get. The package manager should pull in all the necessary packages automatically. 

Once done you will need to run "sudo dpkg-reconfigure -phigh xserver-xorg" to make sure all the xorg config files are set up correctly.

Thanks, the command to remove xfree86 would be:
"sudo apt-get remove xfree86-xorg" ? It says it will only free up like 26k of space, is the xserver that small? lol

---

### Post by Bensky on 2007-11-11
This doesn't look good, I did "sudo apt-get install xfce4" which appeared to be the main package, since it downloaded a bunch of xfce related packages. It finished setting up/configuring everything but gave me no messages or anything.

I then tried your reconfigure command, it and gave me this:
"/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed"

I also tried "startx," which gave me:

"/etc/X11/X is not executable
xinit: server error."
then it closed.

I'm thinking some stuff was left over from xfree86, I looked in my xorg.conf file and saw the lines where I tried to put the fonts in when I still had xFree86. >_<

---

### Post by Bensky on 2007-11-11
Bump. :\ Still can't get it working.

---

### Post by Bensky on 2007-11-11
Anyone? D:

---

### Post by Bensky on 2007-11-12
Ok, uhh...bump. :) anyone?!

I found another package: "xubuntu-desktop." Would that have the same effect as installing the "xfce4" package?

---

### Post by zvacet on 2007-11-12
```
sudo apt-get -f install
```

That should correct problems.If not 

```
sudo aptitude remove --purge xfce4
```

and if you want to install xubuntu

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by Brian96 on 2007-11-21
> **chunderbunny said:**
> The xfree86 xserver is deprecated in Ubuntu (and most other 'nix distros), what you really want is the *xserver-xorg-core* package. 

Probably the easiest way to fix your issue would be to uninstall xfree86, and then install fluxbox or xfce directly, using apt-get. The package manager should pull in all the necessary packages automatically. 

Once done you will need to run "sudo dpkg-reconfigure -phigh xserver-xorg" to make sure all the xorg config files are set up correctly.

I'm having the same problem, and these suggestions have not worked for me.

In Feisty I could do a server install and then install xorg, gnome-core (or xfce3) and gdm, reboot, and all was golden. In Gutsy, however, after a server install and reboot I get hung up at "Running local boot scripts." I can hit enter and get to a log-in, from which I have tried installing xorg (and alternately xserver-xorg-core) and my DE of choice, but on reboot I get hung up at the same spot. I hit enter, login, then type "startx" and get the same error message.

However, a normal install boots fine. It's just the server install and the server plus manual DE install I have trouble with. Any suggestions?

---

### Post by Brian96 on 2007-11-21
> **Brian96 said:**
> I'm having the same problem, and these suggestions have not worked for me.

In Feisty I could do a server install and then install xorg, gnome-core (or xfce3) and gdm, reboot, and all was golden. In Gutsy, however, after a server install and reboot I get hung up at "Running local boot scripts." I can hit enter and get to a log-in, from which I have tried installing xorg (and alternately xserver-xorg-core) and my DE of choice, but on reboot I get hung up at the same spot. I hit enter, login, then type "startx" and get the same error message.

However, a normal install boots fine. It's just the server install and the server plus manual DE install I have trouble with. Any suggestions?

Okay, I got it working by first installing xserver-xorg-core, then manually installing xfonts-base and discover1. This solved the font error message and helped the xserver autodetect my video card so I got the right drivers. Then I ran startx and got x running, so I went back and installed gnome-core and gdm. It is still a little buggy, but I can at least get into the GUI.

---

