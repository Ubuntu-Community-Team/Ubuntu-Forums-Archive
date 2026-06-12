---
title: "FreeBSD is awesome"
date: 2008-04-17
forum: BSD
---

### Post by lespaul_rentals on 2008-04-17
I am now running FreeBSD 6.3 on my home server, powered on 24/7.  I use it for FTP access for my friends, as well as a BitTorrent seedbox.  Now, I know that this server is hardly mission-critical and even an operating system such as Windows XP could do the job, but I like running a server to help me learn more about Linux, and now BSD.  I had Ubuntu Server Edition 6.06 on it before, and that was stable and a great server operating system, but I was looking for something new.

What follows is a summary of my installation experience, if you care to read.

After popping in the disks, I was greated by a curses-based installer.  I like curses a lot more than GUI installers, since it's clean and simple.  Also, most of the time the developers assume you are an expert if you are installing a distro using a curses installer, so they throw in some advanced configuration options.  To use a simile that Linux users would understand, I found the installation process to be very similar to that of Slackware or Arch.

The partitioning process is different than Linux, but the tool they give you to use is reminiscent of cfdisk.  FreeBSD uses its special BSD filesystem, so don't expect to see familiar names such as ext3 or reiserfs in the mix.  However, you will recognize the need for a swap partition, so don't forget to throw that on the hard drive.

The installer gave me the option of installing some applications from the packages included on the CDs.  It worked okay, but it got annoying switching CDs about 20 times (keep that in mind before you install a bunch of extra applications from the CDs).  It also allows you to install the ports collection, which is a good idea, but don't forget to update the ports collection once finished installing.

Virtually everything can be configured through the installation.  It's concise and practical.  It's such a great installer, I can't get over it.  One of the options asks you if you would like to start sshd at boot.  I would recommend this, as you won't need a monitor after you finish the installation and can administer your server headlessly.

When you reboot into your new system, you'll be greeted by a login prompt that will be familiar to users of Slackware, Arch, and Gentoo.  You can login as root here, or if you added a seperate user during the install, you can login with that.

There's always been the sudo vs. su argument.  One of the points sudo supporters use to support their case is the fact that you can simply add or remove a user to the admin group in order to enable or disable their ability to switch to superuser mode.  In FreeBSD, users must be in the wheel group in order to run su.  So, if you want to disable an employee's ability to become superuser because he's been messing around, take him out of the wheel group.  I personally am a supporter of sudo, but FreeBSD's way of handling su is nearly perfect and I don't miss sudo at all.

The default text editors available in the command-line are ee and vi.  vi is definitely the "hacker's editor" and is great for some uses, but when editing a couple of lines in a configuration file, vi commands are just annoying.  My old favorite is nano, so I went about installing nano from ports.

About installing software, FreeBSD couldn't make it any easier.  If you are fine with binaries and like the speed and ease of a pre-compiled package for your architecture, **pkg_add** will do the job for you.  If you like to compile software so you can fine-tune what goes on during the installation process, ports is for you.  The way ports is set up is pretty ingenious.  To find where a port for your desired application resides, simply run **whereis [name of application]**.  I ran **whereis nano** and got the name of the directory.  All ports are organized under */usr/ports*, so all you have to do it change to the directory, and run **make install clean** as superuser.  Characters fly across the screen, stereotypical hacker movie stuff.

Configuration of services and daemons couldn't be any easier.  All config files are well documented and man pages are fantastic.  Configuration files reside in /etc, period.  No looking around the / partition for the neccessary files to modify.  Just go into /etc, look for the name of your service, and edit the file with your preferred text editor.  All logs are kept in /var/log, so no playing hide-and-seek with those, either.

Admittedly, FreeBSD falls short in the X11 area.  If you intend to get an X server running on your machine, you can have fun with that.  I read documentation, messed around with the configuration file, and Googled for a long time before I finally gave up.  After some thought, I realized it just wasn't worth my time.  This was supposed to be a headless server anyway.  However, I did want to run a couple of GUI applications in the background, namely KTorrent, which is my BitTorrent client of choice.  So, I turned to VNC.

VNC compiled and installed in about 30 minutes using ports.  Using my other computers, I was able to access the X session and run KTorrent, then logout and leave KTorrent to do its thing in the VNC session.  A functional, headless server, just like I set out to achieve.  :KS

FreeBSD borrows a lot of security ideas and a few applications from OpenBSD.  One example is the pf firewall.  It is much like the iptables firewall built into the Linux kernel, but even better.  I port scanned my FreeBSD server with nmap, and on the server's screen appeared a message that alerted me it was being port scanned, and the firewall actually adapted to block ports.  Also, if an SSH user changes to root, an alert appears on the console stating the name, date, and time the su command is run.  If you're on the wrong side of a bruteforce attack, a message will appear stating the attempted username and IP address of the attacker, so you can ban them.  It's clear FreeBSD was designed from the ground up to be the ultimate server operating system.

I'm still learning all the ins and outs of FreeBSD, but it's fantastic.  I can't help but smile every time I use it.  It's near perfect.  It's fast.  It's configurable.  It's stable.  It's the kind of operating system you could leave running with a UPS and never worry about hackers or crashes.

FreeBSD is a server masterpiece.

---

### Post by cardinals_fan on 2008-04-27
> **lespaul_rentals said:**
> 
FreeBSD is a server masterpiece.
And not a desktop masterpiece?

---

### Post by cammin on 2008-04-27
If he couldn't get X11 worked out, then he isn't going to make that claim.

---

### Post by cardinals_fan on 2008-04-27
> **cammin said:**
> If he couldn't get X11 worked out, then he isn't going to make that claim.
True enough, I'm just loving it on MY desktop.

---

### Post by stream303 on 2008-04-30
> **lespaul_rentals said:**
> The default text editors available in the command-line are ee and vi.

Wow - what a great writeup!  Thanks for sharing.

What amazed me was how something as simple as making a simple editor part of the install was a blessing for a guy like me who was already familiar with vi.  Using EE saved me countless hours of downtime when trying to help another admin over the phone, who wasn't so savvy with vi.

---

### Post by mips on 2008-04-30
> **stream303 said:**
> Wow - what a great writeup!  Thanks for sharing.

What amazed me was how something as simple as making a simple editor part of the install was a blessing for a guy like me who was already familiar with vi.  Using EE saved me countless hours of downtime when trying to help another admin over the phone, who wasn't so savvy with vi.

Never used EE, how does it compare to nano?
I cannot stand vi and to lazy to learn it. I wish they would include nano in more distros by default, at least give people the option of what editor they want to use.

---

### Post by seanc7 on 2008-05-01
I tried FreeBSD before I was really Unix proficient so I had a hard time with it but now that I'm fairly proficient. I do want to give it another try, I just need a new system that can run virtualisation.

---

### Post by TheS0urce on 2008-05-03
I tried desktopbsd which is based on freebsd 6.3.  Freebsd 6.3 wasn't stable for me it crashed on me 3 times so I gave up on freebsd and started playing with linux distro.  From what I read openbsd and netbsd is more clean and stable OS. Freebsd is more like bleeding edge especially the ports.  Many ports are outdated which can't be good either.  BSD I think it designed for server, look at freebsd 7 it has more features for servers not for desktop.

---

### Post by ibutho on 2008-05-03
> **TheS0urce said:**
> I tried desktopbsd which is based on freebsd 6.3.  Freebsd 6.3 wasn't stable for me it crashed on me 3 times so I gave up on freebsd and started playing with linux distro.  From what I read openbsd and netbsd is more clean and stable OS. Freebsd is more like bleeding edge especially the ports.  Many ports are outdated which can't be good either.  BSD I think it designed for server, look at freebsd 7 it has more features for servers not for desktop.

I know FreeBSD is popular on servers, but it works great on desktops as well. I use it on my main desktop machine (running KDE) and if its configured correctly you won't even notice the difference with Linux distros. I am not sure where you got the info about the stability of the different BSDs, but one thing to note is that they share a lot of code and ports as well as pkgsrc can be configured to only use stable packages if desired.

---

### Post by lespaul_rentals on 2008-05-05
> **stream303 said:**
> Wow - what a great writeup!  Thanks for sharing.

Thanks for the feedback.  Glad someone got something out of it.

---

### Post by sujoy on 2008-05-08
feeling tempted to try it out.

---

### Post by Iandefor on 2008-05-09
Good writeup; what problems did you have with X? I didn't have any, just pkg_add -r xorg.

---

### Post by stream303 on 2008-05-16
> **mips said:**
> Never used EE, how does it compare to nano?

No comparison. :) The ESCape key is your friend.  You can download and install it from the Ubuntu repositories to try it, just sudo apt-get install ee

> I cannot stand vi and to lazy to learn it. I wish they would include nano in more distros by default, at least give people the option of what editor they want to use.

And that was a BIG issue for FreeBSD.  After 386/BSD kind of died on the vine, it prompted FreeBSD into action to focus on getting BSD to the "common man" with a focus solely on a 386 - and part of the mantra was to make it friendlier to those who weren't in academia or research who had access to the big iron (well, medium iron perhaps.)  The EE editor fits into this focus nicely.

I forget if NetBSD (which also took off at nearly the same time due to the stagnation of 386/bsd) also provided the EE editor, but their focus wasn't specifically on the typical consumer desktop 386, but all the major architectures.

You can also get a taste of an older vi, which is Keith Bostic's NVI (new vi) if you don't like vim.  Also apt-gettable.  (It's a classic, but still updated - last update Dec 2007)

Anyway, I don't want to turn this into an editor war, but once I got my head past the whole "modal" concept, vi kind of took off for me.  I also wanted to see what it was like to run such a classic editor and found that I liked it.

---

### Post by techmarks on 2008-05-31
Xfce works now. I built Thunar because it wasn't compiled with file alteration monitor support by default.

---

### Post by Luke has no name on 2008-06-04
I like BSD's filesystem organization better. All config files in /etc, ALL user installed programs go in /usr. APACHE WEB FILES DO NOT BELONG IN /var! they belong in the Apache folder in /usr!

---

### Post by the8thstar on 2008-07-06
Is FreeBSD better than Ubuntu? (less bugs or crashes with as much bleeding edge I mean)

---

### Post by cardinals_fan on 2008-07-06
> **the8thstar said:**
> Is FreeBSD better than Ubuntu? (less bugs or crashes with as much bleeding edge I mean)
It's TOTALLY different, but much stabler.

---

### Post by arloth on 2008-07-07
I used to use FreeBSD often for my servers and actually had it on my desktop a bit, but it ended up being more of a hassle for me.  I'd been using it since 4.8, had mixed results with 5.5 etc.. and I think I gave up on it for the most part somewhere with the 6.x release.  It had it's moments, and I was pleased with it for the most part.  However I think maintaining an Ubuntu based system is much easier now. :-)

Sure it's stable, the ports system is somewhat nice and very easy to find software in.  However, it seemed more effort than it was worth.  For example, at the time they didn't support ext3, and used ufs for the standard file system. No journaling, big downer. I think they're finally on ext3, but most systems now have such big drives/raid on them I prefer to use XFS. I'm not sure if it supports XFS currently, but I got bit by UFS so I may just be blowing smoke on this point. ;-)

Their support for realtek based network cards was shoddy, particularly ones with the 8139, and I was often met with a response of "Go buy a real network card".  Finding a network card that was affordable, and not based on this chip was a nightmare. For several months I ended up running a particular machine off of a very old 3com USB ethernet adapter simply because it worked.

If you keep your computer with the same FreeBSD version on it, but try and get security updates through the ports you'll eventually land in dependency hell.  For example, when updating PHP it would consistently remove the PHP module lines from my apache config files but not put them back in.  The next time apache would restart - bam! No more php.  Other times it would do stupid things and I would find myself manually removing and reinstalling things because the dependencies weren't being met properly.

There were several other gotchas with the ports index that were annoying, ie, doing a make index versus fetching it.  make index would usually get you better, more reliable and consistent results, but running it on anything but current hardware takes forever.

It has it's good points, but it's not for me. At least, not anymore.  I want to spend more time enjoying my computer than updating software and futzing with all manner of file in /etc.  You can take my ubuntu from me when you pry it from my cold dead hands. ;-)

---

### Post by cpcnw on 2008-07-08
root# cd /usr/ports/x11/xorg/
root# make install
root# exit
admin# startx

Following that a single .twmrc will give you a basic desktop

[http://212.159.115.167/twm/twmrc.htm](http://212.159.115.167/twm/twmrc.htm)

Compiling KDE or Gnome oe Xfce may take a bit longer :)

Yep, FreeBSD makes an amazing server [my last server uptime on FreeBSD was 1.5 years before I did a major version UG] and can make a nice desktop but you may have to put a bit more work in than current 'out of the box' Linux distro's. The base system however is well engineered and the documentation superb. Ports are only out of date if you dont update them -or if they are actually abandoned projects [twm?] Over the years most issues I came across where the result of me not reading the doco properly.

---

