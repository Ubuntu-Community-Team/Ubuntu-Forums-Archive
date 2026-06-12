---
title: "Installing Dapper on iMac G3"
date: 2006-11-15
forum: Apple PPC Users
---

### Post by samden on 2006-11-15
I have been attempting to install ubuntu 6.06.1 on a 500mhz iMac G3. I have been following hints and instructions given in previous threads, but have hit a problem I cannot figure out.

I am installing using the alternative install cd (as recommended for this computer by previous posters), and trying to wipe the hard drive and install only ubuntu.

The instalation goes ok until the step "Install the base system". At about 25% of the way through this installation (I am not sure of the exact percentage) I get the message:

[!!] Install the base system.
Base system installation error.
The debootstrap program exited with an error (return value 1)
Check /var/log/syslog or see virtual console 4 for the details.

Please note that I am new to Linux, although familiar with Macintosh computers. I have tried a number of times to do the installation, with various errors, but this is the major persistent error I can't figure out.](*,) 

I have looked at the details in virtual console 4 (pressed ctrl-alt-F4), but the details mean absolutely nothing to me as a Linux novice!

If anyone could tell me what to do now I would be very grateful.

Thankyou.

Please note: This is a duplicate thread to one posted in the "installation and upgrades" section. I realise now this section is more appropriate.

---

### Post by linear on 2006-11-15
1. You could try reburning the CD at a slow speed (4x or less).

2. If you want to try 5.10 (Breezy) instead, the iso may still be available here: [http://releases.ubuntu.cz/5.10/](http://releases.ubuntu.cz/5.10/)

---

### Post by Brian Smith on 2006-11-15
Try the option of "Check CD for defects."
I recently burned a disc that my disc burner app claimed was verified good, but Ubuntu showed as having corrupt files (in the kernel no less) and I had to burn a new disc.  The new disc worked perfectly.

---

### Post by samden on 2006-11-16
An update:

I have now tried installing Ubuntu 6.06.1, Ubuntu 6.10, and Debian on the computer. I have not yet tried Ubuntu 5.10, but it is currently downloading so I will try it tomorrow (thankyou Linear for the link). All the above systems are of course Debian based and very similar, and all have thrown up similar errors. Due to all three throwing up errors I think it is less likely to just be an issue with a faulty cd. I have checked the integrity of the 6.06.1 cd and it says it is fine. I have yet to check the other cds but will do shortly.

Debian throws up almost exactly the same error as Ubuntu 6.06.1. I will write the error messages down here in detail.

1)
Base system installation error.
The debootstrap program exited with an error (return value 1)
Check /var/log/messages or see virtual console 3 for the details
<I then selected "Continue">

2)
Failed to install the base system
The base system installation into /target/ failed.
Check /var/log/messages or see virtual console 3 for the details.
<I then selected "Continue">

3)
Installation step failed
.....
The failing step is: Install the base system
<I then selected "Continue">

This sent me back to the main menu.

Virtual console 3 says:

Setting up libtextwrap1 (0.1-1)

dpkg: dependency problems prevent configuration of console-common:
 console-common depends on console-data; however:
  Package console-data is not configured yet.
dpkg: error processing console-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of base-config:
 base-config depends on console-data (>= 2002.12.04dbs-16); however:
  Package console-data is not configured yet.
dpkg: error processing base-config (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 netkit-inetd
 netbase
 ppp
 pppoe
 pppoeconf
 exim4-base
 telnet
 exim4-daemon-light
 pppconfig
 at
 exim4
 mailx
 console-data
 klogd
 console-common
 base-config
unmount: /target/dev/pts: Invalid argument
unmount: /target/dev/shm: Invalid argument
unmount: /target/proc/bus/usb: Invalid argument


Please remember that this is from the Debian install, NOT ubuntu, but I thought I better write it down while I had it in front of me. As the errors are the same as with ubuntu 6.06.1 the problem is probably the same. If someone can decipher the error messages and tell me what is wrong I would be very grateful!


Ubuntu 6.10 throws up a slightly different error, again during base system installation. These errors are:

1)
Debootstrap warning
Warning: Failure while configuring required packages.
<I then chose "continue">

2)
Debootstrap warning
Warning: Failure while installing base packages. This will be reattempted up to five times.
<I then chose "continue">
<This message repeated a few times, with me hitting continue each time, before it appeared to continue installing>

3)
Debootstrap warning
Warning: Failure while configuring base packages. This will be attempted 5 times.
<I chose continue again, around four times, before it appeared to continue with installation>

4)
Long message, but it basically said: No installable kernel was found.

This could potentially be a cd integrity issue. I will now check that.


If someone could please tell me what is wrong with one of these installations I would be grateful. I am not overly concerned which version of Ubuntu I install, just that I get my computer running on Linux somehow. I would prefer Ubuntu to Debian, but it is a good last resort if I cannot get Ubuntu working.

Thankyou very much for your help.

---

### Post by samden on 2006-11-16
Checking Debian cd integrity:

I type in "check" into the initial screen that comes up when the computer is booted (I assume I am doing this right). The screen then shows:

boot: check
Please wait, loading kernel...
cd:2, check: Unknown or corrupt filesystem

I assume this means the cd is no good, which surprises me as it worked right through to halfway through installation of the base system, then threw up the same error as Dapper.

---

### Post by samden on 2006-11-16
Edgy cd integrity test says that the CD is fine.

Thankyou.

---

### Post by PerryL on 2006-11-17
I like you tried several different distros, including Darwin, and many burns of each and had various problems with every attempt. I finally decided it had something to do with the CD drive in the machine since I have read that Mac CD drives are very picky. This all lead me to try the netboot/network install method. I had to setup a DHCP and TFTP server on my local network (not a problem since I use Linux on all machines). Then I did the netboot from the Mac using Option+Control+o+f to boot from OF...boot:ethn:0,yaboot...and viola the installer loaded over my local network, fired up the installer and after downloading 180MB in 290 files the install completed successfully.

Look up the network install options on here, if you have a fast Internet connection it will work as it downloads and checks each file individually.

**NOTE: Make sure you are using the installer files for the Powerpc**

---

### Post by samden on 2006-11-17
I have now tried installing Ubuntu 5.10, and also Debian from the "business-card" net install cd. Still no luck.

Ubuntu 5.10:
- An error was returned while trying to install the initrd-tools package onto the target system. Check /target/var/log/bootstrap.log for the details.

Debian:
- Base system installation error.
The debootstrap program exited with an error (return value 1).
Check /var/log/messages or see virtual console 3 for the details.

Thanks for the suggestion about net install, but it didn't work for Debian (I could try it for Ubuntu too, I think I will, but expect to see another debootstrap error the same as always).

I think the major error seems to be with this "debootstrap program" whatever it is. I get debootstrap errors (return value 1) with pretty well every version of Ubuntu or Debian I try. What is this debootstrap program? From Googling it I note that lots of people have had problems with it, but cannot find a solution for the iMac G3 through Google.

Can anyone help? I need this computer for work, and a Debian based OS (Debian or Ubuntu) is my best option as far as I can see to easily install Grass GIS, so I don't want to have to give up and move to Mandrake or something like that.

Thankyou.

---

### Post by n_hendrick on 2006-11-17
just a pointer ( I lost about 30 cds ) The iMacs cd drive is a little touchy, every cd I burnt and ran a distro install from gave me an error until I burnt them at half speed (around 6x). so be careful with the distributions. And if all else fails try Slackintosh even better than xubuntu, well, because it comes with fluxbox...a very lightweight window manager, which I prefer to use anyway.

---

### Post by PerryL on 2006-11-18
The bootstrap program is yaboot. To boot the install system you really only need yaboot yaboot.conf (the boot config file) vmlinux (the kernel) initrd.gz (the installer's virtual disk image). yaboot loads the kernel and disk image into memory. yaboot.conf tells yaboot where to get vmlinux and initrd.gz. For a net install you need an initrd.gz that is setup to get the install files from the internet. If you want I can send you the files I used to do an Ubuntu 6.10 install on my B&W powermac.

Make sure you are getting the files from the powerpc branch of the distribution tree. If the bootloader dies immediately with an exit code 1 it usually means you are trying to run an incompatible version...ie an i386 bootloader trying to run on a mac.

---

### Post by samden on 2006-11-18
> **n_hendrick said:**
> just a pointer ( I lost about 30 cds ) The iMacs cd drive is a little touchy, every cd I burnt and ran a distro install from gave me an error until I burnt them at half speed (around 6x). so be careful with the distributions. And if all else fails try Slackintosh even better than xubuntu, well, because it comes with fluxbox...a very lightweight window manager, which I prefer to use anyway.

I just tried burning a 5.10 cd at 8x (the slowest my iBook will allow me to burn at for some reason). It looked good, got just over 70% of the way through the base system installation, before crashing again - "Unable to install ... the initrd-tools package onto the target system". Same error as I have had previously.

I may be forced to give up on Ubuntu and Debian at this rate, but don't want to give up because as a newbie I may find it difficult to install the software I require (Grass GIS, R etc) to other OSs. I am currently burning a Fedora cd to try, but don't want to give up on Ubuntu yet.

---

### Post by linear on 2006-11-18
> **samden said:**
> I just tried burning a 5.10 cd at 8x (the slowest my iBook will allow me to burn at for some reason).

If you want to try an alternate CD-burning program, have a look at [FireStarter FX]("http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter"). I've had better success with it in some cases than with Disk Utility.

---

### Post by samden on 2006-11-20
> **PerryL said:**
> The bootstrap program is yaboot. To boot the install system you really only need yaboot yaboot.conf (the boot config file) vmlinux (the kernel) initrd.gz (the installer's virtual disk image). yaboot loads the kernel and disk image into memory. yaboot.conf tells yaboot where to get vmlinux and initrd.gz. For a net install you need an initrd.gz that is setup to get the install files from the internet. If you want I can send you the files I used to do an Ubuntu 6.10 install on my B&W powermac.

Make sure you are getting the files from the powerpc branch of the distribution tree. If the bootloader dies immediately with an exit code 1 it usually means you are trying to run an incompatible version...ie an i386 bootloader trying to run on a mac.

I have been very careful to only use ppc versions, but thankyou for pointing this out. I would be interested in the files you used to install 6.10, but also need to know how to use them - do I just write them all onto a cd and put it in, will the computer recognise it? Are these files all on the 6.10 cd? I already have downloaded this and could mount the image and copy the files I need.

If you could tell me how to get the files off the cd or where to download them from please do. Otherwise I can PM you my email address so you can send them to me that way if they are not too large. Thankyou for your help.

---

### Post by PerryL on 2006-11-21
The files I have are for booting the mac accross a local network and installing Ubuntu over the Internet. To use the files you need to have a machine on your local network that will act as a DHCP server (to give the mac an IP address) and also act as a TFTP server to send the boot files to the mac. You put the four files onto the TFTP server then when you boot the mac hold down option+alt+o+f to get the built-in mac of boot program. At the OF boot prompt you type boot ethn:0,yaboot ...this tells the mac to boot over its ethernet port. It will grab the yaboot and yaboot.conf files then it will load the kernel then it will get the install program and fire it up. When it installs it will retrieve all of the required files from the Ubuntu ftp servers...one file at a time. It also checks the integrity of each file and if it is messed up it re-downloads it. Pretty much a fool proof if not quick install method.

This was the only way I was able to get a successful install onto my G3...like you I have a large stack of unusable CD's. The files are pretty small so if you want them let me know. You can also download them from Ubuntu in the Netboot area.

---

### Post by Radiolad on 2006-11-21
Hiya, For what it's worth (as I am also a newbie to "Mac/Linux")  I have succesfully loaded Ubuntu 6.06.1 onto my iMac G3 :neutral: 
I decided to order the free Live CDs which only took approx 8 days to be delivered... brilliant.
The GOOD points are
1.The loading of the new OS went without a hitch**.
2. Ubuntu 6.06.1 is like an old friend; very easy to get on with.
*(** excluding my pram battery which was flat.. now replaced)*

The BAD points are
1. Having chosen the 'completely delete OS9.2.2' route, I have LOST the ability to control: Contrast, Brightness and all Picture sizing which was ALL done (as you will know) using on-screen controls.
2. I am ](*,)  banging my head against a brick wall trying to access the web using an ADSL modem (a known working/good Speedtouch 330 *silver*)

With regard to the CD unit in the iMac I had similar difficulties with my X386 PC when rebuilding/installing the software. All manner of ERRORs kept popping up :-k 
The solution in this case turned out to be nothing more than a dusty lens in the unit itself (Yep!! just like a dusty needle on good old fasioned 'gramophone' :-D ) it couldn't read correctly. Fortunately the lens was in the disk TRAY section and was easy to clean when the tray was in the open position.

Maybe some of my experience will help.  When you do get a successful Ubuntu system up and running please _let me know_ how you get on with accessing the ....**WEB **:mad: 

All good wishes for a satisfactory outcome,   Radiolad

---

### Post by stream303 on 2006-11-21
No problem - in the networking forums there are a few Speedtouch tips and hints.  Personally, I'd forget about all the pppoe stuff and just stick your box behind an inexpensive router so that the router and modem can do pppoe in firmware, leaving you with just plain ol' networking.

Send me some questions personally or see my posts in the networking forum - gotta' get that G3 on the air Radiolad!

---

### Post by samden on 2006-11-22
> **PerryL said:**
> The files I have are for booting the mac accross a local network and installing Ubuntu over the Internet. To use the files you need to have a machine on your local network that will act as a DHCP server (to give the mac an IP address) and also act as a TFTP server to send the boot files to the mac. You put the four files onto the TFTP server then when you boot the mac hold down option+alt+o+f to get the built-in mac of boot program. At the OF boot prompt you type boot ethn:0,yaboot ...this tells the mac to boot over its ethernet port. It will grab the yaboot and yaboot.conf files then it will load the kernel then it will get the install program and fire it up. When it installs it will retrieve all of the required files from the Ubuntu ftp servers...one file at a time. It also checks the integrity of each file and if it is messed up it re-downloads it. Pretty much a fool proof if not quick install method.

This was the only way I was able to get a successful install onto my G3...like you I have a large stack of unusable CD's. The files are pretty small so if you want them let me know. You can also download them from Ubuntu in the Netboot area.

Thanks for this. I will hunt the files down in the Netboot area, hopefully I can figure out which ones they are. However (sorry to confuse matters!) I will have to do some juggling to do a network boot. The G3 is hooked to the internet through an ethernet network, but only to the internet. It does not have acces to any networked drives, and I do not have administrator privileges on my large, complicated and very frustrating work network to give it this. I do however have an iBook G4 and a crossover ethernet cable - I could potentially set up a local network to boot from the iBook. But then the ethernet ports on both computers would be in use, and neither would be hooked to the internet. A very confusing situation to me.

Would it be possible for me to hook my Macs together with an ethernet cable and install Ubuntu on the G3 hard drive from the iBook, using the full install cds I have downloaded, thus bypassing any issues with a dodgy cd drive on the iMac? Could I do this from a mounted cd image on the iBook to avoid any issues with burning cds? Could I possibly do a minimal install like this, then disconnect the ethernet cable, hook the G3 to the internet and allow it to continue by downloading the files? :-k 

I wish I had proper access to my work network, it would make this all a lot simpler!

Thankyou for your help. I will start playing with ethernet cables and see what I can come up with. Any further suggestions about what might (and what definately will not) work would be appreciated.

---

### Post by samden on 2006-11-22
> **Radiolad said:**
> Hiya, For what it's worth (as I am also a newbie to "Mac/Linux")  I have succesfully loaded Ubuntu 6.06.1 onto my iMac G3 :neutral: 
I decided to order the free Live CDs which only took approx 8 days to be delivered... brilliant.


This is a very encouraging story. And I am interested that you managed to install on a G3 from the Live CDs - I have not been using them because I read previous posts that said the live CDs wouldn't work on a G3 and the alternative install cds should be used. Maybe I should try the live cds ... although this would involve burning still more cds (current cd count is 14!).

I will keep you posted on what success I have (or do not have)!:mrgreen:

---

### Post by samden on 2006-11-22
I have hooked the iBook to the iMac using ethernet, started up the iBook, started personal file sharing, and copied all the files from the Ubuntu 6.10 alternative install cd (as an experiment - I have not yet downloaded the net boot files) into my shared folder on the iBook. I then booted the iMac holding down ctrl-option-o-f, and typed in boot ethn:0,yaboot at the prompt. I get the reply:

0 > boot ethn:0,yaboot can't OPEN: hd:,\\:tbxi

I am not sure what this means. I think I have probably got to enter the iBook's IP address somewhere on the iMac to get it to recognise it, but don't know how to do this at the Open Firmware boot command line. If someone could give me some more instructions on how I might hook these computers together using ethernet to boot from the iBook please let me know, this is the only way I know of that I can connect the iMac to a network folder.

Thankyou.

---

### Post by samden on 2006-11-22
> **samden said:**
> This is a very encouraging story. And I am interested that you managed to install on a G3 from the Live CDs - I have not been using them because I read previous posts that said the live CDs wouldn't work on a G3 and the alternative install cds should be used. Maybe I should try the live cds ... although this would involve burning still more cds (current cd count is 14!).

I will keep you posted on what success I have (or do not have)!:mrgreen:

I have now burnt a live cd of 6.06.1 and attempted to boot the G3 from it. When I first did it I just got a black screen. When I tried again I typed "live video=ofonly", and this time it tried to boot for a while then gave me the message that it couldn't boot the x-window manager (or something along those lines). I have tried the cd in my iBook and it boots fine, using the standard boot options. The cd appears fine. When I run a check on it with the G3 it says "1 checksum failed" so it can't be perfect, but I am surprised that it won't work at all on the G3 when it works perfectly on the G4.

---

### Post by Radiolad on 2006-11-22
Hi Radiolad here!
Re:blank screen:  Forum member LINEAR (who is a :KS ) sent me this:-

[COLOR="SeaGreen"]The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome[/COLOR]

*NB: Hash is uppercase on pound sign #######  *

I used it with the LiveCD and just chose the ordinary (default) 'boot' option to instigate the running of the CD. It worked perfectly.
Once Ubuntu was 'installed' it booted without the need for the above fix.
  [COLOR="Red"]DONT FORGET YOU WILL LOOSE YOUR SCREEN CONTROLS IF YOU DELETE OS9[/COLOR] :rolleyes:  (just like I have:evil: )

  Regards Radiolad  [SIZE="3"][SIZE="4"][SIZE="3"](still not on the WEB ...Arrgh!!!)[/SIZE][/SIZE][/SIZE]

---

### Post by samden on 2006-11-23
You are a legend, Radiolad! I am having my most promising day with Ubuntu yet. Still not installed, but looking closer.

I have managed to boot a Xubuntu 6.06.1 live cd on the iMac using the above instructions. The OS looks great, and I can't wait to have it actually working on the computer! BUT it would not install, once more I had errors spat at me.

I then tried to boot a Ubuntu 6.06.1 live cd on the iMac. I have had mixed success. The best I have got to in a number of attempts is seeing the bars at the top and bottom of the screen, but with a black desktop. Once I was able to open the desktop through the top menu, open the installer and attempt to install - again errors were spat at me. Most of the time I am not able to even access the menus on the screen.

Xubuntu looks more promising than ubuntu - it boots from the cd faster, and the OS runs perfectly from the cd. The graphics look much better - ubuntu displays in a very grainy fashion. But I cannot get either to install yet.

I suspect that I should be using a different instruction 6 to that in the above post with Xubuntu.
sudo killall -HUP gdm
must refer to Gnome Desktop Manager or something, which is not included in Xubuntu. This command allows the live cd to boot (I don't know why!), but the problems I have in installing could be due to a faulty command here.

On the other hand there may be something to do with the hard drive that will not allow me to install ubuntu on it, or some faulty setting somewhere that will not allow me to install just as I have not been able to install from the alternative install cd.

I am playing around, I have a new motivation now that I have seen the lovely blue Xubuntu screen working on the computer, but still need any suggestions that anyone can come up with. I will tell you as soon as possible if I manage to crack it myself.

Thankyou for all your help, especially :KS RADIOLAD:KS

---

### Post by samden on 2006-11-23
I would like to try the network boot files, but cannot figure out how to do this with the computer hardware I have available (as described previously).

I have ordered pressed cds from shipit, in the hope that they might do the trick. However I really need the computer working long before they will arrive.

If anyone could explain how I could either boot the iMac from the Xubuntu live cd OR through ethernet from my iBook I would be very appreciative. Or if you could explain any other ideas that would be great. I am getting very frustrated with the computer - it has been an almost full time job for the last week and a half and I still have no OS.

Thankyou very much

---

### Post by stream303 on 2006-11-24
Ok, I'm pretty beat and my head is swimming so take this for what it's worth. :)

I wonder if you are just running out of space on the hd?  How are you doing the partitioning?  Are you just trying to use free-space, or blowing away the whole drive?

Makes me wonder if you do in fact have OS9 still on there, but were trying to install to free-space which may not be adequate?

Obviously blowing out the whole disk will really dump your OS9 install.

dunno' :)

---

### Post by samden on 2006-11-24
> **stream303 said:**
> Ok, I'm pretty beat and my head is swimming so take this for what it's worth. :)

I wonder if you are just running out of space on the hd?  How are you doing the partitioning?  Are you just trying to use free-space, or blowing away the whole drive?

Makes me wonder if you do in fact have OS9 still on there, but were trying to install to free-space which may not be adequate?

Obviously blowing out the whole disk will really dump your OS9 install.

dunno' :)
I have been wiping the whole disk (19GB), so should have tonnes of space. I have no OS9 left - wish I did have it left as at the moment the computer is quite unusable!

---

### Post by beanworks on 2006-11-24
I don't know if this will help, but your original post is very similar to errors I was getting when trying to install on my G4 powerbook.

I had YellowDowLinux installed on a partition, and OSX on a partition.  I tried to get rid of the YDL and put Ubuntu in its place. I initially had a lot of trouble trying to reformat the partition, size the partition, etc., and when I finally got it erased and resized properly (I thought), the install problems hit.

yaboot hung around even after erasing the linux partition.  So I finally just reformatted the whole drive, wiping out OSX, and continued with the install.  No more problems.

---

### Post by TheWalt on 2006-11-25
Here is my story.

I have an old iMac G3 333mhz which I upgraded to 384meg ram and put in a 20gig hard drive.  I'm running xubuntu 6.06.1 on it (using it now to type this actually) and am very happy with the performance.  It took me about 3 days to get to this point though for the following reasons.

First, the old tray loader does NOT like all brands of cd's.  Burning speed had no issue with me, but the brand of cd makes all the difference.  I went through 7 cd's of one brand with all kinds of random errors, but when I switched brands all my iso's work now first time every time, even at 52x burn speed.  Ended up using Memorex with a white lable FYI.

Second, and this may be due to the machine being a slot loader, but I had to partition using large volume support for yaboot to work.  That option sets /boot to be within the first 8gig which is a limitation of the older slot loading iMacs.

Third, I only use the alternate install cd's, not the live ones.  The live cd's take too much to run for my little iMac, and you have to do all that monitor fixing (which does work following the above posted instructions) which isn't worth the hassle.

And lastly, Edgy 6.10 ran horrible, worse then OSX 10.3.x did.  I almost gave up, but then had a thought.  6.10 has all the 3d xgl stuff loaded by default in the xserver, even if it is not turned on.  6.06.1 didn't include any of those features out of box, so I tried that and am VERY pleased.  I have just over 200mb ram free upon boot, which is almost 50meg more then on 6.10, and all applications run well.

Keep on trying, everything was detected and setup fine post install.  Xubuntu 6.06.1 brought life back to my old iMac, and I'm sure it can for others too.

---

### Post by stream303 on 2006-11-25
I love reading success stories like this!

Thanks for the detailed info.  Makes me want to rescue one!

---

### Post by samden on 2006-11-30
Still trying, no success yet.

I have tried using a TDK cd rather than the HP ones I was using - no luck, exactly the same errors as before. I'm rather stuck. ](*,)

---

### Post by stream303 on 2006-11-30
Not sure if this is directly applicable, buy have you visited sites like lowendmac:

[http://lowendmac.com/imacs/2001-700.html](http://lowendmac.com/imacs/2001-700.html)

Do you still have your OS/9 disks?  Can you reinstall to the original hd?  Maybe pick up a firewire 400 external hd and install OS/9 on it?  (not familiar with os9 so not sure it's possible.)

I just picked up a 40gb "G-drive" firewire/usb mini external hd at the Apple store so I don't have to dual-boot since my internal hd is dedicated solely to Ubuntu.  Works great - on boot if the firewire drive is powered, OSX.  When off, yaboot picks right up and loads Ubuntu.  (I compiled a custom kernel for firewire support - OR you can reinstall with the Alternate text-based installer which recognizes firewire drives)

Just some thoughts to get *something* up and running. :)

---

### Post by samden on 2006-11-30
> **TheWalt said:**
> Second, and this may be due to the machine being a slot loader, but I had to partition using large volume support for yaboot to work.  That option sets /boot to be within the first 8gig which is a limitation of the older slot loading iMacs.

I would like to try using LVM, but have some errors when I do. I am currently using the Ubuntu 6.06.1 alternative install cd, burnt at 8x onto a TDK CD-R.

LVM computes the following partition table:

IDE1 master (hda) - 20.0 GB 2Head
    #1  32.3 kB                Apple
    #2   1.0 MB B K boot       untitled
    #3 256.0 MB B F ext3       untitled     /boot
    #4  19.7 GB   K lvm        untitled
LVM VG Ubuntu, LV root - 19.2 GB Unknown
    #1  19.2 GB   F ext3       /
LVM BG Ubuntu, LV swap_1 - 583.0 MB Unknown
    #1 583.0 MB   F swap       swap

Then when I choose "Finish partitioning and write changes to disk" I get the message:

[!!] Partition disks
No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system.

What does this mean? What modifications must I make to the above partition table to get this to work?

Thankyou.

---

### Post by samden on 2006-11-30
> **stream303 said:**
> Do you still have your OS/9 disks?  Can you reinstall to the original hd?  Maybe pick up a firewire 400 external hd and install OS/9 on it?  (not familiar with os9 so not sure it's possible.)

No OS9 disks, and I am frustrated by that! I am at the stage where I would like to put OS9 back on it and give up on Linux but have passed the point of no return now... Linux will be better than OS9 though, which is why I abandoned OS9 originally.

---

### Post by TheWalt on 2006-11-30
> **samden said:**
> Still trying, no success yet.

I have tried using a TDK cd rather than the HP ones I was using - no luck, exactly the same errors as before. I'm rather stuck. ](*,)

Few thoughts...

First, definatly xubuntu for the older machine IMHO.

Have you verified via md5 checksum that the ISO your burning is valid?

Did you try the alternate install cd instead (suggested by most people for older G3 iMac)?

Your using default partitioning, whole disk, with LVM?

---

### Post by linear on 2006-11-30
> **samden said:**
> I would like to try using LVM...

<snip>

No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system.

What does this mean? What modifications must I make to the above partition table to get this to work?

I can't see why you would need LVM; if I understand correctly, you don't have an older tray-loader.

How much RAM do you have, by the way? (If low, forget about Ubuntu and stick to Xubuntu.)

The Apple_Bootstrap partition needs to be partition #2 (see [here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch4.en.shtml")). If you erase the entire disk and let the installer figure out the partitioning, it should be created properly (you may need to use the alternate install disk, though).

After install, you may still need to edit xorg.conf and disable dri, as noted previously.

---

### Post by Kalvin on 2006-12-01
> **samden said:**
> Then when I choose "Finish partitioning and write changes to disk" I get the message:

[!!] Partition disks
No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap partition at least 819200 bytes in size, using the HFS Macintosh file system.

What does this mean? What modifications must I make to the above partition table to get this to work?

Thankyou.

You may be better served by setting up the partitions manually.  A NewWorld partition is a special partition you can create with the partitioner that the Alternate Install CD uses. (At least in Edgy...I assume Dapper is the same.)  Create this partition first, then any others you may want.

I only have limited experience with this, but that is how I needed to get edgy to work on my iBook G4.  I received the same error message as you did when letting the partitioner set things up for me.

---

### Post by samden on 2006-12-04
I had a play with the partitioning settings taking note of what everyone has said here. I renamed the #2 partition Apple_Bootstrap and checked all settings with the default partitioning method (not LVM). Then I let it boot again on the offchance that something might work...

After many minor error messages etc, it all installed! :) :biggrin: :)  (Ubuntu 6.06.1 alternative install cd). I happily removed the cd, rebooted the computer, and was very pleased to finally see the Ubuntu login screen. I typed in my username and password and got the last message I wanted to see:

"Incorrect username or password. Letters must be typed in the correct case." #-o 

I cannot believe it is installed but it won't let me access it! I have tried every variation on my username and password I can think of that I might have mistyped it as during the installation process, and am still stuck.

What should I do here? I don't want to have to try reinstalling again - who knows if it will work again. I have no idea why it worked this time and don't know whether it will work again. Can I hack into this and change my username and password?

Thanks heaps for all the help! I am very excited about the computer working better now, but it is maddening that I can't get into it! :)

---

### Post by samden on 2006-12-04
Actually, this is a big change of topic, hacking in without correct username. Will open a seperate thread in this forum on it. Please reply there on this issue, this thread can remain aimed at any further problems I have with the installation itself.

New thread: [http://www.ubuntuforums.org/showthread.php?p=1843734#post1843734](http://www.ubuntuforums.org/showthread.php?p=1843734#post1843734)

---

### Post by shubox357 on 2006-12-07
i did what you did radio ladb but then got a message saying this:

"there was a problem registering the panel with teh bonobo activation server.
The error code is 3.
The panel will now exit."

followed by this: 

"Nautilus can't be used now due to an unexpected error."

i tried it again and the same thing happened when i re inpute the things you did. any ideas?

---

### Post by samden on 2006-12-08
I can't believe I'm actually saying this after 3-4 weeks of trying but

I HAVE A WORKING XUBUNTU 6.06 INSTALL ON MY IMAC!!! :D 

As you can see I'm rather pleased. I gave up on this password thing and reinstalled the system a number of times until it finally relented and worked. Not on the net yet, but I'm sure that will follow soon. 

For some reason I have different errors each time I install. What worked in the end was basically installing from the Xubuntu 6.06 alternative cd over and over again (different errors every single time) until it finally decided to work. The key thing seemed to be repeating each step in the install until it worked - this installation, installing software worked finally on the fourth try (failing at about 95% on all other tries).

Thanks everyone for your help. :mrgreen:

---

### Post by tripuz on 2006-12-25
Hi,
I'm trying to install Xubuntu Dapper Drake on an iMac G3 233: everything goes fine until X starts; at this time, the monitor gets turned off. I tried the methods in the posts above but they didn't work - it looks like the monitor can't turn itselt on, even if I try to get to the command line. 
What should I do? I even tried booting with video=ofonly. How can I get the live CD to boot in text-only mode (no X until I tell him so)?
Thanks

---

### Post by tripuz on 2006-12-25
Ok the alternate CD is working and installing...:)

---

