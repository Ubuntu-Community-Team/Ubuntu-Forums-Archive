---
title: "Maverick install on new 7-1 13&quot; MacBookPro"
date: 2010-11-04
forum: Apple Hardware Users
---

### Post by blueridgedog on 2010-11-04
I did a reinstall of Ubuntu on my new Mac yesterday and thought I would document the process for anyone who may benefit.

From within MacOSX, I installed rEFIt, boot menu manager/loader from their source forge site:

[http://refit.sourceforge.net/#download](http://refit.sourceforge.net/#download)

Still in MacOSX, I used disk utility to shrink my MacOS partition and make two new partitions, one for swap (1gb) and one for Ubuntu (50gb in my case).

Instructions for this are located here:

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

Still while inside MacOSX you need to identify folders in your home directory that you want to access from within Linux and remove the ACL properties of the directory, such as:

From within your home directory:
```
chmod -N ./Music/
```

The -N option is not in our Linux man pages as it is ACL specific, but can be found in Apple and Sun man pages.  -N strips ACL permissions from the file or directory so applied.

Additionally, you may want read permissions to some of your files on the Mac:

```
chmod -R 755 ./Music/
```

This changes your Music folder and all subfolders and files to be world readable.  Since I do not plan disabling journaling on the MacOS side, I am not going for write access to the Mac partition, hence the 755 permissions.

With the partions created, ACLs removed and permissions sorted, I booted on the current Maverick 32 bit install disk and setup the Mac as is generally described here:

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)
and
[https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

Upon first boot, the first thing to do was connect it to a wired network (the wireless hardware needs a driver that has to be downloaded). 

Once connected I ran:

```
sudo add-apt-repository ppa:mactel-support && sudo apt-get update

```

After that I installed the proprietary hardware drivers for the wireless hardware and the graphic hardware.

A variety of packages needed to be installed to make things work:

```
sudo apt-get install nvidia-bl-dkms macfanctld v86d applemc-dkms applesmc-dkms nvidia-bl-dkms pommed bcm5974-dkms xserver-xorg-input-synaptics ubuntu-restricted-extras git-core libdbus-1-dev libconfuse-dev libaudiofile-dev libasound-dev libpci-dev libdbus-glib-1-dev libglade2-dev libgtk2.0-dev libx11-dev libxext-dev libxpm-dev
```

New modules were installed with:

```
sudo modprobe nvidia-bl
sudo modprobe coretemp
```

Coretemp needs to be added as a module to load at start, so

```
sudo vi /etc/modules 
```

and add coretemp to the end of the file.

To make DVD playback work, I used the new shell script:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

You can't reboot the Mac out of the box, but instead you have to make a small change to grub:

(note here I use vim, in other places I use vi, but use whatever editor you are comfortable with, gedit works great too!)
```
sudo vim /etc/default/grub
```

and change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"

Then run:

```
sudo update-grub
```

To get the sound working, I added 
```
options snd-hda-intel model=mbp55
```

to the end of the alsa-base.conf file with:

```
sudo vi /etc/modprobe.d/alsa-base.conf 

```

Reboot then run alsamixer and select the front speakers, press "M" to unmute then arrow up to max out the volume.

To make the Mac keyboard items work, you need the latest pommed:

```
git clone git://git.debian.org/git/pommed/pommed.git
cd pommed
make
```

Once you have the new pommed binary, you can install it in place of the one you have with:

```
sudo service pommed stop
sudo cp pommed/pommed /usr/sbin/pommed
sudo service pommed start
```

Then you can edit the pommed.conf file and add the pommed configuration linked to above:

```
sudo cp /etc/pommed.conf /etc/pommed.conf.bak
sudo vim /etc/pommed.conf
```

After editing the file, restart pommed:

```
sudo service pommed stop
sudo service pommed start
```

After working with system a bit I noticed the mic input volume was low, so I installed the pulse audio manager:

```
sudo apt-get install paman
```

Run it with paman and select your analog input, and put the percentage at about 250%.

I also grew tired of the red led coming out of the speaker jack and muted the S/PDIF via alsamixer.

As a full time Ubuntu user, I am happy with the outcome, but have two complaints...one the sound quality on the laptop under Linux is so poor to make it almost moot to get sound working (I still boot into MacOSX to play music), two the install on this latest Mac hardware is a bit more complex than it should be.

All in all the new MacBookPros are very nice and getting Ubuntu on one and working well makes them even better.  Tonight I will try some external speakers and see if that changes things.

---

### Post by lael on 2010-11-04
I have a 6,1 (latest 17" MBP) and my install was pretty similar.

Pommed definitely needs to be rebuilt in the PPA.  I've been pulling/building/using the latest pommed too.

I still haven't been able to get my mic working yet.  I used gnome-alsamixer instead of the command line version.  I'm not sure that this is the same issue that you have but I noticed that I had to turn up the 'Surround' to get stereo sound.  give that a try.

---

### Post by blueridgedog on 2010-11-04
The install guide linked to above states:

Microphone
The microphone is muted out of the box. Go to System-->Preferences-->Sound-->Input and either move the slider or click the box to unmute. Tested working with Skype.

There is no apparent way to increase the microphone volume in the sound preferences.
You can change microphone level over 100% with paman:

```
sudo apt-get install paman
```

Perhaps this will help with your mic issue.  I will try the surround tip.  Thanks.

---

### Post by Clordio on 2010-11-04
A couple questions for you as I am having some difficulty (I am only using the Live CD right now to make sure everything works).

Did you use 64 bit Maverick?

Is there something about the live cd that prevents you from getting pommed because when I try to install it I get an error saying

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pommed : Depends: libconfuse0 (>= 2.5) but it is not installable
E: Broken packages
```

The only thing holding me back from actually installing is this screen brightness issue. As it stands if I modprobe the nvidia-bl or mbp_nvidia_bl the screen goes to full brightness. But if I change the brightness it dims WAY down and I can not get it to full brightness again, the screen stays incredibly dim. Any ideas?

---

### Post by blueridgedog on 2010-11-05
> **Clordio said:**
> A couple questions for you as I am having some difficulty (I am only using the Live CD right now to make sure everything works).

Did you use 64 bit Maverick?

Is there something about the live cd that prevents you from getting pommed because when I try to install it I get an error saying

The only thing holding me back from actually installing is this screen brightness issue. As it stands if I modprobe the nvidia-bl or mbp_nvidia_bl the screen goes to full brightness. But if I change the brightness it dims WAY down and I can not get it to full brightness again, the screen stays incredibly dim. Any ideas?

I use 32 bit. I would not be surprised if you had issues getting the new pommed working on the live cd.  Once you do the install, the back light issue is resolved.  Mine works fine as configured.

---

### Post by Clordio on 2010-11-06
Good to know.

Just an update, I was able to get pommed (I found my problem was I had not opened up the universe repo's yet) and was able to get a weird effect with the brightness. Each time I upped the brightness it would flicker really bright and then back to really low until I reached the highest setting where I could finally get some visibility.

For future reference I was using the 64-bit ubuntu live cd Maverick 10.10. The nvidia driver I used to get the flickering effect but still max brightness was the mbp-nvidia-bl-dkms (nvidia-bl-dkms produced no flickering but top brightness was inadequate).

I will burn a 32-bit live cd to check if this might be a 64-bit problem. If I get the same results I will do an actual install of 64-bit and report back. As it stands I am considering this a possible 64-bit problem or live-cd problem.

-Clordio

**[UPDATE]**

Ok, so I tried it on the 32-bit live-cd and experienced the very same problem. I played around with mbp-nvidia-bl-dkms and nvidia-bl-dkms and I seem to have more success in actually gaining some decent brightness and actual full brightness but very glitchy(flickering between dim and bright while changing) with mbp-nvidia-bl-dkms. It almost appears to me that the computer is trying to look at two different settings for the backlight (note: I only had one of these drivers installed at a time) which leads me to believe that the computer is constantly referring to the live-cd's configuration as well as the newly installed drivers.

I will now actually install the 64-bit Maverick and test settings on that. Hopefully the live-cd environment is just the problem.

-Clordio

P.S.

I apologize for thread-jacking blueridgedog but this is the first I have heard of this problem after intense googling and board searching so I would like to document this just in case someone else experiences the same thing.

---

### Post by blueridgedog on 2010-11-07
> **Clordio said:**
> I apologize for thread-jacking blueridgedog but this is the first I have heard of this problem after intense googling and board searching so I would like to document this just in case someone else experiences the same thing.

No thread jacking here...I was just posting my work so that others may get some help.  I too had the odd adjustment issue with screen brightness until I installed the nvidia driver and the packages mentioned.  I suspect a true install with the display driver will work for you.  I have put Linux on my mac several times now that I have the partitions setup and am considering getting it "about right" then making an ISO that others can download with remastersys.

---

### Post by linuxopjemac on 2010-11-07
> I have put Linux on my mac several times now that I have the partitions setup and am considering getting it "about right" then making an ISO that others can download with remastersys.

That is a very good idea !

---

### Post by Clordio on 2010-11-07
I have discovered the problem! :D

So installed 64 bit maverick and had the exact same problems. About ready to pull my hair out I realised that the nvidia 3d driver (proprietary) still needed to be installed, which necessitates a reboot. I never installed it while trying the live cd because you can not successfully reboot :P

So just a heads up for any future installers. Be sure to install the proprietary nvidia driver for 3d. I thought it was non-essential but it really caused some problems.

Thank you blueridgedog for your help!

-Clordio :guitar:

---

### Post by Clordio on 2010-11-08
**[YET ANOTHER UPDATE]**

I'm not sure if you or anyone else has tried this but I was playing with alsamixer and if you un-mute the surround sound and up it to a little over your preferred front speaker level you get pretty decent sound! Check it out and let me know if you already knew of this.

I found I liked the levels at 79 for front speaker and 81 for surround speaker. :grin:

---

### Post by theSuperman on 2010-11-09
I have a new 7,1 Macbook (from what I hear, the setup is similar to the MBP), and I noticed that my left speaker is quieter (underpowered, less bass) than the right. I have played with Alsamixer and nothing there has changed that. Am I the only one seeing this? Its really noticeable when you click "Test Speakers."

For me, I have not needed Pommed; the keys seem to work good enough for me. By the way, after I installed the Proprietary Nvidia drivers, I was unable to change the brightness until I added```
Option "RegistryDwords" "EnableBrightnessControl=1"
``` to the Device section of xorg.conf. Just thought I would throw that in there, since it caused many stressful hours to figure that out.

---

### Post by Clordio on 2010-11-09
I had not noticed it before but after doing the test speaker option in preferences I do have more volume and bass in the right speaker. All I can do is mess with alsamixer and it does not appear to help.

Good find I wonder if anybody has any suggestions.

---

### Post by theSuperman on 2010-11-09
> **Clordio said:**
> I had not noticed it before but after doing the test speaker option in preferences I do have more volume and bass in the right speaker. All I can do is mess with alsamixer and it does not appear to help.

Good find I wonder if anybody has any suggestions.

I'm just glad someone else notices it too. In Sound Preferences, under the Hardware tab, you can play around with different profiles. Everything else other than Analog Stereo Duplex results in major audio lag. the 4.0 profile almost works...it just sounds like the speakers aren't being detected properly.

---

### Post by blueridgedog on 2010-11-10
Un-muting and boosting the surround volume in alsamixer helped my sound quality, but the sound is still generally poor compared to the same hardware running under MacOSX.

---

