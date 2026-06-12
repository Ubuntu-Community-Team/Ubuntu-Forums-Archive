---
title: "installing real player 10"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by scoldingice on 2005-10-16
ok i'm trying to install realplayer 10 for linux. i went out and downloaded the packet. it is labeled "realplayer10gold.bin". on the web site they give this set on instructions... 


Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

when i went to do the frist set of instructions that they gave i got this

root@brian-ubuntu:/home/moneyman # chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
root@brian-ubuntu:/home/moneyman #

please help.

the website is [http://www.real.com/linux]("http://www.real.com/linux")

---

### Post by irifan on 2005-10-16
Hi,

have you checked if the Realplayer file is actually in the /home/moneyman direcory?

Places -> Search for files
will help.

---

### Post by scoldingice on 2005-10-16
thanks man itw was supposed to be in that folder instead of on the desktop. thankyou very much

---

### Post by homerhomer on 2005-11-12
not supported but this seems to work for me

[http://ftp.debian-unofficial.org/deb...rge.1_i386.deb](http://ftp.debian-unofficial.org/deb...rge.1_i386.deb)

*note* I didn't have video until I turned of Acceleration *

---

### Post by kelsey23 on 2005-11-12
You don't want RealPlayer 10. Trust me. A great way to get spyware for you GNU/Linux box.

---

### Post by mattotoole on 2005-11-14
The instructions are fine, except for one thing -- where's the best place to put it?  Certainly not in your home directory.  /usr/bin?  /opt?  Then how do you get it to work with your browser, etc?

The script creates a directory RealPlayer, with a bunch of directories inside it, for plugins, etc.  The path to execute is then /foo/RealPlayer/realplay.

---

