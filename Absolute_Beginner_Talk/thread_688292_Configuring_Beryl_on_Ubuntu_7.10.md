---
title: "Configuring Beryl on Ubuntu 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-02-05
Hi guys!

First of all, thanks for the wealth of information you post here... my transition to Ubuntu has been excellent... until i met this Hicup!

So.. I was having a look at the following guide to use Beryl:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

However... things are not going to way it has been indicated in the guide... Once i modified the </etc/X11/xorg.conf>... the machine boots up in Low Graphics mode, and the following error is generated once i run glxinfo | grep vendor

Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: Couldn't find RGB GLX Visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".

... Anyone know what i might be doing wrong? Im running a Dell Inspiron 9300 running an ATI Raidon Mobility X300

Thanks!

---

### Post by lswest on 2008-02-05
well first off, Ubuntu 7.10 is Gutsy Gibbons, and the tutorial you were using was for Feisty Fawn (7.04), so which version are you using? because what's true for one isn't necessarily true for another.

*EDIT* might want to have a look at [this]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4781&st=0&sk=t&sd=a")

---

### Post by markbusu on 2008-02-05
Yup... i missed that... I am running on Ubuntu 7.10 Gutsy Gibbon...

Thanks for your quick reply

---

### Post by lswest on 2008-02-05
no problem, and i updated the last post with a link to an automated beryl install script, but i also saw these suggestions [this one]("http://ubuntuforums.org/showthread.php?t=583723") and [this]("http://ubuntuforums.org/showthread.php?p=4245717")  looks like compiz-fusion has very much replaced Beryl...what exactly did you want beryl for?

---

### Post by bumanie on 2008-02-05
Beryl is no longer a supported project. Beryl and compiz have been joined and are now one program called compizfusion. It would be much better for you to use that. You should be able to use it by system --> preferences --> enable desktop effects (something like that, I'm at work and not in front of my ubuntu machine).

---

### Post by lswest on 2008-02-05
if you want more desktop effects you can install the compiz-config settings manager with ```
sudo apt-get install compizconfig-settings-manager
``` and then you can access it under system-->preferences-->advanced desktop effects

---

### Post by markbusu on 2008-02-05
Thanks for the links!!

Well i dont really "need it" i just looks sweet :) and wanted to give it a try... However Compiz Fusion looks by far better!

In the mean time i have managed to restore XORG and got my display once again... I am going to try compiz-fusion now... using one of the links you provided:

[http://ubuntuforums.org/showthread.php?t=660966&highlight=compiz](http://ubuntuforums.org/showthread.php?t=660966&highlight=compiz)

Now Let us pray this one goes fine :)

Cheerz!

---

### Post by steveneddy on 2008-02-05
> **bumanie said:**
> Beryl is no longer a supported project. Beryl and compiz have been joined and are now one program called compizfusion. It would be much better for you to use that. You should be able to use it by system --> preferences --> enable desktop effects (something like that, I'm at work and not in front of my ubuntu machine).

Agreed.

Beryl was great in it's time, but Compiz-Fusion is where the Ubuntu/Linux eye candy is at.

Just get your video card set up correctly and CF should run fine.

---

### Post by markbusu on 2008-02-05
Hold on... so Compiz-fusion is included in Gipsy Gibbon... all i need to do is run the command 

sudo apt-get install compizconfig-settings-manager

On a side Note... SUDO command is performing impersonification of the Root User?

Thanks!

---

### Post by lswest on 2008-02-05
sudo=super user do, which basically means you're running the command that follows with root permissions^^  and yes, compiz-fusion is installed by default, the install command i posted just installs another manager which has some extra customizable effects that you can use.  Be sure to install the radeon driver for your ATI card before trying to enable deskop effects by going to system-->preferences-->appearence  then the visual effects tab, and either "standard" or "custom" should be chosen (custom will only be visible if you installed ccsm before)

---

### Post by markbusu on 2008-02-05
Thanks for the Clarification...

One last thing.. and sorry for being so thick about this... but i just started...

When you refer to the radeon driver for my ATI card... are you refering for the restricted drivers (XORG) by default installation... or some other open source Drivers?

Thanks!

---

### Post by lswest on 2008-02-05
xorg is just a configuration file for your graphical user interface (GUI) but yes, the radeon driver is the restricted driver.  it's restricted because it's a propriety driver (e.g. not released under the GNU open source license, and is licensed to ATI)

and no problem, took me a while to understand all the nuances too^^ always happy to help.  And, well, i've been using linux for a while now :P (about 3-4 years), but once you start using it, you get pretty comfortable with all the terms and commands.  Glad we could help.

---

