---
title: "ATI Radeon 9200 driver in feisty Xorg problems"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by w4ett on 2007-05-17
Well it seems that after doing a clean install of feisty, my ati Radeon 9200 card cannot render 3d at all.  GLXGEARS and screensavers lock my system up.  This card performed well in edgy and google earth worked well and I'm not trying to use compiz or Beryl.   I did all the obvious things ( sudo dpkg-reconfigure xserver-xorg ///// sudo gedit /etc/X11/xorg.conf) and I am using the radeon open source driver.   Now after reading more posts on the forums I see that Xorg 7.2 wont work with my card.  Does anyone have an easy how-to to replace xorg 7.2 back to 7.1 as was in edgy or even if this will solve the problem?   Help!

---

### Post by ccesare on 2007-05-17
I have a *Mobility* Radeon 9200 on my laptop, and it runs just fine with feisty. I am also using the radeon driver.

Try the vesa driver out and see if it works for you.

---

### Post by chamberlain2006 on 2007-05-17
I use the 9200SE with 3d and I have NO problems.

---

### Post by w4ett on 2007-05-17
Out of desperation, I have gone back to using the on-board sis641 vid on my ASRock MB, which is not much better but it hasn't crashet yet at least.  I've tried just about everything I can think of....changing radeon drivers to versa and then back to radeon....x says I got direct rendering.  just got me stumped.  I can't run screensavers, google earth or even glxgears.   I even tried a new 9200 card...(I bought two for one).   I guess I'll be buying a new Nvidia card this weekend.

---

### Post by myoungf1 on 2007-05-17
I am curious with all the other users with replies if they can run a game such as Open Arena with the 9200 ATI card under Feisty.  I have a 9250 and had to revert back to edgy to get 3d going now I have no problems as I did with Feisty.

---

### Post by w4ett on 2007-05-17
> **myoungf1 said:**
> I am curious with all the other users with replies if they can run a game such as Open Arena with the 9200 ATI card under Feisty.  I have a 9250 and had to revert back to edgy to get 3d going now I have no problems as I did with Feisty.

Sounds like the same problem I ran into.  When u went back to edgy and 3d went back to normal.??  I want to revert to xorg 7.1 from 7.2 which is included in feisty.

---

### Post by myoungf1 on 2007-05-18
Yes I was finally able to get 3d rendering working with edgy eft since it uses the 7.1 xorg.  Installed Open Arena after switching back to edgy and finally could see what I was doing in Open Arena.

---

### Post by w4ett on 2007-05-18
> **myoungf1 said:**
> Yes I was finally able to get 3d rendering working with edgy eft since it uses the 7.1 xorg.  Installed Open Arena after switching back to edgy and finally could see what I was doing in Open Arena.

Congratulations on the 3D success.   I don't really want to downgrade to edgy though.  Being a relative noob, I guess what I need is a guide to replace xorg in feisty with the older version from edgy, it that is even possible.  Any Xorg Gurus out there up to the challenge? ):P

---

### Post by myoungf1 on 2007-05-20
Sorry for the late reply but unfortunately its not an xorg problem but an ati problem.  Xorg 7.2 is prebuilt into Feisty Fawn as the graphical interface for Feisty.  Simply trying to use an older xorg.conf isn't going to change your problems with the ati drivers as you would have to have xorg 7.1 completly installed.  My question is is that even possible to keep feisty and downgrade your entire xorg from 7.2 to 7.1?  From what I have read its not and if you want 3d rendering with an ati card you are better off going back to edgy eft.

---

### Post by tormod on 2007-05-20
It would be even better if you could file a bug with technical details, and help getting this problem fixed once for all! Look at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/) and see also [https://wiki.ubuntu.com/Bugs/AtiDriver](https://wiki.ubuntu.com/Bugs/AtiDriver)
If you are courageous, look at [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

---

### Post by w4ett on 2007-05-20
> **myoungf1 said:**
> Sorry for the late reply but unfortunately its not an xorg problem but an ati problem.  Xorg 7.2 is prebuilt into Feisty Fawn as the graphical interface for Feisty.  Simply trying to use an older xorg.conf isn't going to change your problems with the ati drivers as you would have to have xorg 7.1 completly installed.  My question is is that even possible to keep feisty and downgrade your entire xorg from 7.2 to 7.1?  From what I have read its not and if you want 3d rendering with an ati card you are better off going back to edgy eft.

Thanks for the reply.  That is the question.....what ARE the procedures to replace Xorg 7.2 with Xorg  7.1?  "sudo apt-get remove xserver-xorg-core" is the method to remove any experimental Xorg files and "sudo apt-get install xserver-xorg-core" is the way to replace it, BUT how do I get the repo listings to accept the Edgy Xorg 7.1 Core to install within Feisty?

---

### Post by w4ett on 2007-05-20
It seems that I have found the method to revert to Xorg 7.1 in Feisty:  [https://answers.launchpad.net/ubuntu/+source/xorg/+question/6106](https://answers.launchpad.net/ubuntu/+source/xorg/+question/6106)

I've been looking for for this for days.

QUOTE:
  Cesare Tirabassi  said on 2007-05-05:


In answer to your question, to downgrade your xorg server to 7.1 you can follow these instructions.
You are likely to break or make your system unstable, if you haven't done it so already; consider yourself warned (so backup your home directory and any important configuration file):

- enable the edgy main repository in your sources.list file
- download and install Xorg 7.1 with the command: sudo apt-get install xorg=1:7.1.1ubuntu6
UNQUOTE.

Will report back on results.

---

### Post by tormod on 2007-05-20
It is very difficult to "downgrade" to Xorg 7.1 in Feisty. There could be a possibility of building an older version of the ati driver and use it with Xorg 7.2 (if the problem is in the ati driver).

Is this a PCI card or an AGP card?

---

### Post by tormod on 2007-05-20
I "forward-ported" the edgy version of the ati driver to feisty, and attached it to this bug:
[https://bugs.launchpad.net/bugs/114520](https://bugs.launchpad.net/bugs/114520)

Would be interesting if you could try it and tell us if there's any difference.

---

### Post by w4ett on 2007-05-21
> **tormod said:**
> It is very difficult to "downgrade" to Xorg 7.1 in Feisty. There could be a possibility of building an older version of the ati driver and use it with Xorg 7.2 (if the problem is in the ati driver).

Is this a PCI card or an AGP card?

Mine is an 8X AGP RV280.   Never could get the ATI Driver to work in Edgy.  Had to use the open source 'Radeon' driver instead, which did give me some 3D capability using mesa, but apparently is incompatible with Xorg 7.2.  When I upgraded to Feisty it all went up the spout.

---

### Post by tormod on 2007-05-21
Sorry if I was not clear enough: When I said "ati driver" I meant the open-source "ati" driver (which includes the "radeon" driver), and not the proprietary "fglrx" driver from ATI Inc.

---

### Post by w4ett on 2007-05-21
> **tormod said:**
> Sorry if I was not clear enough: When I said "ati driver" I meant the open-source "ati" driver (which includes the "radeon" driver), and not the proprietary "fglrx" driver from ATI Inc.

OK....Now all is clear.  I'll try the upgraded driver for Feisty today.   I'm currently using the on-board SIS 661 on my MB (ASRock K7S41GX), but will reinstall the ATI 9200 card and replace the older driver with your new version. 8)

---

### Post by w4ett on 2007-05-21
I used the following procedures to try your "forward-ported" ati driver:

1.  Downloaded the driver .Deb package installer from Lauchpad
2.  In terminal removed the xserver-xorg-video-ati driver
3.  Installed the changed driver, ignoring the Newer Version Available  and Software Update     available warnings.
4.  Shutdown and re-install ATI Radeon 9200 SE card.
5.  Boot into recovery mode
6.  sudo dpkg reconfigure Xserver-xorg
7.  Sudo nano /etc/X11/xorg.conf checking applicable device entries
8.  Attempted boot into gnome
9.  Got the dreaded Xfailure Screen.
10.Triple checked entries and re-attempted to start x several times

I received the following errors:  
[B][I][U]Module ABI minor Version (2) is newer than server version (1)

Failed to load module "ati" (Module Requirement Mismatch 0)
[/U][/I][/B]

I sifted thru xorg.conf with a fine tooth comb and all the setting are correct.  I'm assuming these error messages are due to the differences between Xorg 7.2 and 7.1 and this driver needs a tweak?

---

### Post by tormod on 2007-05-21
My fault, I forgot I had upgraded to a newer xorg-server 1.3 on the build machine, so it was built against the 1.3 headers. I have now posted a new package to the same bug report. This one I have verified to load fine on a normal Feisty machine, but since I don't have an ATI card on it, I don't know how well it runs.

---

### Post by w4ett on 2007-05-21
Thanks...will give it another go......BTW..before I do, do you see any problem with my procedure for installing the new driver?  i THINK I got it correct, but please correct me if I'm wrong.

---

### Post by tormod on 2007-05-21
[QUOTE=w4ett]Thanks...will give it another go......BTW..before I do, do you see any problem with my procedure for installing the new driver? i THINK I got it correct, but please correct me if I'm wrong.[/QUOTE]
It's very good. You don't have to deinstall the previous driver, just ignore the downgrade warning.

---

### Post by w4ett on 2007-05-21
Ok...managed to get X back up with the ported driver.  3D still not working,,,glx gears locking up system again, but 2D performance is OK.

glxinfo:

don@don-desktop:~$ glxinfo 
name of display: :0.0 
display: :0  screen: 0 
direct rendering: Yes 
server glx vendor string: SGI 
server glx version string: 1.2 
server glx extensions: 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group 
client glx vendor string: SGI 
client glx version string: 1.4

---

### Post by tormod on 2007-05-22
Ok, so it's most likely not the driver then, but something else. It could be the kernel. Could you try to install the Edgy kernel, it should work fairly well, just enable the edgy-updates repository and _do not upgrade_, just "sudo apt-get install linux-image-2.6.17-11-generic" and then change repository again. You will of course keep the Feisty kernel, you can choose between them in the grub menu.

Since this is in the "Absolute Beginner Talk" I have to add this disclaimer otherwise some well-meaning, over-protecting people will complain: **Do not mix packages and repositories from different distributions!** Stay away from the command line :)

Ok, this said, w4ett, you seem to be competent and there is nothing to be afraid of. It's easier than downgrading Xorg...

Did you try without the VideoRAM (should be kilobytes: 65536) and FBDev (default is off) options? Is this a tablet PC? BTW, please attach xorg.conf and Xorg.0.log as plain text files (you might as well use the bug tracker for this).

Tormod

---

### Post by tormod on 2007-05-22
Now that I see you have 64MB of RAM and AGP (you should have said this in the first place...), there are some known bugs:

Can you set AGP aperture size in BIOS? What's the current value? Try 64MB.

Can you try Option "BusType" "PCI" ?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=392915](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=392915)
[https://bugs.freedesktop.org/show_bug.cgi?id=6111](https://bugs.freedesktop.org/show_bug.cgi?id=6111)

---

### Post by w4ett on 2007-05-22
Success...at last 3d is operational.  This is using the forward ported driver in Feisty Xorg7.2. Device info as follows:

Section "Device"
	Identifier	"ATI Radeon 9200SE"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	65536
	Option		"UseFBDev"		"true"
        Option          "BusType" "PCI"
EndSection

Section "Monitor"
	Identifier	"Dell E773c"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60

don@don-desktop:~$ glxgears
3075 frames in 5.0 seconds = 614.817 FPS
3070 frames in 5.0 seconds = 613.835 FPS
3069 frames in 5.0 seconds = 613.695 FPS
3069 frames in 5.0 seconds = 613.772 FPS
3070 frames in 5.0 seconds = 613.808 FPS
3070 frames in 5.0 seconds = 613.807 FPS
3069 frames in 5.0 seconds = 613.745 FPS
3069 frames in 5.0 seconds = 613.778 FPS
3070 frames in 5.0 seconds = 613.841 FPS
3068 frames in 5.0 seconds = 613.593 FPS
3069 frames in 5.0 seconds = 613.767 FPS
3070 frames in 5.0 seconds = 613.832 FPS
3067 frames in 5.0 seconds = 613.218 FPS

---

### Post by w4ett on 2007-05-22
It seems that 3D funtionality is good.  I installed Google Earth at it works well with all functions operational.  This card will never be a gamer but I'm happy at this point.  So, bottom line is the Forward-Ported ATI Driver works with Feisty.  Now I suppose the newer driver in the repos needs to be blacklisted so it will not appear in the System Update??? to get rid of the Nag factor at startup, and so I don't accidentally reinstall it during the next system update.

Question now is: How do I blacklist this update?

Other than that....I would say this problem is resolved for the card 3D rendering by use of the ported driver in Xorg 7.2.  Tormod...This is GOLDEN,,,,and needs to be added to a how to Wiki!

---

### Post by tormod on 2007-05-22
Please try **only** the BusType PCI option and with the original Feisty "ati" driver.

---

### Post by tormod on 2007-05-22
I am happy that you got your card working, but we shouldn't stop there. Please also answer my question: "w4ett, was the 2D performance worse with the original feisty ati driver?"

And did you try without PCI and without "UseFBDev" ?

If we don't do this systematically, (and you don't answer all questions) we'll get no bug fixed, only you will get your card sub-optimally working without AGP, and the drivers will not be fixed for everybody in the next release...

---

### Post by w4ett on 2007-05-22
without the option UseFBDev :

don@don-desktop:~$ glxgears
3165 frames in 5.0 seconds = 632.956 FPS
4245 frames in 5.0 seconds = 848.972 FPS
5005 frames in 5.0 seconds = 1000.836 FPS
5006 frames in 5.0 seconds = 1001.192 FPS
5006 frames in 5.0 seconds = 1001.174 FPS
4952 frames in 5.0 seconds = 990.300 FPS
4916 frames in 5.0 seconds = 983.083 FPS
4916 frames in 5.0 seconds = 983.119 FPS
4917 frames in 5.0 seconds = 983.366 FPS
4889 frames in 5.0 seconds = 977.608 FPS
3692 frames in 5.0 seconds = 738.245 FPS

Obviously better 3D response.....will next remove option pci

---

### Post by w4ett on 2007-05-22
Ok....bottom line here.....UseFBDev not required. with Bus Type PCI...FPS rate better.  Without the Bus Type PCI there is NO 3D acceleration.  glxgears locks system requiring Hard Boot....all this is with the ported driver.

I placed Bus Type PCI back in xorg.conf and left UseFBDev out at present.

---

### Post by tormod on 2007-05-22
OK, so you get the same results with the original as with the ported driver? AGP breaks with both drivers? Then you can reinstall the original and forget about my "forward-ported" one.

Did you check the BIOS? Did you try the Edgy kernel? AGP uses some kernel modules.

It would be good to find out exactly what broke from Edgy to Feisty...

---

### Post by w4ett on 2007-05-22
> **tormod said:**
> OK, so you get the same results with the original as with the ported driver? AGP breaks with both drivers? Then you can reinstall the original and forget about my "forward-ported" one.

Did you check the BIOS? Did you try the Edgy kernel? AGP uses some kernel modules.

It would be good to find out exactly what broke from Edgy to Feisty...

No..I only get 3d with your ported driver.....Driver in Feisty has NO 3d...even from the Live CD.   Bios AGP App  has been tried in both 64MB and Automatic modes......Did not try the Edgy Kernel YET....but currently, with the Feisty Kernel these settings seem to work.  If I remember correctly, PCI  had to be enabled in Edgy for 3D to work as well.

---

### Post by myoungf1 on 2007-05-22
I have a pci ATI card in Edgy and I don't remember having to activate, for lack of a better word, pci to get it work.  Only problem I had was tweaking xorg.conf to get 3d working after fglrx drivers were installed from the ATI website.

---

### Post by w4ett on 2007-05-22
> **myoungf1 said:**
> I have a pci ATI card in Edgy and I don't remember having to activate, for lack of a better word, pci to get it work.  Only problem I had was tweaking xorg.conf to get 3d working after fglrx drivers were installed from the ATI website.

Is your card a 9250???...if so visit [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520)

---

### Post by AzraelUK on 2007-05-22
I've filed a bug report, you can see it [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/116268").

---

### Post by tormod on 2007-05-22
> Is your card a 9250???...if so visit [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/114520](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/114520)
That bug is for PCI cards! Don't mess it up with AGP bugs...

Azrael, please open a new bug for the "ati" driver. Bugs in the "fglrx" driver are something completely different, and there's nothing we can do about bugs in such proprietary drivers.

---

### Post by myoungf1 on 2007-05-22
> **w4ett said:**
> Is your card a 9250???...if so visit [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520)

Sorry should have been more clear and looked under the hood before I said anything.  I do have an ATI Radeon 9250 AGP card and got it working with Edgy Eft for 2d and 3d rendering with the ATI drivers from their site.  

Also tormond I agree that their is nothing to be done by Ubuntu on proprietary drivers like the ATI ones, but since they have supposedly went open source is their any current progress on getting them to work in feisty?

---

### Post by tormod on 2007-05-22
> **myoungf1 said:**
> Also tormond I agree that their is nothing to be done by Ubuntu on proprietary drivers like the ATI ones, but since they have supposedly went open source is their any current progress on getting them to work in feisty?

AMD/ATI has not gone open source! The open-source "ati" drivers are developed by the free-software community. AMD/ATI Inc has dropped support for these old cards in their proprietary "fglrx" driver.

---

### Post by myoungf1 on 2007-05-22
Ahh, that makes sense.  I did a quick lookup and ATI is only saying, via marketing, they are committed to improving their linux support.  Sounds like thats just words blowing in the wind.

---

### Post by tormod on 2007-05-22
> **w4ett said:**
> No..I only get 3d with your ported driver.....Driver in Feisty has NO 3d...even from the Live CD.   Bios AGP App  has been tried in both 64MB and Automatic modes......Did not try the Edgy Kernel YET....but currently, with the Feisty Kernel these settings seem to work.  If I remember correctly, PCI  had to be enabled in Edgy for 3D to work as well.

You did try the Feisty driver with the PCI option? The Live CD will of course crash since it will use AGP  by default on an AGP card. The PCI option turns off AGP and uses PCI instead.

Please verify this summary:

Without DRI
- every version works
With DRI
- Edgy: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver and Edgy kernel: AGP broken, only PCI works
- Feisty: AGP broken, PCI broken

Now for looking forward, would you dare have a look at [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge) ? If we can establish this bug in a recent development version, it's a good chance the Xorg developers at freedesktop.org might help us.

---

### Post by w4ett on 2007-05-22
> **tormod said:**
> You did try the Feisty driver with the PCI option? The Live CD will of course crash since it will use AGP  by default on an AGP card. The PCI option turns off AGP and uses PCI instead.

Please verify this summary:

Without DRI
- every version works
With DRI
- Edgy: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver and Edgy kernel: AGP broken, only PCI works
- Feisty: AGP broken, PCI broken

Now for looking forward, would you dare have a look at [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge) ? If we can establish this bug in a recent development version, it's a good chance the Xorg developers at freedesktop.org might help us.

Since our last permutation of settings, and after further testing:

Without DRI
- every version works
With DRI
- Edgy: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver: AGP broken, only PCI works
- Feisty with forward-ported Edgy driver and Edgy kernel: AGP broken, only PCI works

reloaded feisty xorg7.2 ati driver: - Feisty: AGP broken, PCI 3d 50% FPS Rate of ported driver with option  bus type "pci"   Normal AGP Mode ustable and no 3D

---

### Post by tormod on 2007-05-22
Did you record FPS for all four cases?

So basically there's no difference between Edgy and Feisty, only that the 6.6.2 driver is twice as fast (glxgears-wise) as 6.6.3 ?

---

### Post by w4ett on 2007-05-22
> **tormod said:**
> Did you record FPS for all four cases?

So basically there's no difference between Edgy and Feisty, only that the 6.6.2 driver is twice as fast (glxgears-wise) as 6.6.3 ?


exactly>

glxgears Feisty Xorg7.2 forward ported driver...... (NO) UseFBDev: PCI option

don@don-desktop:~$ glxgears
4004 frames in 5.0 seconds = 800.792 FPS
6138 frames in 5.0 seconds = 1227.453 FPS
6193 frames in 5.0 seconds = 1238.462 FPS
6198 frames in 5.0 seconds = 1239.550 FPS
6104 frames in 5.0 seconds = 1220.777 FPS
6113 frames in 5.0 seconds = 1222.544 FPS
6196 frames in 5.0 seconds = 1239.053 FPS
6087 frames in 5.0 seconds = 1217.398 FPS
6116 frames in 5.0 seconds = 1223.132 FPS


glxgears Feisty Xorg 7.2 forward ported driver........ (Yes)UseFBDev PCI Option

don@don-desktop:~$ glxgears
3075 frames in 5.0 seconds = 614.817 FPS
3070 frames in 5.0 seconds = 613.835 FPS
3069 frames in 5.0 seconds = 613.695 FPS
3069 frames in 5.0 seconds = 613.772 FPS
3070 frames in 5.0 seconds = 613.808 FPS
3070 frames in 5.0 seconds = 613.807 FPS
3069 frames in 5.0 seconds = 613.745 FPS
3069 frames in 5.0 seconds = 613.778 FPS
3070 frames in 5.0 seconds = 613.841 FPS
3068 frames in 5.0 seconds = 613.593 FPS
3069 frames in 5.0 seconds = 613.767 FPS
3070 frames in 5.0 seconds = 613.832 FPS
3067 frames in 5.0 seconds = 613.218 FPS


In all respects, AGP DOES NOT WORK

These are the two I recorded....I can reload the other options and re-post

---

### Post by w4ett on 2007-05-22
I opened an IRC Channel:  	 irc://freenode/ubuntu-radeon9200

---

### Post by w4ett on 2007-05-23
Feisty Xorg7.2 Feisty ATI Driver, Option UseFBDev ="false" Option PCI

don@don-desktop:~$ glxgears
718 frames in 5.4 seconds = 131.747 FPS
678 frames in 5.5 seconds = 124.066 FPS
904 frames in 5.2 seconds = 173.659 FPS
1695 frames in 5.1 seconds = 334.623 FPS
1695 frames in 5.1 seconds = 331.607 FPS
1695 frames in 5.2 seconds = 325.193 FPS
1808 frames in 5.3 seconds = 339.754 FPS
1695 frames in 5.1 seconds = 335.206 FPS
1695 frames in 5.1 seconds = 332.270 FPS
1695 frames in 5.0 seconds = 338.469 FPS

Once again No AGP

---

### Post by tormod on 2007-05-23
You should file a bug on this performance regression, independent of the AGP issue.

---

### Post by w4ett on 2007-05-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/116471](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/116471) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **tormod said:**
> You should file a bug on this performance regression, independent of the AGP issue.

Bug Reported:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/116471](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/116471)

---

### Post by tormod on 2007-05-30
w4ett, can you please file a bug on the issue that you have to disable AGP (use PCI instead) to not have it crash?

myoungf1, it never got clear for me how your situation was: did DRI work fine in Edgy with the "ati" driver (I am not so interested in the "fglrx" driver), but crashed in Feisty? Using AGP or PCI? Maybe you should also file a bug.

Remember that the busy developers almost never look in the forums, it's to noisy and messy here :) Only good bug reports with clear and detailed information help.

---

### Post by w4ett on 2007-05-30
> **tormod said:**
> w4ett, can you please file a bug on the issue that you have to disable AGP (use PCI instead) to not have it crash?

Can do Tormod.  Will post a bug report on the AGP VS PCI crash issue.

---

### Post by w4ett on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/117875](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/117875) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug report filed.

---

