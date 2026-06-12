---
title: "Firefox 5 in Lucid?"
date: 2011-06-24
forum: Apple Hardware Users
---

### Post by rsavage on 2011-06-24
Hi all, 

I'm currently running FF5 in natty, but am sort of thinking about going back to lucid or maverick for various reasons.  However, I want the latest version of firefox so could somebody confirm for me if the following works please?

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update

FF5 should now appear in synaptic?


What I want to do is create a minimal install (as minimal as possible), but with firefox as the browser.  I'm actually thinking of possibly giving a debian installation a spin (similar to mintppc, but using a compiz standalone session instead of openbox) so any info regarding FF5 and debian would be appreciated as well.  Do you think the ppa would work with debian stable?  

Cheers!

---

### Post by Untitled_No4 on 2011-06-25
Well, the first point one should make is that Debian has Iceweasel, not Firefox. As far as I know there is no repository for Debian which offers FF, so you have to download it from FF's website and manually install it.

The second point is that Debian hasn't got a PPA system. New software is always released to Sid first, and then to the Testing branch. You can run one branch of the OS and install packages from the repositories of the other branches by using Apt Pinning. A Google search will show you how to do it, it's not that difficult.

As for Ubuntu Lucid and Firefox5, if you go to [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable) which is the page of the Mozilla Team, you can see they have repositories for Lucid, and they also say:
```
Firefox Stable releases.

Aimed at Lucid and Maverick users who want to use a modern browser which starts faster than you can brew your morning coffee
```
So it should (99.9%) work.

---

### Post by rsavage on 2011-06-25
Thanks for the reply.  However, if you look here [http://mozilla.debian.net/dists/squeeze-backports/iceweasel-5.0/](http://mozilla.debian.net/dists/squeeze-backports/iceweasel-5.0/) there are no power pc versions of iceweasel-5.

A bit of googling tells me you can use the ubuntu repositories with debian.  Simply editing the source list is one way.  So the only question remains how many extra packages will need updating to get it to work in debian.  I suppose the apt pinning you describe would be used for this.

The reason I asked if somebody could check it out in lucid was because the lucid files are so much smaller than the maverick/natty ones.  It made me a bit suspicious.

---

### Post by rsavage on 2011-06-25
*Removed post as the information was incorrect.*

---

### Post by linuxopjemac on 2011-06-25
I would not install Ubuntu packages within Debian.

---

### Post by rsavage on 2011-06-25
Yes, I keep reading that although nobody puts a satisfactory explanation.  Since you can use debian packages in ubuntu then I don't understand why you can't use ubuntu packages in debian.  Other people report it works fine though so you don't know who to believe.

---

### Post by rsavage on 2011-07-05
To answer my own question from the original thread: No you can't get a ppc version of firefox 5 using this method.  I thought I had invesigated this pretty thoroughly before, but I must have overlooked that there is actually no ff5 package!  There are v5 packages for everything else except the 'firefox' package.  Which I think is a bit odd.  
 
So you would have to compile firefox from source to get it into lucid/maverick.
 
It seems the only way to 'easily' get automatic updates for firefox is to continue updating to the latest version of ubuntu.  I've recently installed lubuntu 10.10 and was quite impressed so I'll install a natty lubuntu now.  Linuxopjemac, btw I think lubuntu could give your mintppc some stiff competition!! Time to boot mintppc using auto login: 47 seconds.  Time to boot lubuntu 10.10 using auto login 36 seconds! ;)

---

### Post by linuxopjemac on 2011-07-05
thanks rsavage for the competition experiment :) I stick with MintPPC anyway if you don't mind ;)

---

### Post by rsavage on 2011-07-05
Yes I thought you'd say that! I actually thought mintppc would be quicker due to all the hype you read about debian so I was surprised by the result! Maybe it's becasue I followed some installation instructions I found on a google search instead of your proper ones? I can't guarantee everything works in lubuntu as well as it does in mintppc, but I haven't come across any big issues so far. I'll look over at mintppc for the solution!

---

### Post by linuxopjemac on 2011-07-05
What solution are you looking for ?

The thing with Lubuntu is that you can't get all the programs I selected by default. You will have to add them yourself. Lubuntu has a very small amount of desktop applications installed, just like LXDE in Debian.

---

### Post by rsavage on 2011-07-05
Hmm...let me think.... well the first one I need is a way to select cpu frequency. Currently it is set to maximum like it is in mintppc too. Is there a nice applet I can install? The one I have got just displays the speed and doesn't give you an option to change it like it does in standard ubuntu. With Cpu set to maximum the fan comes on alot. I'll install powernowd to do this automatically, but for the moment I want to do it manually.
 
I wanted to test suspend/hibernate, but the suspend/hibernate options on the logout menu only give me the screensaver. This I noticed was a problem on mintppc too. Is there a way to activate these menu options?
 
Setting the power button to activate suspend (using gnome power management i think?) didn't do anything. This works in normal ubuntu. I'll investigate this although suspend is something I never use. I did get it to work using powerprefs (just like mintppc).
 
No problems with wifi.
 
Does mintppc hibernate work for a G4 ibook?
 
Thanks for any info on the above.

---

### Post by rsavage on 2011-07-05
Linuxopjemac, I noticed on your forum that somebody was after mac osx instructions for usb.  Don't know if this works [https://help.ubuntu.com/community/Installation/FromUSBStick#From Mac OSX](https://help.ubuntu.com/community/Installation/FromUSBStick#From Mac OSX)

---

### Post by linuxopjemac on 2011-07-05
suspend does not work with nvidia based laptops, that's all I know.

---

### Post by linuxopjemac on 2011-07-12
I backported Iceweasel 5 from mozilla.debian.net for PowerPC / Squeeze. People installing MintPPC 9 will have Iceweasel 5 automatically.

---

### Post by linuxopjemac on 2011-08-19
As of this weekend MintPPC 9 users will have Iceweasel 6 :P

---

### Post by rsavage on 2011-09-06
Just to keep this thread updated..... I detailed my installation of Lubuntu Natty in this thread [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) .

Installing the latest firefox (currently 6.01) into lucid/maverick gets discussed again in the above thread, and it should be quite easy to do it by installing the packages from natty.  If anybody wants instructions then please ask and I'll be happy to post.  

From a bit of googling it seems firefox 3.6.x will be put out to pasture soonish and when this happens firefox in lucid and maverick will get upgraded automatically.

---

