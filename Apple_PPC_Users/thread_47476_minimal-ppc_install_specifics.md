---
title: "minimal-ppc install specifics"
date: 2005-07-08
forum: Apple PPC Users
---

### Post by chascon on 2005-07-08
This is something I wrote up and I think is worth sharing.  There are various issues in this howto but I don't want to concern myself with fs flamewars.  I wouldn't mind knowing how to get around the fact that ubuntu closed the cups web-interface (I've tried messing with cups.conf? ), and how to adjust font sizes manually.

minimal ubuntu install

Use at your own discretion. By using the posted info, you agree to hold the responsibility of any results henceforth, not I. This document does not guarentee anything either.

I wanted to do a minimal install with ubuntu as I used to do with debian. I found out from [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Get yourself a very fast system, faster than the default ubuntu install. I did on my 400mhz iMac DV.

First of all, hoary has some multiseat problem with some computers. I got around it. I was able to circumvent the multiseat install failure using d-i's step by step menu selection. On the first pass it fails after naming hostname. You're still missing filling out the domain name, so I selected 'back' and reran network configuration (or the like). The second time around it fails after setting domain name, which is what I wanted.

I did a server install by typing server at the install prompt, I am using XFS for every partition on my '/', '/usr', '/var', 'swap', '/tmp', '/home' ('/boot' uses its own 'newworld boot parition').

Partitioning:

Hint: if you don't know how to create this multi-partition scheme, you can use sarge's|debian's credit card installer (burned onto a regular sized cd) to partition it. Just select multi-user setup. Once it formats and writes the partitions you can backout. If it starts to install the base install, just control-c to stop. Then backup to main menu, and reboot, then hold mouse down to spit out the credit card cd and reboot to OS X [if yaboot appears, hit x to boot OS X]). Then throw in the ubuntu cd, once in partitioning, accept manual partitioning, look over previously written-by-sarge partitions, and write it again. If you didn't set the fs types for the partitions before, you have to commit before writing again. Just highlight each partition and hit enter, then specify XFS (excecpt for '/boot' which gets a 'neworld boot partition'). You can also assign the mount point in that dialog window. This is just a matter of typing in '/home' for '/home', '/tmp' for '/tmp', and so forth (leave the swap partition alone).

Base install:

You then can apt-get a few things like your favorite window manager (I chose 'fluxbox'), 'xserver-org', 'xlibmesa-dri', and 'xfonts-base', 'xfonts-100dpi', 'xfonts-75dpi', 'xfonts-scalable' [perhaps 'configlet-frontends' as apt-get suggests it but I never do].

Xwindows:

To get X, run dpkg-configure xserver-xorg and mainly choose defaults. For mouse, /dev/input/mice has always worked for me (on my iMac and ibook). Or just boot up on a live cd (ie., ubuntu-ppc live) and copy the xorg.conf (or XF86Config or XF86Config-4 file) and throw it in to to the /etc/X11/. Rename it to xorg.conf if different.

Firewall:

install firestarter and configure it asap.

Acceleration:

With this minimal install and presumably more due to XFS, glxgears reports better performance. With a regular ubuntu install I'm sure I was getting an inconsistant rate circa to 400 FPS (peaking at about 416FPS on a good day regardless of wm), and now it is consistant 427FPS. My machines need 16 default depth for accel to work.

External firewire burner:

1) poweron the external, and throw in a written cd

2) install xcdroast and start it with sudo I believe, and let it scan for your external. This was easier than when I had gnome installed, as it immediately found my Liteon (packaged as a Lacie). With a full ubuntu install, I was beginning to think that gnome doesn't allow other cd apps to even 'see' my external.

Screen positioning:

xvidtune installs automatically. Start it up from term, modify, test. When happy with tests, press 'show' and take a note of the long line of numbers output in term. Highlight the line, and

vim /etc/X11/xorg.conf

and append the copied line below the resolution lines. Add the new line with ModeLine and append xvidtune's output after that with a space between.

Things left:

Printing:

I just don't understand how ubuntu has disabled the cups web-interface but apt-getting 'gnome-cups-manager' (and running it from command) should set up printers easily. Just run 'gnome-cups-manager' from term to start it.  Normally, on a minimal debian install I would install 'cupsys', and 'foomatic-bin'.  You can also install 'cupsysbsd' if necessary.  Then I would open a browser and point it to [http://localhost:](http://localhost:) 631 then sign in as user: root, password: ROOTPASSWORD and configure my printer.  Ubuntu doesn't allow this.  I don't need to know why as it is a security issue.  The root password gets carried as a simple text.  But I've read that this is really a security problem when the cups server changes from its default location.  I'm not sure if this helps in this case, but there is a firewall up, so can't the web-interface be enabled safely?

Font sizes:

Fonts are a little larger than I normally set it to but more than acceptable. I know these can be adjusted manually. More on this to come.

As far as performance, as I've said I find this faster than ext3 in almost every respect. The one exception is only the initial start of X (with startx at console). It's acceptable, but seems slower. Not a big deal for me.

Sound should be as easy as installing alsa-mixer or your favorite frontend which will install backend deps.  For reference and double checking, you can install alsa-base and alsa-utils as well as libcdaudio.so as backends.  To restart alsa after installing this software <noop>/etc/init.d/alsa restart</noop> should work.
The following two commands might be in order:
adduser YOUR_USERNAME audio
adduser YOUR_USERNAME cdrom


Previous trial with reiserfs:

I tried reiserfs prior to this with devastating results on the first reboot. It reported problems of corruption with the journal, irq problems (something I never have had with any mac OS or gnu-linux distro on the same exact hardware), and suggested rebooting with irqpoll. Reboot, halt, or shutdown -h now did not work. They returned a buffer?, I|O? error. I read and hear that ubuntu is going to push reiserfs in the future. Man I think this is a mistake. If Hans wants us to become alpha testers he better improve his software to the point where it is workable/stable, a point that makes the testing of his fs both mutually productive for the end user (in terms of user end stability) as it is for his, presumably, pet project. Seems more like a toy at this point in time, according to my limited experience.

Chascon

[http://ubuntuppc.info/61.html](http://ubuntuppc.info/61.html)

---

### Post by Rxke on 2005-07-09
binonabiso times out for me...

---

### Post by chascon on 2005-07-09
I just tried the minimal install on an old P1 I built and put reiserfs (version 3 I assume) on most partitions except /boot (as before with my iMac) and it surprisly seems much more stable than the ppc port.  I'd heard good things about reiserfs and sinse most of these these comments are proably coming from pc users I thought I owed it to see its performance on pc.  The only "problem" is a report of a dangling symlink and I don't think this is due the the fs. Hans and his team need to allocate a bit of time on the ppc port, as I see it.

---

