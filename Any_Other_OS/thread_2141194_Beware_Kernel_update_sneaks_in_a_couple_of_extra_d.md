---
title: "Beware: Kernel update sneaks in a couple of extra desktop environments"
date: 2013-05-01
forum: Any Other OS
---

### Post by Rebelli0us on 2013-05-01
I updated my Mint MATE 13 to [kernel 3.9]("http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html"), and upon reboot a crippled OS without taskbar greets me. I now have in addition to MATE:

Gnome Classic
Gnome Classic - no effects
Ubuntu 
Ubuntu-2d
Several hideous Themes

Now all users other than myself login to blank desktop. Root also gets a blank desktop. I only updated the kernel, why did I get a couple of Mickey Mouse GUIs thrown-in?

---

### Post by buzzingrobot on 2013-05-02
How did you do the update? From what source? What specific commands? What repos were enabled?

---

### Post by tgalati4 on 2013-05-02
More importantly, why did you do the update?  You had a working system.  What was in kernel 3.9 that you absolutely had to have?  Mint 14 Mate has version:

tgalati4@Mint14-Extensa ~ $ uname -a
Linux Mint14-Extensa 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

So you have jumped from 3.2 to 3.9 bypassing several intermediate yet major versions.  I would expect breakage.  The extra desktops are just a bonus.  Linux Mint Mate 15 would pull a newer kernel and then strip out the extra desktops.  The extra desktops may or may not be the cause of your issue.

---

### Post by lykwydchykyn on 2013-05-02
There is no way a kernel update would cause you to have more desktop environments.

---

### Post by buzzingrobot on 2013-05-02
> **lykwydchykyn said:**
> There is no way a kernel update would cause you to have more desktop environments.

Hence the request for the repos, etc. Every time a new kernel hits, five minutes later a batch of Ubuntu sites publish cookie-cutter articles exclaiming "How To Install Kernel 3.X in Ubuntu and Mint!".  It's just boilerplate text of a few apt-get lines, with no explanation of why you might upgrade, or might not.  There's usually something silly like "Dozens of exciting new features!" tossed out without elaboration. These sites and these articles do users a disservice. If your kernel is working, you have no compelling reason to upgrade.

---

### Post by tgalati4 on 2013-05-02
I need to get out more often.

---

### Post by lykwydchykyn on 2013-05-03
Looks like this particular tutorial has you downloading a script from someone's dropbox folder and running it blindly.  Lovely.

---

### Post by monkeybrain2012 on 2013-05-03
?? strange that you get more DE and themes with a kernel update. Now can you boot into the previous one? Also check in synaptic to see what has been installed and when (check history) It is possible that you installed those other things as dependencies for something else without remembering it.

P.S. I just installed 3.9 from the same site to check. Works great so far (I have multiple test partitions which I use for such purposes. :))

---

### Post by buzzingrobot on 2013-05-03
> **lykwydchykyn said:**
> Looks like this particular tutorial has you downloading a script from someone's dropbox folder and running it blindly.  Lovely.


I looked at the script. It pulls down the headers and the kernel image from the kernel PPA, deposits them in a temporary directory, does "dpkg -i *.deb", and exits. Hard to see how you end up with a batch of new DE's and themes after that, unless that dpkg command was run in a directory with other deb's..

---

### Post by CharlesA on 2013-05-03
> **lykwydchykyn said:**
> Looks like this particular tutorial has you downloading a script from someone's dropbox folder and running it blindly.  Lovely.

Yikes!

I looked at the script and it doesn't seem to do anything bad, but that sure isn't something I would do.

The code from the script is below, and that link to that dropbox user seems to occur a lot on the upubuntu site.

```
#!/bin/sh

echo "$(tput setaf 3)--- Kernel 3.9 will be installed in an `uname -i` system---$(tput sgr0)"

echo ""

sleep 2

read -p "Press Enter to continue, or abort by pressing CTRL+C" nothing

echo ""
echo ""

#i386 links

link1="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-headers-3.9.0-030900_3.9.0-030900.201304291257_all.deb"

link2="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-headers-3.9.0-030900-generic_3.9.0-030900.201304291257_i386.deb"

link3="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-image-3.9.0-030900-generic_3.9.0-030900.201304291257_i386.deb"

#amd64 links

url1="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-headers-3.9.0-030900-generic_3.9.0-030900.201304291257_amd64.deb"

url2="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-image-3.9.0-030900-generic_3.9.0-030900.201304291257_amd64.deb"

#System architecture

arch=`uname -m`
if  [ $arch = i686 ] || [ $arch = i386 ]; then

mkdir -p $HOME/kernel-i386 

cd $HOME/kernel-i386

wget -c $link1
wget -c $link2
wget -c $link3

sudo dpkg -i *.deb  

sudo rm -rf $HOME/kernel-i386

elif [ $arch = "x86_64" ]; then

mkdir -p $HOME/kernel-amd64

cd $HOME/kernel-amd64

wget -c $link1
wget -c $url1
wget -c $url2

sudo dpkg -i *.deb  

sudo rm -rf $HOME/kernel-amd64

     else
        echo "Unsupported Architecture"
fi
```

With that being said, is it even a good idea to use a raring kernel on a Mint system?

---

### Post by matt_symes on 2013-05-03
Hi

That script is not responsible for your new desktops unless the folders were already created and populated with debs - unlikely.

As CharlesA pointed out, it's not malicious, rather it's uneconomically written, but you should always think twice about installing anything that is not from the main repositories.

If in doubt, post it here beforehand.

Kind regards

---

### Post by lykwydchykyn on 2013-05-03
> **CharlesA said:**
> Yikes!

I looked at the script and it doesn't seem to do anything bad, but that sure isn't something I would do.

Sets a bad precedent, IMHO.  Hello, social engineering...
> 
With that being said, is it even a good idea to use a raring kernel on a Mint system?

Really shouldn't do much damage, unless maybe the OP is running LMDE.  Even then, a kernel is mostly device drivers; it doesn't really impact the high-level functiong of the system as much as people think, at least in my experience.  I've used backported kernels, custom kernels, 3rd-party kernels, etc.  It's usually not a problem unless you forget to enable some filesystem support or some piece of hardware, or if you manually installed a proprietary video driver, etc.

It's not going to put new files in /usr/share/xsessions, that's for sure.

---

### Post by CharlesA on 2013-05-03
> **lykwydchykyn said:**
> Sets a bad precedent, IMHO.  Hello, social engineering...

Agreed. Kinda like those gnome-look trojans that happened a while back.


> Really shouldn't do much damage, unless maybe the OP is running LMDE.  Even then, a kernel is mostly device drivers; it doesn't really impact the high-level functiong of the system as much as people think, at least in my experience.  I've used backported kernels, custom kernels, 3rd-party kernels, etc.  It's usually not a problem unless you forget to enable some filesystem support or some piece of hardware, or if you manually installed a proprietary video driver, etc.

It's not going to put new files in /usr/share/xsessions, that's for sure.

Thanks. I know Mint is a Ubuntu directive, but I didn't know the details.

---

### Post by snowpine on 2013-05-03
Switch to Ubuntu, It's Better! ;)

---

### Post by Atitudes on 2013-05-03
Hi there!
One very noobish question, I am using ubuntu 12.04LTS with kernel 3.2.0. 

As it was said:
> **buzzingrobot said:**
> If your kernel is working, you have no compelling reason to  upgrade.

Can anybody enlighten me about the need to update or not the kernel? I was actually searching about desktop computer overheating problems' and came across some kernel answers, some suspicious, other actually made a lot of sense (perhaps not directly related to my issue) and made me curious. 

If someone could have the kindness to guide me through my quest I would be gladly thankful!!

---

### Post by CharlesA on 2013-05-03
Personal preference. I am still on the 3.2 kernel and having no issues with it.

---

### Post by Atitudes on 2013-05-03
> **CharlesA said:**
> Personal preference. I am still on the 3.2 kernel and having no issues with it.

Thanks and +1!
I had so much trouble to make music editing programs working that I really do not want to mess with it :P (still fighting with QJackCtl and Guitarix lol, impossible to have them working together grrr, 
but I do manage QJackCtl with other softwares tho :confused:)

Until I have enough time and storage space to backup everything, I wont mess either with my Ubuntu version nor Kernel one as *almost* everything is working perfectly!!
PS - I hate to get back on W7 @work :p

---

### Post by buzzingrobot on 2013-05-04
> **Atitudes said:**
> Hi there!

Can anybody enlighten me about the need to update or not the kernel? 


If you have a specific problem that you know an updated kernel addresses and corrects, then it could be worth thinking about updating. 

I seldom update kernels.  If I'm going to see problems with a default kernel, it is probably going to happen very soon after the initial install, or, perhaps, if I add hardware. Other than that, if everything is working fine, I don't see a need to do an upgrade. I wouldn't upgrade just on the vague notion that I might see something better.

There's potentially some advantage from sticking with a release's default kernel because distributions can't guarantee what will happen when their updates are applied to a system modified by the user. E.g., if an update is released that relies on the presence of the default kernel, then someone who has a different kernel needs to be aware of that.

Also, I believe (but it's worth verifying) that the kernels released into Ubuntu's kernel PPA are built to the standard configuration, not to the configuration used to build the release kernels.  In theory, at least, that might make a difference.

---

### Post by matt_symes on 2013-05-04
Hi

> Also, I believe (but it's worth verifying) that the kernels released  into Ubuntu's kernel PPA are built to the standard configuration, not to  the configuration used to build the release kernels.  In theory, at  least, that might make a difference.

The mainline kernels in the Ubuntu kernel PPA are built using Ubuntu's standard configuration but they are not patched using the sauce patches.

Therefore they are vanilla kernels with Ubuntu's kernel configuration.

Kind regards

---

### Post by lykwydchykyn on 2013-05-04
I try an upgraded kernel whenever I have hardware problems; it's worth a try to see if they are improved.  Like I said earlier, the kernel is mostly hardware drivers, and better hardware support is the primary reason to use one kernel version over another.

I would point out too, there's really no harm in installing kernels; if it fails, you just reboot and choose your old kernel in GRUB (then promptly uninstall the bad kernel!).  You can install all the kernels your hard drive can hold in a single install, and just switch between them at boot.

---

### Post by Rebelli0us on 2013-05-05
Thank you, and sorry for the delayed response.

The reason for the kernel update is Mint 13/Ubuntu Precise doesn&#8217;t support Intel z77 platform (crashes).

I updated to kernel 3.5.1 which seems to fully support z77, no crashes. 

However mobo has Intel Centrino Advanced-N 6235 (rev 24), I get slow reconnect and occasional non-connect on resume. Also there is still no way to read fan speeds and the usual assortment of data from Sensors Applet on z77 mobos. So I tried Kernel 3.9

Update: The kernel update clearly trashed the OS, so I did [the uninstall command from the above link]("http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html"). Result: On reboot, grub had **NO Linux OS listed in the boot menu**! This was a disaster &#8211; even worse than &#8220;grub rescue&#8221;.

The website looks official, I&#8217;ve found countless references to it by &#8220;experts&#8221; for kernel updates etc., kernel 3.5.1 worked just fine, so why not kernel 3.9.  Are you guys suggesting that the script is malicious or amateurish?  If so, how does one update? Mint 13/Ubuntu Precise 12.04 is Long Term Support but may never get an official kernel update.

---

### Post by Rebelli0us on 2013-05-05
... BTW, my Mint 13 was default vanilla install. After [the kernel 3.9 update]("http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html"), MDM login (and mdmsetup) listed extra GUIs that were not there before:

Gnome Classic
Gnome Classic - no effects
Ubuntu
Ubuntu-2d
Extra ugly Themes that didn’t even work

How did these sneak in?

---

### Post by SuperFreak on 2013-05-05
I have a  Asrock Z77 Extreme 4-M  Motherboard and my kernel is 3.5 on Ubuntu 12.04.2. I have had no serious issues with that kernel or earlier kernels going back to 3.2.

---

### Post by Rebelli0us on 2013-05-05
Regrading Intel Centrino Advanced-N 6235 (rev 24), here's fragment from syslog. It connects eventually, but very slow. Normally on resume wireless is already connected by the time you see the desktop. Any ideas?

 > NetworkManager[1090]: <warn> (10) failed to find interface name for index
 NetworkManager[1090]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
 NetworkManager[1090]: **<error> [1367768761.189651] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object**
 NetworkManager[1090]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
 dbus[1035]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
 NetworkManager[1090]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/ieee80211/phy0/rfkill22 disappeared
 dbus[1035]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

---

### Post by matt_symes on 2013-05-05
Hi

> **Rebelli0us said:**
> Thank you, and sorry for the delayed response.

The reason for the kernel update is Mint 13/Ubuntu Precise doesn&#8217;t support Intel z77 platform (crashes).

I updated to kernel 3.5.1 which seems to fully support z77, no crashes.

However mobo has Intel Centrino Advanced-N 6235 (rev 24), I get slow reconnect and occasional non-connect on resume. Also there is still no way to read fan speeds and the usual assortment of data from Sensors Applet on z77 mobos. So I tried Kernel 3.9

I have no experience of that motherboard so i can't really add much to that without research.

I would say that did you read the release notes for the kernels to see what had been added or did you just install it and hope for the best ?

> 
Update: The kernel update clearly trashed the OS, so I did [the uninstall command from the above link]("http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html"). Result: On reboot, grub had **NO Linux OS listed in the boot menu**! This was a disaster &#8211; even worse than &#8220;grub rescue&#8221;.

How many kernels did you have installed ? You can boot into a liveDC/USB, and update-grub or install another kernel if that is your problem.

You may have to chroot though.

> 
The website looks official, I&#8217;ve found countless references to it by &#8220;experts&#8221; for kernel updates etc., kernel 3.5.1 worked just fine, so why not kernel 3.9.  Are you guys suggesting that the script is malicious or amateurish?  If so, how does one update? Mint 13/Ubuntu Precise 12.04 is Long Term Support but may never get an official kernel update.

Nobody is suggesting the script is malicious. It does what it says on the tin.

The only comment i would make about the script is that it could have been writtten in half the number of lines - hence uneconomical.

Installing scripts from the Internet is always a gamble. The script could be out of date, it could be malicious and unless you can read the script to see what it does, you are taking a gamble.

The sites does look pretty trustworthy however, as CharlesA stated, it's not something i would do without looking through the script first.

There is no way that script would install extra desktops or, as stated by someone else, add entires in /usr/share/xsessions/. It downloads the kernels from the kernel PPA and installs them for you.

Are you totally sure you did not do this somehow ?

Have you checked the dpkg logs ? 
Have you checked the timstamps in the entries in xsessions ? 
What kind of diagnosis have you done so far ?

Kind regards

---

### Post by CharlesA on 2013-05-05
> **matt_symes said:**
> 
Nobody is suggesting the script is malicious. It does what it says on the tin.

The only comment i would make about the script is that it could have been writtten in half the number of lines - hence uneconomical.

Installing scripts from the Internet is always a gamble. The script could be out of date, it could be malicious and unless you can read the script to see what it does, you are taking a gamble.

The sites does look pretty trustworthy however, as CharlesA stated, it's not something i would do without looking through the script first.

Yeah, it just seems like an inefficient way to install new kernels, though. The only way I've found to install the 3.9 kernel is to either use that script or do it manually. I assume that is because they aren't in the main repos yet?

---

### Post by matt_symes on 2013-05-05
Hi CharlesA

> **CharlesA said:**
> Yeah, it just seems like an inefficient way to install new kernels, though. The only way I've found to install the 3.9 kernel is to either use that script or do it manually. 

Yep. I install them manually.

> I assume that is because they aren't in the main repos yet?

Ther're in saucy's repos only i think.

Kind regards

---

### Post by Rebelli0us on 2013-05-05
> **matt_symes said:**
> Hi



I have no experience of that motherboard so i can't really add much to that without research.

I would say that did you read the release notes for the kernels to see what had been added or did you just install it and hope for the best ?



How many kernels did you have installed ? You can boot into a liveDC/USB, and update-grub or install another kernel if that is your problem.

You may have to chroot though.



Nobody is suggesting the script is malicious. It does what it says on the tin.

The only comment i would make about the script is that it could have been writtten in half the number of lines - hence uneconomical.

Installing scripts from the Internet is always a gamble. The script could be out of date, it could be malicious and unless you can read the script to see what it does, you are taking a gamble.

The sites does look pretty trustworthy however, as CharlesA stated, it's not something i would do without looking through the script first.

There is no way that script would install extra desktops or, as stated by someone else, add entires in /usr/share/xsessions/. It downloads the kernels from the kernel PPA and installs them for you.

Are you totally sure you did not do this somehow ?

Have you checked the dpkg logs ? 
Have you checked the timstamps in the entries in xsessions ? 
What kind of diagnosis have you done so far ?

Kind regards


Thank you. Yes I read the release notes for the kernels, Centrino Advanced-N 6235 was supposedly supported form 3.2 forward but it still isn’t working on this mobo. As for the z77 platform, I think anything over 3.5 should do, but no sensors even with 3.9


I had the original 3.2, 3.5 which I added in hopes, and 3.9 -- so 3 kernels total. 


Yes, the botched OS could have been rescued, Grub Customizer would have fixed it, but the desktop had become an ugly mixture of Mint+Unity so I deleted partition and reinstalled.


I don’t know how the extra desktops got added, perhaps some trigger in the install, but I’m sure I didn’t. I didn’t check the time stamps of the xsessions, I don’t enjoy forensic work, besides the OS was smelling of Unity so it had to go regardless.


For the benefit of anybody googling the mobo is Asus P8Z77-I DELUXE/WD and my Gigabyte GA-Z77X-UD5H also needed kernel 3.5+ to be crash-free.

BTW, I’ve installed 3.5.1 form the same place on several machines and nothing other than kernel was ever installed. From bash_history:

wget -O linux-kernel-3.5.1 [http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.5.1](http://dl.dropbox.com/u/47950494/upubuntu.com/linux-kernel-3.5.1)
chmod +x linux-kernel-3.5.1
sudo sh linux-kernel-3.5.1

The actual kernel is 3.5.1-030501-generic #201208091310

Is that a better script? I had no idea this could happen.. hypothetically... could somebody compile a kernel with malicious code and propagate it in this manner?

---

### Post by buzzingrobot on 2013-05-05
> **Rebelli0us said:**
> hypothetically... could somebody compile a kernel with malicious code and propagate it in this manner?

Hypothetically, sure  If people are willing to to download and run the script without looking at it, it's a piece of cake.

But, the script in question was innocuous. It retrieved and installed kernel files from Ubuntu's kernel PPA. If those files contained something other than kernel files, then everyone who installed the 3.9 kernel from that PPA would have had the same problems and Ubuntu would have have a minor flap on its hands.

Did you actually launch those other DE's?  If not, perhaps they were just created as display manager entries when the new grub config was created.

---

### Post by Rebelli0us on 2013-05-05
> **buzzingrobot said:**
> Hypothetically, sure  If people are willing to to download and run the script without looking at it, it's a piece of cake.

But, the script in question was innocuous. It retrieved and installed kernel files from Ubuntu's kernel PPA. If those files contained something other than kernel files, then everyone who installed the 3.9 kernel from that PPA would have had the same problems and Ubuntu would have have a minor flap on its hands.

Did you actually launch those other DE's?  If not, perhaps they were just created as display manager entries when the new grub config was created.

Yes, like I said in the OP a Unity-like OS **without taskbar** booted right after the update. I tried Appearance options and got Unity-style square ON/OFF switches. Ctrl+Winkey did nothing, Alt-F2 likewise. It was definitely a crippled Unity. Logged off to root, same thing. I was still getting Mint MDM though, so I was able to select MATE in mdmsetup's "Default Session". However, Mint was messed up.

---

