---
title: "Again Nvidia Drivers and X problems"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by IChertov on 2007-04-15
X server fails after reboot, familiar ain't it ;)
What happened was I updated some things with the Update Manager and after I restarted the PC X failed no problem it has happened before I can fix it ;) i replaced "nvidia" with "nv" and i loaded GDM :)
I'm a beginner by the way so if you plan to explain something please try to explain ti like it's for an idiot :) 
So GDM loaded.. i thought to remove nvidia drivers 
I'm using Ubuntu 6.10
 *sudo apt-get remove nvidia-glx nvidia-kernel-common*
Ok so now i thought that I should Install them again :-)
* sudo apt-get install nvidia-glx nvidia-kernel-common*

so then I changed the xorg.conf file the thing to be "nvidia" instead of "nv"
reboot or exit X :( and again :-( X Server not working ...
it said 
(EE) Screen(s) found, but none have a useable configuration
..
I tried to search in a couple of forums and I asked uncle Google... i found people with similar problems but somehow i didn't understand what to do and how to do it :-(
I'm using Nvidia GeForce 4 MX440 

Please help the poor boy

---

### Post by wjp.reg on 2007-04-15
Have you tried booting into rescue mode and then running
```
dpkg-reconfigure xserver-xorg
```?

Works for me.

What release of ubuntu are you using?  In feisty there is now a very handy restricted driver manager which can load your nvidia driver.

Cheers!

---

### Post by IChertov on 2007-04-15
i'll remove nvidia-glx and nvidia-kernel-common now 
then I'll reboot in Rescue mode.. then install nvidia again? or first reconfigure X?? 
:)

so I've tried to do that thing, but the X gave me some other crap.. I saw only "nv" and no "nvidia"
last time when it ran ok with the drivers installed it was "nvidia"

---

### Post by IChertov on 2007-04-15
Need help...

---

### Post by kapampa on 2007-04-15
I have the same problem and the same driver you have. It seems that upgrading to feisty gives some problems with the old 6.10 nvidia settings.
Well it's still in development!  #-o :cry:

---

### Post by IChertov on 2007-04-15
sooner or later someone will help :) 
hopefully 
:)

---

### Post by wjp.reg on 2007-04-15
I'm running feisty with nvidia (GeForce MX 4000) and when first upgrading from 6.10 I lost xwindows.  I didn't go about installing/uninstalling anything.  I rebooted and ran rescue mode, and did as I described above in my previous post.  Feisty then started up in "nv" mode and I then went to the "System" menu | Admin, and ran the restricted drivers manager and my nvidia was restored.

On a clean install I believe that restricted drivers manager will install the appropriate drivers for you.

Here's a link that explains this: [http://ostoolbox.blogspot.com/2007/03/ubuntus-restricted-drivers-manager.html]("http://ostoolbox.blogspot.com/2007/03/ubuntus-restricted-drivers-manager.html")

---

### Post by Wee Nyaff on 2007-04-15
> **wjp.reg said:**
> I'm running feisty with nvidia (GeForce MX 4000) and when first upgrading from 6.10 I lost xwindows.  I didn't go about installing/uninstalling anything.  I rebooted and ran rescue mode, and did as I described above in my previous post.  Feisty then started up in "nv" mode and I then went to the "System" menu | Admin, and ran the restricted drivers manager and my nvidia was restored.

On a clean install I believe that restricted drivers manager will install the appropriate drivers for you.

Here's a link that explains this: [http://ostoolbox.blogspot.com/2007/03/ubuntus-restricted-drivers-manager.html]("http://ostoolbox.blogspot.com/2007/03/ubuntus-restricted-drivers-manager.html")

I am such a newbie I do not know how to get in to rescue mode. 
 I have the same basic problem as the original poster except that I am running an Nvidia geforce 7600gs.  I went in to Display effects and was asked "do you want to enable nvidia graphics card" I did and then when it had finished unpacking it asked me to restart. I did and now I have a screen that says " Failed to start the X server (your graphical interface). It is likely it is not set up correctly.  Would you like to view the X server output to diagnose the problem."

I do not know what to do from this point so the machine is just sitting there while I do this and some other work on my work Windows machine.
Can someone please help me with simple instructions.  A simple kick up the bum will be accepted as due for my foolishness.
Thanks in advance
Alan

---

### Post by wjp.reg on 2007-04-15
You can get into rescue mode by pressing esc when the system reboots which displays the startup menu.  Just select rescue mode.

Once booted, then run ```
dpkg-reconfigure xserver-xorg
``` and answer all the questions, most of which you are safe to accept the defaults (at least in my case :-)

Ubuntu SHOULD auto detect your video and monitor and you should be good to go.  If not, I can't help any further and suggest you search the forum some more.

good luck

---

### Post by IChertov on 2007-04-15
> **wjp.reg said:**
> You can get into rescue mode by pressing esc when the system reboots which displays the startup menu.  Just select rescue mode.

Once booted, then run ```
dpkg-reconfigure xserver-xorg
``` and answer all the questions, most of which you are safe to accept the defaults (at least in my case :-)

Ubuntu SHOULD auto detect your video and monitor and you should be good to go.  If not, I can't help any further and suggest you search the forum some more.

good luck

When i Did that X server configuration didn't found the driver "nvidia" it found "nv"
:(

---

### Post by Lurgen on 2007-04-15
I share your pain, I too have restarted my machine only to discover that X won't start. Cryptic (and poorly formatted) error messages didn't help either.

As a potential replacement for Windows, Ubuntu isn't making me particularly happy this week...

The fix (for me) was to force a re-install of the nvidia drivers. This forced it to recompile with the new kernel version. Not that any of the error messages make this particularly easy to figure out. I now keep the official nVidia drivers in my home directory, just waiting for the next time an update kills the machine.

The cause turned out to be an automatic update, which changed my kernel version. This automatic update rebooted my system while I was AFK (overnight), causing my VMWare lab to shut down dirty and my working notes file (in a text editor) to be lost. Pretty stupid way to handle updates, and I can't figure out a way to make it NOT reboot without my consent.

I get why the nvidia drivers that ship are so poor, it's the whole pre-compiled proprietary code binary files, along with the licensing thing but as an end-user I honestly don't care. What I care about is that I can't rely on the machine to be up and running. Sure, I know how to make it tick again, but my wife wouldn't have a clue how to download and install a video driver from a console session.

---

### Post by Steve H on 2007-04-16
> **wjp.reg said:**
> Have you tried booting into rescue mode and then running
```
dpkg-reconfigure xserver-xorg
```?

!

I'm having a similar problem, I upgraded to Feisty last night, and now my Nvidia drivers aren't working: so no X desktop. I didn't have time to try anything last night so I will try this when i get home.....

---

### Post by TURNER on 2007-04-16
> I'm having a similar problem, I upgraded to Feisty last night, and now my Nvidia drivers aren't working: so no X desktop. I didn't have time to try anything last night so I will try this when i get home.....

If in doubt....kick it out....

I've found that the best way of dealing with such issues is simply trial and error, perhaps one day you can then write a how to for new users experiencing similar.

I'd reconfigure X, or if you also receive the infamous X cannot start screen then simply ok out of it and press CTL-ALT-F1 log in via terminal and either:

```
dpkg-reconfigure xserver-xorg
```

Or if you backed up your xorg.conf simply revert back to the previously working version:

```
sudo cp /etc/X11/xorg.conf (your back up file name) /etc/X11/xorg.conf
```

Hope this helps!

---

### Post by wjp.reg on 2007-04-16
run it again and scroll down the list of drivers.  If nvidia is not there, it may not have been installed.

So run **dpkg-reconfigure xserver-xorg** again

---

### Post by Steve H on 2007-04-16
I have finally managed to get my Desktop up and running again. It wasn't quite as simple as it seemed at first. I managed by doing the following:

First I ran ¨dpkg-reconfigure xserver-xorg¨ as a lot of people had suggested, but after 2 times (once using ¨nvidia¨ drivers and one using ¨nv¨) i was still not getting a desktop. Looking through the xorg.conf it was saying ¨screens found: no usable modes¨. So instead of accepting the defaults created by the reconfigure, I disabled ¨DRI¨ and only allowed the maximum resolution to be 1024x768. BINGO! I now had a desktop to get on the Internet.

As soon as i got on the desktop I got a message saying I needed to install ¨linux-restricted-modules-2.6.20-15-generic¨. Which I did, (as well as installing the recommended packages as well). When it tried to install the ¨nvidia-glx¨ i kept getting the error:

¨E: /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2¨

No matter how many times i tried the error kept returning.

So I tried using the ¨Restricted Packages¨ listed in System -->Administration. But i kept getting the same error, and nothing was allowing me to use the old driver.

So i went to Nvidia ([_this page_]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html")) and downloaded the latest drivers.

I quit out of the X desktop, ran a new console (ctrl-alt-F1) then killed the gdm process:

sudo killall gdm

next I ran the Nvidia driver script, went through all the steps, and Bob&#347; your uncle, Ie got my Desktop back at Full resolution, with glx extensions working ( I tried glxgears, just to be sure).

Finally......

Hope this helps.

---

### Post by IChertov on 2007-04-16
> **Steve H said:**
> I have finally managed to get my Desktop up and running again. It wasn't quite as simple as it seemed at first. I managed by doing the following:

First I ran ¨dpkg-reconfigure xserver-xorg¨ as a lot of people had suggested, but after 2 times (once using ¨nvidia¨ drivers and one using ¨nv¨) i was still not getting a desktop. Looking through the xorg.conf it was saying ¨screens found: no usable modes¨. So instead of accepting the defaults created by the reconfigure, I disabled ¨DRI¨ and only allowed the maximum resolution to be 1024x768. BINGO! I now had a desktop to get on the Internet.

As soon as i got on the desktop I got a message saying I needed to install ¨linux-restricted-modules-2.6.20-15-generic¨. Which I did, (as well as installing the recommended packages as well). When it tried to install the ¨nvidia-glx¨ i kept getting the error:

¨E: /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2¨

No matter how many times i tried the error kept returning.

So I tried using the ¨Restricted Packages¨ listed in System -->Administration. But i kept getting the same error, and nothing was allowing me to use the old driver.

So i went to Nvidia ([_this page_]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html")) and downloaded the latest drivers.

I quit out of the X desktop, ran a new console (ctrl-alt-F1) then killed the gdm process:

sudo killall gdm

next I ran the Nvidia driver script, went through all the steps, and Bob&#347; your uncle, Ie got my Desktop back at Full resolution, with glx extensions working ( I tried glxgears, just to be sure).

Finally......

Hope this helps.


Could you explain what is the Nvidia Driver Script...

?

isn't it going to be easier if someone would just post the contents of his working xorg.xonf file.. and we'll replace what's wrong and that's it :) 
Always watch what a fat guy is ordering in a restaurant ;) :D

---

### Post by Steve H on 2007-04-16
I have attached my xorg.conf, as it is now, with just one monitor running (no-TV out).

I did forget to mention that i ran the following:

¨sudo nvidia-settings¨

from the command line once i was back on the desktop after i installed the Nvidia proprietary driver script, in order to get a working xorg.conf, then i restarted the X server again.

The Nvidia driver script is just the bash shall installer script that comes with the driver from Nvidia. It just asks things like ¨Do you want to download the distribution specific driver for your distribution?¨ , ¨Do you want the X server to be configured?¨. It is just the usual driver installation questions, sorry if i made it sound more complicated than it is.

---

### Post by kapampa on 2007-04-16
I have now re-installed feisty in "clean" way (Formated my hard drive) :) . 
Still when i run feisty restricted drivers and enable the GeForce 4 MX on reboot my xserver fails!
I think it's a problem with the new feisty nvidia repositories!

---

### Post by Steve H on 2007-04-16
Have you installed the Nvidia drivers from their site? It seemed to work for me, you must do it from the root terminal with GDM killed. (See post above)

---

### Post by IChertov on 2007-04-16
When I finish my work i'm planing to do the following :)

correct me if I'm wrong 
log in in recovery mode directly then i will type
 ```
sudo apt-get remove nvidia-glx nvidia-kernel-common
```
hoping that that would remove everything that I have installed before :)
next i'll reboot and log in in the working desktop with no drivers :) I'll take the suitable drivers from NVIDIA's site \Give me a hint about the drivers ;) ( Ubuntu 6.10 Edgy - GeForce 4 MX 440 ) \
so i'll put them into an easy place like /home/my user/ :)
CTRL+ALT+Backspace :) 
```
 killall gdm 
```
then 
```
 sh /home/my user/NVIDIA-drivers.run 
```
hopefully if everything goes well and the machine installs the drivers i'll type in
```
dpkg-reconfigure xserver-xorg
```
and i'll try to find in the Graphics driver "nvidia" the rest default
if nothing happens I'll manually edit xorg.conf and disable DRI :)
if that doesn't work 
I DON'T KNOW :)

---

### Post by linuks on 2007-04-16
> **IChertov said:**
> When I finish my work i'm planing to do the following :)

correct me if I'm wrong 
log in in recovery mode directly then i will type
 ```
sudo apt-get remove nvidia-glx nvidia-kernel-common
```
hoping that that would remove everything that I have installed before :)
next i'll reboot and log in in the working desktop with no drivers :) I'll take the suitable drivers from NVIDIA's site \Give me a hint about the drivers ;) ( Ubuntu 6.10 Edgy - GeForce 4 MX 440 ) \
so i'll put them into an easy place like /home/my user/ :)
CTRL+ALT+Backspace :) 
```
 killall gdm 
```
then 
```
 sh /home/my user/NVIDIA-drivers.run 
```
hopefully if everything goes well and the machine installs the drivers i'll type in
```
dpkg-reconfigure xserver-xorg
```
and i'll try to find in the Graphics driver "nvidia" the rest default
if nothing happens I'll manually edit xorg.conf and disable DRI :)
if that doesn't work 
I DON'T KNOW :)

Hi Chertov,

The last line, dpkg-reconfigure xserver-xorg won't be necessary. I installed my drivers from nvidia site and when they installed you are asked to run nvidia-conf?? script. It will place correct values in xorg.conf so you don't have to modify it. You can if you must, later on, that is. 

Why go into a rescue mode? Can you get to a terminal? GDM will try to log you in on terminal 7 and you can press control + alt + F1 and log in. Log in and try to install. You may need network connection working when installing Nvidia drivers.

Good luck.

Linuks

---

### Post by IChertov on 2007-04-16
> **linuks said:**
> Hi Chertov,

The last line, dpkg-reconfigure xserver-xorg won't be necessary. I installed my drivers from nvidia site and when they installed you are asked to run nvidia-conf?? script. It will place correct values in xorg.conf so you don't have to modify it. You can if you must, later on, that is. 

Why go into a rescue mode? Can you get to a terminal? GDM will try to log you in on terminal 7 and you can press control + alt + F1 and log in. Log in and try to install. You may need network connection working when installing Nvidia drivers.

Good luck.

Linuks

Thanks ;)
Network connection ? :) well i do have internet and my connection is shared trough the network ;) so it must be working ;)

---

### Post by Kuoi on 2007-05-23
Am I missing something or what ?

I'm trying to install the official drivers but this is only getting worser than worse.

I've uninstalled the drivers , but what now ?

When I try to start to installer in "recovery console" it gives me an error that I run in Level1 , and I have to run in Level3.

When i reboot , and type "killall gdm" in the "terminal as root" , my computer hangs , and I have to reset it to boot again.
I can't do anything else then .

I have seen an error too , that X-server is still running at some point , but I've tried so many things , that I don't know anymore when this came up.

QUESTION : How can I open a "terminal as root" when gdm is not loaded ?

Kuoi

---

### Post by syko21 on 2007-05-23
Hit ctrl+alt+f2 and log in with your user name and pw.
```

sudo su
(password)
/etc/init.d/gdm stop

```

dont use killall gdm, its not specific.

---

### Post by Kuoi on 2007-05-23
Many thanks ...

It almost worked , but now I get an error that I have the **wrong kernel**.
I'm using Ubuntu Studio  , must I set Ubuntu Feisty as default in Grub , or something ?

Kuoi

---

### Post by Kuoi on 2007-05-23
Still nothing works , after I've uninstalled Ubuntu Studio.

I'm sick of it , and forget about Beryl , because everything is working well , exept that I have the feeling that my videocard is not completely used as it should be.

For example it's an AGP , and in Xorg it tell's me it's pci.
Now , I know , all are pci , but I don't see a sentence with AGP : yes  or something.
I've seen that before on examples from Xorg files in this forum.

Question : How can I see what driver is loaded ?

Kuoi

---

### Post by psmar on 2007-05-23
try running " sudo dpkg-reconfigure xserver-xorg" choose the vesa setting under graphic card type ( its the generic vga driver) then once rebooted click on the restricted nvida driver that was the only fix that worked for my geforce 4 mx 400
may the buntu be with u

---

### Post by Kuoi on 2007-05-23
I've just tried Envy , and now it's the right driver "nvidia" in Xorg.conf.

Greetings, Kuoi

---

