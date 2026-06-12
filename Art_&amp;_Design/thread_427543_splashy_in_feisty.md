---
title: "splashy in feisty?"
date: 2007-04-29
forum: Art &amp; Design
---

### Post by theonlykman on 2007-04-29
hey, does anybody know how to install splashy in feisty? I went off an old howto for edgy and it doesnt work. After doing splashy_config the themes installed without error (I tried a couple of different ones), but all that I get on boot up is a black screen with verbose messages.
Thanks

---

### Post by lyceum on 2007-04-30
Are you using the gnome splash-screen manager? You can get it from Synaptic Package Manager. It is the easiest way I have found to change the splash screen.

---

### Post by sorcererx84 on 2007-05-05
Same problem here. No splash, just boot messages.

---

### Post by lyceum on 2007-05-06
> **sorcererx84 said:**
> Same problem here. No splash, just boot messages.

Have you installed the Splash screen manger? 

System/Administration/Synaptic Package Manager

It is listed as "gnome-splashscreen manager"

Once installed you can turn on and off your splash screen and easily change the image.

---

### Post by Hairy_Palms on 2007-05-07
gnome-splashscreen-mananger isnt what theyre looking for, that only controls the gnome splash.
they are trying to use splashy which is an alternative to ubuntus usplash.

---

### Post by lyceum on 2007-05-07
> **Hairy_Palms said:**
> gnome-splashscreen-mananger isnt what theyre looking for, that only controls the gnome splash.
they are trying to use splashy which is an alternative to ubuntus usplash.

oh... sorry

---

### Post by theonlykman on 2007-05-10
no problem....Im thinking that Splashy is broken in Feisty...or maybe just broken in general?

---

### Post by andrewpsy on 2007-05-11
hi, how could you get rid of that ubuntu default splash image?

thx a lot.

---

### Post by islet8 on 2007-05-12
> **theonlykman said:**
> hey, does anybody know how to install splashy in feisty? I went off an old howto for edgy and it doesnt work. After doing splashy_config the themes installed without error (I tried a couple of different ones), but all that I get on boot up is a black screen with verbose messages.
Thanks

I've got the same problem, it bothered me a lot.
Who knows how to solve it, thx a lot!

---

### Post by Hairy_Palms on 2007-05-12
the short answer, find a usplash theme, 
plenty on gnome-look
[http://www.gnome-look.org/content/show.php/Archlinux+USplash+Theme?content=52066](http://www.gnome-look.org/content/show.php/Archlinux+USplash+Theme?content=52066) for example
then copy it to /usr/lib/usplash/uplash-artwork.so
and then run "sudo dpkg-reconfigure linux-image-2.6.20-15-generic"
replace 2.60.20-15-generic with your kernels name voila new usplash.

---

### Post by islet8 on 2007-05-12
> **Hairy_Palms said:**
> the short answer, find a usplash theme, 
plenty on gnome-look
[http://www.gnome-look.org/content/show.php/Archlinux+USplash+Theme?content=52066](http://www.gnome-look.org/content/show.php/Archlinux+USplash+Theme?content=52066) for example
then copy it to /usr/lib/usplash/uplash-artwork.so
and then run "sudo dpkg-reconfigure linux-image-2.6.20-15-generic"
replace 2.60.20-15-generic with your kernels name voila new usplash.

but if we want to use splashy rather than usplash? how should we do?

---

### Post by sandman55 on 2007-05-12
Are you guys talking about grub boot splash screens or something else

---

### Post by Hairy_Palms on 2007-05-12
talking about the bootsplash theme, i havent used splashy since usplash was introduced, but they have an official guide on their website

[http://splashy.alioth.debian.org/wiki/doku.php?id=installation](http://splashy.alioth.debian.org/wiki/doku.php?id=installation)

---

### Post by islet8 on 2007-05-13
[http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions](http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions)

here seems to be a solution for this problem, but it still does not work on my ubuntu.
my /etc/event.d/rcS is as follows:
> # rcS - runlevel compatibility
#
# This task runs the old sysv-rc startup scripts.

start on startup

stop on runlevel

# Note: there can be no previous runlevel here, if we have one it's bad
# information (we enter rc1 not rcS for maintenance).
console output
script
	#runlevel --set S >/dev/null || true
	#PREVLEVEL=N
	#RUNLEVEL=S
	#export PREVLEVEL RUNLEVEL

	set $(runlevel --set S || true)
	if [ "$1" != "unknown" ]; then
		PREVLEVEL=$1
		RUNLEVEL=$2
		export PREVLEVEL RUNLEVEL
	fi

	exec /etc/init.d/rcS
end script
what's wrong?

---

### Post by sandman55 on 2007-05-13
Hi guys Herman has a good guide [Here](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) just scroll down to "Add a splashimage to the GRUB menu"

---

### Post by islet8 on 2007-05-13
> **sandman55 said:**
> Hi guys Herman has a good guide [Here](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) just scroll down to "Add a splashimage to the GRUB menu"

we are talking about **usplash**, not *splashimage for grub menu*!

---

### Post by sandman55 on 2007-05-13
Sorry about that Ive been following up some links and I've just realized I'm on the wrong track

---

