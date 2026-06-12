---
title: "Installing Ubuntu 7.10 on a Dell D630"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Surf121 on 2007-10-25
I have recently decided to give Linux a try on my dell latitude d630.
I was able to install version 7.10 in a partition automatically created; therefore, now I can double boot with windows XP.
Everything seems to be working fine except two things as of now:
-I have no sound
-I can't enable visual effects

I'm a complete newby to Linux and Ubuntu therefore please explain in detail.
I allready tried some methods found in other posts but have no idea what they are talking about and they seem to be for experts.

---

### Post by Afkpuz on 2007-10-25
Do you have an ati video card?

---

### Post by JoshF on 2007-10-25
To get sound working on mine I installed linux-backports-modules-generic.  That worked for me.

Also to get compiz working edit /etc/xdg/compiz/compiz-manager and add the following line to the end:
```
SKIP_CHECKS=yes
```

All of the effects don't work with that video card so things might crash in certain situations.

---

### Post by Surf121 on 2007-10-25
> **Afkpuz said:**
> Do you have an ati video card?

I have an Intel 965 Express Chipset "Intel Integrated Graphics Media Accelerator X3100"

---

### Post by Surf121 on 2007-10-25
> **JoshF said:**
> To get sound working on mine I installed linux-backports-modules-generic.  That worked for me.

Also to get compiz working edit /etc/xdg/compiz/compiz-manager and add the following line to the end:
```
SKIP_CHECKS=yes
```

All of the effects don't work with that video card so things might crash in certain situations.

Thanks I will try it later today, but first,how do I edit /etc/xdg/compiz/compiz-manager?
Do you believe all effects will eventually work?

---

### Post by JoshF on 2007-10-25
To edit that file:
```
sudo nano -w /etc/xdg/compiz/compiz-manager
```
Then add that line to the end:
```
SKIP_CHECKS=yes
```
The press crtl-x to save and exit.  Your compiz should work now.

There are a couple thinks that I hope get working with that video card in the future, including better dual monitor support.  But I don't know if or when anything will get fixed.

---

### Post by Surf121 on 2007-10-25
Anyone know about the sound issue?

---

### Post by bpickel on 2007-10-25
On my 630. I had to go and download and compile alsa from source. Follow this documentation and you should be OK.

 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


Also here is a thread that may help if you have additional after you actually have sound.

[http://ubuntuforums.org/showthread.php?t=570890&highlight=sound](http://ubuntuforums.org/showthread.php?t=570890&highlight=sound)

Hope this helps. Let me know if you have other trouble . I may have a few answers (I have the same Lappy) !

---

### Post by Surf121 on 2007-10-25
I get
configure: error: this packages requires a curses library

I then install it with this command from a terminal: 
sudo apt-get install libncurses5-dev

but get the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libncurses5-dev

Any help?

Seems like libncurses5 is allready installed

---

### Post by Surf121 on 2007-10-26
Anyone know??

---

### Post by JoshF on 2007-10-26
To get my sound working I installed linux-backports-modules-generic.

Open up you Synaptic Package Manager and search for it.  Then install it.  Then reboot.  Worked for me.

---

### Post by Dark Savant0 on 2007-10-31
I actually fixed all these problems in my own D630 Gutsy installs pretty simply.

For sound, you may need to check the actual kernel you are using. On UbuntuStudio and Ubuntu, it auto-installed the realtime kernel and thus the package to install is actually "linux-backports-modules-rt". I do believe it is in Universe. No nasty side-effects of make install (and one should do checkinstall instead, so that aptitude takes care of dependencies later on). Remember to install the right version for your kernel.

For Compiz Effects, no need to hack anything. Just do the following:

- sudo aptitude install xserver-xgl compiz-config-settings-manager
- Restart Computer once it notifies you of the XGL change
- Menu -->System -->Preferences --> Appearance
- Desktop Effects tab, check "Custom" and let it configure it for you. Then you can go into configure it and add/remove the effects you like.

If you want advanced effects regarding the Window Manager, you can replace GTK+ with Emerald (should be in the repos). Just be sure to install some themes with emerald because I don't think they are installed by default.

---

### Post by Surf121 on 2007-11-01
Thanks to bpickel I now have sound!
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 

The compiz fusion problem was fixed via the skip_check = yes 
or via 
- sudo aptitude install xserver-xgl compiz-config-settings-manager

Both work!

Now I don't see the option in desktop effects tab to check "Custom" and let it configure it for me, that Dark Savant0 is talking about. I don't see it!

Also once beryl and emerald is up and running mysteriously the close, minimize and maximize buttons in the window bar have dissapeared.

Anyone know why? Any solution to this problem?

---

### Post by thirunavukkarasu on 2007-11-01
pls give a try for this
apt-get install ncurses

Also, my suggesstion is to use the Synaptic package manager; when u don't know the exact package name.

Rgds,
Thiru.S

---

### Post by Kleenux on 2007-11-08
> **Surf121 said:**
> Thanks to bpickel I now have sound!
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 

Yes, this is the solution, as the "simple install of ... generics" simply doesn't work for me
[I did a fresh Ubuntu 7.10 install Server, then get Desktop, updates, added lines in /etc/apt/sources.list etc...]

Another thing: the Dell touch pad and the mouse buttons are very "touchy". Dell implemented a "smart" way to guess if the user clicks or no with a simple touch of the key... this is really awkward! In windows there is a Dell manager stuff to stop/regulate this behaviour.

Is there a similar Dell touch pad manager for Linux Ubuntu? Thanks

---

