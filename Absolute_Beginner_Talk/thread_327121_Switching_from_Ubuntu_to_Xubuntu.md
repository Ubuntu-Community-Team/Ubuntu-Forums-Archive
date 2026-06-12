---
title: "Switching from Ubuntu to Xubuntu?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-28
Well, now that I've been toying around with Xubuntu it's become obvious that no matter how fast your computer is Xfce is quicker than GNOME. So I'm thinking of making the switch, but since reinstalling isn't an option I would like to just change the things within Ubuntu that need to be changed.

1) How do I change the loading screen in the beginning from Ubuntu to Xubuntu?

2) How do I make the two things I need (nm-applet and gnome-power-manager) boot up automatically?

3) How do I edit the applications menu? I've noticed that the GNOME menu doesn't effect the Xfce menu, and I would like to learn how to edit Xfce's.

---

### Post by jpoRS on 2006-12-28
Sorry, Clicked the wrong button.

---

### Post by Tazix on 2006-12-28
> **Pobega said:**
> Well, now that I've been toying around with Xubuntu it's become obvious that no matter how fast your computer is Xfce is quicker than GNOME. So I'm thinking of making the switch, but since reinstalling isn't an option I would like to just change the things within Ubuntu that need to be changed.

1) How do I change the loading screen in the beginning from Ubuntu to Xubuntu?

2) How do I make the two things I need (nm-applet and gnome-power-manager) boot up automatically?

3) How do I edit the applications menu? I've noticed that the GNOME menu doesn't effect the Xfce menu, and I would like to learn how to edit Xfce's.

I think it would be easier if you download the Xubuntu ISO, and install it from scratch (erasing Ubuntu). That way you have a clean install and no gnome / ubuntu specific apps confusing you... like xfce has it's own menu editor, etc.

Anyway... to answer your question... everything for XFCE can be found in the Settings Manager... including the menu editor (At least on the pure Xubuntu install / ISO).  Also... there's an area in Xubuntu's menu that let's you "autostart applications"  That's done upon login. (Applications -> Settings -> Autostarted Applications)

If you need something autostarted without loging in... then you need to create / edit the appropriate init script... 

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Look at "Installing custom init-scripts" section.

-Taz

---

### Post by Jorge32 on 2006-12-28
There's a way of changin to xubuntu without reinstalling it. Just download the Xubuntu desktop from the synaptic package manager and install it. The next time the loading screen will be Xubuntu's and you will keep the applications from Ubuntu. Even at the login screen there's an option of starting with GNOME or with XFCE.
Is that what you were looking for?

---

### Post by Pobega on 2006-12-28
Would [this page](http://www.psychocats.net/ubuntu/purexfce) work in switching my system to Xubuntu, discluding gnome-power-manager and nm-applet (Seeing as I use both of those)?

---

### Post by Jorge32 on 2006-12-28
why don't you try removing eveyrthing and then downloading from the synaptic gnome power manager and nm applet?

---

### Post by Pobega on 2006-12-28
Well I basically plan on not removing the programs I use, but I'm just posting here to make sure doing that won't mess anything up within my system.

---

### Post by tommytom on 2006-12-28
I just recently installed Xubuntu from Synaptic alongside Gnome and it led to some strange results. Firstly my menu bar was full of programs which where specific to Kubuntu (also installed earlier but with out any cross over problems) this is easy to fix as you can just edit the menu. What was slightly more annoying was the confusion of gtk themes between Gnome and XFCE. Gdesklets for example start up under both desktops and apps like Gkrellm started up in XFCE, although it was not in the start up programs for XFCE only Gnome. If somebody can help you avoid these issues then by all means install XFCE, it's great. Otherwise proceed with caution as my system was sorted  prior to my messing about and now needs me to spend time fixing it :(

---

### Post by Pobega on 2006-12-28
Mmm, I see. Well, I'm using a System76 laptop and I'd switch to Xubuntu completely but I'm not sure if the installed drivers are 100% supported there (For example, I've got no idea where I got nm-applet from. I'm guessing System76). So it would be most benefitial for me to just swap my current install over from Ubuntu to Xubuntu, especially considering that I have all of my music on this HDD, and that would be annoying to back up.

Basically I just want to know besides gnome-terminal (Because I like GNOME's terminal) and gnome-power-manager what should I keep as to not cripple anything in the Ubuntu installation

---

### Post by K.Mandla on 2006-12-28
> **Pobega said:**
> Well, now that I've been toying around with Xubuntu it's become obvious that no matter how fast your computer is Xfce is quicker than GNOME. So I'm thinking of making the switch, but since reinstalling isn't an option I would like to just change the things within Ubuntu that need to be changed.

1) How do I change the loading screen in the beginning from Ubuntu to Xubuntu?

2) How do I make the two things I need (nm-applet and gnome-power-manager) boot up automatically?

3) How do I edit the applications menu? I've noticed that the GNOME menu doesn't effect the Xfce menu, and I would like to learn how to edit Xfce's.
1. Do you mean the boot splash screen, or the brown Ubuntu bar that appears after login?

2. Try this [nm-applet howto]("http://ubuntuforums.org/showthread.php?t=239178"), and there is a battery and power monitor available in Xubuntu. 

3. There is a Menu Editor under Applications > Settings, but the general consensus is ... that it generally stinks. On the whole, the Xubuntu and Ubuntu menus should mirror one another when new programs are installed. If not, you might have to tinker with the editor.

---

### Post by K.Mandla on 2006-12-28
> **Pobega said:**
> Mmm, I see. Well, I'm using a System76 laptop and I'd switch to Xubuntu completely but I'm not sure if the installed drivers are 100% supported there (For example, I've got no idea where I got nm-applet from. I'm guessing System76). 
If it works under Ubuntu, it should work under Xubuntu. You could ask under the [System76 Support area]("http://ubuntuforums.org/forumdisplay.php?f=158"), just to be safe.

---

### Post by Pobega on 2006-12-28
Thank you, that How-To was very informative. But what I would still like to know is would switching to a full Xfce system on an Ubuntu install mess up the install in any way?

**Edit:** And by that I mean using the [PureXfce](http://www.psychocats.net/ubuntu/purexfce) way.

**Edit2:** > 1. Do you mean the boot splash screen, or the brown Ubuntu bar that appears after login?
I mean the boot splash screen.

---

### Post by Tazix on 2006-12-29
I still think you would save yourself a lot of frustration by downloading the Xubuntu ISO and doing a fresh / pure install.  There's just too much garbage left over when you apt-get install "another-desktop" then apt-get remove "old-desktop".

And yes... doing that pure xfce thing "sudo aptitude remove 'old-desktop' ***COULD*** mess something up.  There are no guarantees that a script can cover everything.  I trust adding / removing extra desktops about as much as I trust a "Winblows upgrade install". :p  That long command to paste to "remove ubuntu" could affect something you are using in both environments.

Heck... just boot the live CD version to see if you can do what you want without affecting your Ubuntu install.  That's the great thing about live CDs.  Of course, it boots slow and programs launch slow... but you can get a good idea of what you want to do before an install.

[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)

-Taz

---

### Post by ssergeje on 2006-12-29
> **Pobega said:**
> Mmm, I see. Well, I'm using a System76 laptop and I'd switch to Xubuntu completely but I'm not sure if the installed drivers are 100% supported there 

I have all of my music on this HDD, and that would be annoying to back up.

1) The drivers are in the kernel. It is the same in all dereviates of Ubuntu (Ku & Xu).
If everything is working under Ubuntu it will be working under Xubuntu

2) Next time make a separate partition for /home, and installing new OS from CD would be like 1-2-3 :cool: 

BTW I used to use Xubuntu on Ubuntu.
Do 
```
sudo apt-get install xubuntu-desktop
```
This will install xubuntu, will replace the splash screen etc
Then you can clean up the XFCE menu from Gnome programs with menu editor
Can't help with network manager, haven't been there, haven't done that :-#

**EDIT:**
The link you have could make the trick, since it removes Gnome-desktop packages BUT I see that there you supposed to have XFCE ***already*** installed. If you dont have it, try the command given there (*sudo apt-get remove .....*) and then type
```
sudo apt-get install xubuntu-desktop
```

---

### Post by redDEADresolve on 2006-12-29
Xubuntu is a great choice if you like it. Best bet is to do a clean install. All your system76 hardware will work on Xubuntu just like Ubuntu. Kernel and drivers are the same, window manager is the only thing that changing. So there no real difference in terms of hardware usability. My system worked the sameon a clean Kubuntu as a clean Ubuntu.

Back Up and Reinstall.

---

