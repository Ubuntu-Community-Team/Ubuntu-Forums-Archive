---
title: "X server config"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mowcius on 2007-04-05
X server config 

I put this post on about an hour and a half a go and am wondering if someone has the answer now.

part way through the x server config my computer is asking me what the desired default color depth in bits is

i selected 24

then it came up with a message at the bottom saying:

x server-xorg postinst warning: over possibly-customised configuration
file backup; in /etc/x1/xorg.conf. 20070404210759

it then came up with the command prompt

what do i do?

---

### Post by mac.ryan on 2007-04-05
I understand you had a previously working installation that went broken when you tried to tweak it... if my understanding is correct then you can try:

Look into your /etc/X11 directory, delete (or rename) your current xorg.conf and rename one of the backups (possibly the one suggested by your error message) into xorg.conf.

Then you should be able to log in again in graphical way. To try, just type "startx" in the shell promt.

Best luck!

---

### Post by Mowcius on 2007-04-05
i didn't have a previously working workstation

i've never got it to work

thanks anyway

---

### Post by teaker1s on 2007-04-05
```
lspci | grep VGA
``` please type this and tell us output, It's quite possible that you have a graphics card that needs a little setting up.

Also you could try
```
sudo dpkg-reconfigure xserver-xorg
``` and try **vesa** as driver until we sort out exactly the issue

---

### Post by Mowcius on 2007-04-05
i've allready tried 

sudo dpkg-reconfigure xserver-xorg

that's what it came up in

and how do you type a vertical line

---

### Post by julian67 on 2007-04-05
> **Mowcius said:**
> X server config 

I put this post on about an hour and a half a go and am wondering if someone has the answer now.

part way through the x server config my computer is asking me what the desired default color depth in bits is

i selected 24

then it came up with a message at the bottom saying:

x server-xorg postinst warning: over possibly-customised configuration
file backup; in /etc/x1/xorg.conf. 20070404210759

it then came up with the command prompt

what do i do?

The configuration tool is just warning you that it has written you a new xorg.conf and backed up your old one as xorg.conf. 20070404210759. The standard xorg.conf  from an ubuntu install is non standard (various expected paramenters are not present such as monitor size) so the tool recognised this as one that you might have customised and alerts you to this in case you want to examine your customised config and apply any customised parts to the new one. I wouldn't worry about it unless find something doesn't function as expected/wanted in which case you can check the 2 files for the differences and use the settings from the old one that did work.

To type a | on a US keyboard look at the key above "Enter". It's the broken vertical line. On a UK keyboard the key is to the left of Z

---

### Post by Mowcius on 2007-04-05
it comes up with the command prompt and then won't let me do anything else

and it doesn't do anything else either

just sits there as though it's laughing at me!

---

### Post by julian67 on 2007-04-05
So instead open a terminal and type ```
lspci
``` and hit return.  Copy the result and post it here, then anyone who tries to help you can see what hardware you have there.

---

