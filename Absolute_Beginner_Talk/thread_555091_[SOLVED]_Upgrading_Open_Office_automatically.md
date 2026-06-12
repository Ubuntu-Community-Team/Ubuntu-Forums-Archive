---
title: "[SOLVED] Upgrading Open Office automatically"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by MrDiaz on 2007-09-19
Hi, I was wondering if there is a way to update Open Office from either the terminal or our package manager? Or my only choice is downloading the tar file and install it manually?

Thanks.

---

### Post by MrDiaz on 2007-09-19
anyone? :(

---

### Post by Dougie187 on 2007-09-19
not sure if there is one yet, but you could just wait until the updated version gets put in the repositories. it takes a bit of time, especially since it just came out. but if you are feeling impatient just get the tar and do it yourself. People on here can help you out if you need.

---

### Post by Maestro23 on 2007-09-19
If you want OO 2.3 you can either wait for Gutsy 7.10 (comes installed from what I hear) or download the tarball from OpenOffice.org and install on your system.

---

### Post by MrDiaz on 2007-09-20
> **Maestro23 said:**
> If you want OO 2.3 you can either wait for Gutsy 7.10 (comes installed from what I hear) or download the tarball from OpenOffice.org and install on your system.

But that is coming out around October right? Still a while to get there  :P

---

### Post by Maestro23 on 2007-09-20
> **MrDiaz said:**
> But that is coming out around October right? Still a while to get there  :P

Are we there yet Papa Smurf... :smile:

Yep, I believe 18 October is the date. That's why I said if you really wanted it now, you can install the package from OO.org.

---

### Post by forestpixie on 2007-09-20
> But that is coming out around October right?
apparently so 

it's quite easy to install it from the download if you feel you need to :)

Edit - as he ~(or she) said :) slow fingers here

---

### Post by Maestro23 on 2007-09-20
> **forestpixie said:**
> apparently so 

it's quite easy to install it from the download if you feel you need to :)

Edit - as he ~(or she) said :) slow fingers here

He... :lolflag:

---

### Post by forestpixie on 2007-09-20
you can never tell - who's to say MrDiaz is male :lol:

---

### Post by Maestro23 on 2007-09-20
> **forestpixie said:**
> you can never tell - who's to say MrDiaz is male :lol:

True... :smile:

---

### Post by chrismine on 2007-09-20
Openoffice 2.3 is already in the Gutsy repo's. I am running it as of a few days ago.

Be careful when installing from source - it may give problems when you wants to do a distribution upgrade.

---

### Post by ukripper on 2007-09-20
Try this - [http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

Go to Update section and install using deb package as shown

---

### Post by slymi2005 on 2007-09-23
i downloaded the deb files but i get this when i follow the tutorial above:

tar zxvf OOo_2.3.0_LinuxIntel_install_en-US_deb.tar.gz
tar: OOo_2.3.0_LinuxIntel_install_en-US_deb.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

any ideas?

---

### Post by nikoPSK on 2007-09-23
just go to synaptic search "openoffice" or "office" or something then if there is a little star beside openoffice click on it and mark for upgrade. Otherwise just wait or go to update manager then check.):P

---

### Post by Maestro23 on 2007-09-23
> **slymi2005 said:**
> i downloaded the deb files but i get this when i follow the tutorial above:

tar zxvf OOo_2.3.0_LinuxIntel_install_en-US_deb.tar.gz
tar: OOo_2.3.0_LinuxIntel_install_en-US_deb.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

any ideas?

You need to navigate to where you saved the file.  Example, if you saved it on your Desktop:

> cd /home/username/Desktop (Capital D)

Then run your tar command.

---

### Post by slymi2005 on 2007-09-23
I did what you said and it gave me this:

~/Desktop$ tar zxvf OOo_2.3.0_LinuxIntel_install_en-US_deb.tar.gz
OOG680_m5_native_packed-1_en-US.9221/
OOG680_m5_native_packed-1_en-US.9221/readmes/
OOG680_m5_native_packed-1_en-US.9221/readmes/README_en-US.html
OOG680_m5_native_packed-1_en-US.9221/readmes/README_en-US
OOG680_m5_native_packed-1_en-US.9221/licenses/
OOG680_m5_native_packed-1_en-US.9221/licenses/LICENSE_en-US
OOG680_m5_native_packed-1_en-US.9221/licenses/LICENSE_en-US.html
OOG680_m5_native_packed-1_en-US.9221/DEBS/
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core03u_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core05u_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-pyuno_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-headless_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-javafilter_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-emailmerge_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-gnome-integration_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core08_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core04u_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-draw_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core09_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-onlineupdate_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/desktop-integration/
OOG680_m5_native_packed-1_en-US.9221/DEBS/desktop-integration/openoffice.org-debian-menus_2.3-9215_all.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core10_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-kde-integration_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core05_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-base_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-xsltfilter_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core04_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core07_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core06_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-math_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-calc_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-graphicfilter_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-writer_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core01_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core02_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-impress_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-testtool_2.3.0-5_i386.deb
OOG680_m5_native_packed-1_en-US.9221/DEBS/openoffice.org-core03_2.3.0-5_i386.deb

then it said:
~/Desktop$ cd OOG680_m5_native_packed-1_en-US.9221/DEBS/

---

### Post by Maestro23 on 2007-09-23
While you're inside the DEBS directory, run the following:

> sudo dpkg -i *.deb

*You might want to delete the office that came with Ubuntu first though.

---

### Post by slymi2005 on 2007-09-23
Oops I was inputting both lines at one time, i got it running now. thank you so much for your help.

---

### Post by Maestro23 on 2007-09-23
> **slymi2005 said:**
> Oops I was inputting both lines at one time, i got it running now. thank you so much for your help.

No prob man.  Hope everything goes well.:guitar:

---

### Post by nikoPSK on 2007-09-26
Or you could just get the 7.10 alpha. It comes with openoffice 2.2:)

---

### Post by Maestro23 on 2007-09-26
> **nikoPSK said:**
> Or you could just get the 7.10 alpha. It comes with openoffice 2.2:)

I wouldn't recommend 7.10 (in its current stage) to someone new to linux who wants a stable system.:popcorn:

Some problems may arise that a new person would have no clue as to how to fix.

---

### Post by nikoPSK on 2007-09-28
sorry I meant 2.3 and I always spring for beta/ alpha releases... :)

---

### Post by MrDiaz on 2007-10-06
> **forestpixie said:**
> you can never tell - who's to say MrDiaz is male :lol:

haha the **Mr **made that pretty clear I believe

---

### Post by forestpixie on 2007-10-06
aaah - but does it ;)

you'd think so but as I said you can never tell or at least until we get telepathic uplinks through linux we can't :)

if you see this could you mark thread as solved - use the thread tools

---

