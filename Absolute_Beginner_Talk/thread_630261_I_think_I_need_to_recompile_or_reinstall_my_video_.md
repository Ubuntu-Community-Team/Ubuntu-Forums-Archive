---
title: "I think I need to recompile or reinstall my video card drivers. Error before log-in."
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by sentientd on 2007-12-03
My husband has deployed overseas and I have no idea what I'm doing or where to start. Is there anyone that can help me?

A while ago I think I updated my Ubuntu kernel and when I restarted I couldn't get to my login screen or desktop. 

The loading screen appeared and after that was through I was presented with a funky looking error page about my Nvidia drivers.  I took some pictures of it so that everyone could see what it said.

[IMG]http://i125.photobucket.com/albums/p64/sentientdevice/I%20fail%20at%20Ubuntu/Picture039.jpg[/IMG]

[IMG]http://i125.photobucket.com/albums/p64/sentientdevice/I%20fail%20at%20Ubuntu/Picture040.jpg[/IMG]

[IMG]http://i125.photobucket.com/albums/p64/sentientdevice/I%20fail%20at%20Ubuntu/Picture042.jpg[/IMG]

My friend says that this is a very simple fix but I have absolutely no idea where to begin!  

He says I am supposed to reinstall or recompile my video card drivers.

When I say I have no idea where to begin I really mean it. I don't know how to do anything with Ubuntu especially if I can't even get to my desktop... 

I'd love to be able to fix this myself... but I am absolutely clueless! Can anyone tell me where to start? 

I've tried to read about my problem... but most of the solutions assume that the reader knows the most basic things about using Linux... and well... I don't know those things... It's very sad :(

---

### Post by GSF1200S on 2007-12-03
To get back to a graphic interface, try the following command after it fails to load. Log in at the command line, and type this command:

sudo dpkg-reconfigure -phigh xserver-xorg

Select your monitor resolution (you know this right?) and when it asks what drivers to use, select "nv"

Then, once your back at the command line, type this in (after you login if necessary):

sudo /etc/init.d/gdm restart

If the latter command doesnt get you to a gui, try:

sudo reboot

If you want to try and get 3d stuff going, post back here.. if not, the nv drivers should get you running without the fancy stuff..

---

### Post by sentientd on 2007-12-03
> **GSF1200S said:**
> To get back to a graphic interface, try the following command after it fails to load. Log in at the command line, and type this command:

sudo dpkg-reconfigure -phigh xserver-xorg

Select your monitor resolution (you know this right?) and when it asks what drivers to use, select "nv"

Then, once your back at the command line, type this in (after you login if necessary):

sudo /etc/init.d/gdm restart

If the latter command doesnt get you to a gui, try:

sudo reboot

If you want to try and get 3d stuff going, post back here.. if not, the nv drivers should get you running without the fancy stuff..

OKAY!  Thank you so very much!!!! :biggrin:

I did have a little problem with choosing the resolution because I wasn't sure how to select them.  I can only choose as high as 1024x768 since I didn't know how to choose any higher resolutions in the menu I was presented with.   I just used the arrow keys and pressed enter. Apparently that isn't how its done :P 

But my monitor is large and wide... so 1024x768 just won't do.

Regardless this is very awesome and I'm happy to be able to get back in! thank you thank you thank you!

Before this all happened I was using Beryl, but that doesn't seem to want to launch now. 

Do you have any advice regarding that as well?  

I was really loving my Beryl!

Thank you again for your help! :)

---

### Post by lamalex on 2007-12-03
First off, do you know which version of Ubuntu you are running? You can find out by going to System > About ubuntu, and in that document it should say. If you can't find it, open up a terminal and type ```
cat /etc/lsb-release
```.
If you're running Ubuntu Gutsy 7.04 you can fix your resolution by going to System > Administration > Screens and Graphics. On the Screen section you can change your resolution, and in the graphics card section, changed the driver to nvidia. That will get you beryl back. If you're running an older version, running ```
dpkg-reconfigure xserver-xorg
``` again should allow you to fix everything, but select the nvidia driver, and a larger resolution. Arrow keys and space bar to move around inside of a field, tab key to change fields. Hope that helps!

---

### Post by sentientd on 2007-12-03
> **Iamalex said:**
> First off, do you know which version of Ubuntu you are running? You can find out by going to System > About ubuntu, and in that document it should say. If you can't find it, open up a terminal and type ```
cat /etc/lsb-release
```.
If you're running Ubuntu Gutsy 7.04 you can fix your resolution by going to System > Administration > Screens and Graphics. On the Screen section you can change your resolution, and in the graphics card section, changed the driver to nvidia. That will get you beryl back. If you're running an older version, running ```
dpkg-reconfigure xserver-xorg
``` again should allow you to fix everything, but select the nvidia driver, and a larger resolution. Arrow keys and space bar to move around inside of a field, tab key to change fields. Hope that helps!

Thank you! I have Edgy Eft right now, but I am about to upgrade to Gutsy. 

Earlier when I was selecting the drivers with the sudo thing (hah I dont know what to call it)  I chose "nvidia," but I think that did not work and I had to go with "nv."

But I'm hoping I can upgrade to Gutsy, follow your advice, and go from there. :)

---

### Post by GSF1200S on 2007-12-03
> **sentientd said:**
> Thank you! I have Edgy Eft right now, but I am about to upgrade to Gutsy. 

Earlier when I was selecting the drivers with the sudo thing (hah I dont know what to call it)  I chose "nvidia," but I think that did not work and I had to go with "nv."

But I'm hoping I can upgrade to Gutsy, follow your advice, and go from there. :)

Oh man, im sorry.. you can type those commands again and generate a new xorg.conf. You select your resolution by scrolling down to the chosen resolution and pressing space bar. I really should have thought to say this one..

You cant upgrade to Gutsy from Edgy. Youll have to dist-upgrade to Feisty, and then upgrade to Feisty from there. Thing is, I dont know how well that would go. Alot of that depends on how your husband set it up, and what sources he has set up in sources.list. If your happy with how it currently runs, I might suggest leaving it. It may not give you any issues at all.. They are slowly improving these dist-upgrades..

---

### Post by GSF1200S on 2007-12-03
I didnt notice the Beryl part.. If you upgrade to Gutsy, youll get to use compiz fusion, which is even better. In order to use compositing effects, well need to get your video drivers working. Do you know what video card you have? If we know that, we can either try to install from Synaptic or we can download them from nvidias website and install them from the command line- that will get Beryl back, in Edgy's case...

---

### Post by lamalex on 2007-12-03
I say go for the upgrade. Back up your data first, and then jump in. The worst case is you'll learn a whole lot about Ubuntu, and when your husband comes back, he'll be so impressed with your new Linux skills. We're here to help through every step, and if you need more help, visit us in IRC chat.

---

### Post by sentientd on 2007-12-03
> **GSF1200S said:**
> I didnt notice the Beryl part.. If you upgrade to Gutsy, youll get to use compiz fusion, which is even better. In order to use compositing effects, well need to get your video drivers working. Do you know what video card you have? If we know that, we can either try to install from Synaptic or we can download them from nvidias website and install them from the command line- that will get Beryl back, in Edgy's case...

Thanks! I was able to go back and select all of the resolutions so that's all good!

Do you think I should go through the releases and upgrade to Gutsy? So far I don't mind things too much the way they are now, as long as I can get Beryl working again. :P

Since I really like the way I have Beryl configured right now so I'd probably wait a little while to get Compiz-Fusion anyways unless I can import those settings somehow.  

I'm pretty sure my video card is an Nvidia Geforce 6600.

---

### Post by sentientd on 2007-12-03
> **Iamalex said:**
> I say go for the upgrade. Back up your data first, and then jump in. The worst case is you'll learn a whole lot about Ubuntu, and when your husband comes back, he'll be so impressed with your new Linux skills. We're here to help through every step, and if you need more help, visit us in IRC chat.

That's wonderful! This is actually a lot of fun! Thank you again! :grin:

I'm going to have to go out and learn about creating backups. :)

---

### Post by GSF1200S on 2007-12-03
Well, youre eager enough, so id say go for it. If you upgrade to Gutsy, im not sure if you can still use Beryl- compiz is enabled by default. So you may need to tweak again. As said before, the worst that could happen is you could learn alot about Linux and that isnt bad. After you upgrade up (after backing up to a backup harddrive, etc), we can help you setup your video card and go from there...

---

