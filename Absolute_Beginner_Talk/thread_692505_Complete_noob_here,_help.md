---
title: "Complete noob here, help"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by 500sd on 2008-02-09
Well, I just installed Ubuntu 7.10 dual booting on xp, and the only reason why I installed Ubunutu is because of Beryl, and various theming programs. I need help on how to install beryl...and wine or some program that allows windows apps to be used on linux. 

-500sd

---

### Post by bwhite82 on 2008-02-09
Welcome to Ubuntu! Might I suggest that you peruse the extensive Wiki?

[http://help.ubuntu.com/community](http://help.ubuntu.com/community)

Here is for compiz-fusion (beryl and compiz have merged, beryl is no longer):

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Here is for Wine:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

If you have any questions after you have followed the instructions in the above links, I'd be happy to oblige.

-Cheers

---

### Post by 500sd on 2008-02-09
Lol first step and i'm already stuck :\ 
It says run sudo apt-get update 
but where do i run that in?

---

### Post by bwhite82 on 2008-02-09
Applications>Accessories>Terminal

Edit: BTW, the first step is adding software repositories, in which a link is giving showing you how to do it.

---

### Post by bwhite82 on 2008-02-09
Advice: I would spend some time reading the wiki fully before you delve into setting up CompizFusion and Wine. It will show you linux basics which will save you a lot of headaches in the future. The link I provided you is the community documentation, you may also want to check out the Official documentation:

[http://help.ubuntu.com](http://help.ubuntu.com)

Reading up on documentation is big in linux, folks spend a lot of time creating it for the sole purpose of helping people out. I've been using linux for many years now, and I am still constantly reading.

---

### Post by overdrank on 2008-02-09
> **Soldierboy said:**
> Advice: I would spend some time reading the wiki fully before you delve into setting up CompizFusion and Wine. It will show you linux basics which will save you a lot of headaches in the future. The link I provided you is the community documentation, you may also want to check out the Official documentation:

[http://help.ubuntu.com](http://help.ubuntu.com)

Reading up on documentation is big in linux, folks spend a lot of time creating it for the sole purpose of helping people out. I've been using linux for many years now, and I am still constantly reading.

+1 :KS

HI and welcome 500sd:)

---

### Post by 500sd on 2008-02-09
Hmm I'm still confused on how to install programs...I just don't get it :(

---

### Post by overdrank on 2008-02-09
> **500sd said:**
> Hmm I'm still confused on how to install programs...I just don't get it :(

HI and what are you trying to install?
 This is a good link also
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by happysmileman on 2008-02-09
> **500sd said:**
> Hmm I'm still confused on how to install programs...I just don't get it :(

Most programs are literally just Going into "Add/remove programs" in the menu, then installing them from there, then all updates will be handled by Ubuntu, so it makes it easier in the long run.

But compiz-fusion (the groovy desktop effects) and Wine require some setting up to do, but you only have to do it when you first install them, all updates will be as easy as other software thankfully

---

### Post by 500sd on 2008-02-09
Yea i'm just trying to get Wine and compiz-fusion. And various programs to run through wine.

---

### Post by happysmileman on 2008-02-09
[This]("http://www.winehq.org/site/download-deb") is how the Wine website describes it, doesn't look very n00b friendly, but to summarize, you open up a terminal (Applications>Accessories>Terminal), then type the following four lines, making sure to press enter after each line, it should ask you for your password after the first line:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

And the "-O-" on first line and "-O" on second are capital letter 'o's, not zeroes, and they have to be capital letters.

Post any errors you encounter here, or if you need it explained more.

---

### Post by 500sd on 2008-02-09
It won't let me type my password for some reason...i copy pasted that into terminal, than it asked for my pass but i couldn't type anything

---

### Post by happysmileman on 2008-02-09
> **500sd said:**
> It won't let me type my password for some reason...i copy pasted that into terminal, than it asked for my pass but i couldn't type anything

Your password won't actually show up (stops people reading it over your shoulder I suppose), it is actually being typed in, you just can't see it, so type it in and press enter, that should work.

(My ex-girlfriend had the exact problem first time she had to use terminal :P )

---

### Post by scorp123 on 2008-02-09
> **500sd said:**
> than it asked for my pass but i couldn't type anything Passwords are never ever echoed back :)  Forget about the BS you see in movies where you get stars or some other BS feedback when you type a password.

Just do as people tell you ... type your password and hit the "Enter" key. :)

---

### Post by wigglydiggly on 2008-02-09
Welcome to Linux

---

### Post by 500sd on 2008-02-09
Thanks for the help so far guys, I think I got Wine working. Theres Wine config in the "Other" section of my applications menu. So any help on compiz-fusion?

---

### Post by rainwalker on 2008-02-09
If you're on the latest version of Ubuntu, version 7.10 named "Gutsy Gibbon", compiz is installed by default. You can check by going to System > Administration > System Monitor and looking under the "System" tab.
If you are running Gutsy, then compiz is already installed and you can adjust the settings under System > Preferences > Appearance under the "Visual effects" tab. To get even more options, go to System > Administration > Synaptic Package Manager and install the package called "compizconfig-settings-manager". It will be under System > Preferences > Advanced Desktop Effects Settings

---

### Post by 500sd on 2008-02-10
Perfect thanks sooo much!

---

### Post by rainwalker on 2008-02-10
If you want to check what enables a certain plugin, look under the "Actions" tab in that plugin's settings. There you can view/change the settings for activating them
button1 = left mouse button
button2 = the scroll wheel, or if you can't click with it then it's the right mouse button
button3 = the right mouse button if you are able to click with the scroll wheel
super = that's the key with the windows logo on it

---

### Post by 500sd on 2008-02-10
Also, how would one get themes ?

---

### Post by ispy on 2008-02-10
[www.gnome-look.org](www.gnome-look.org)

should suit your needs. I personally recommend the Mac4Lin project. google it, but it requires terminal knowledge and stuff, not for absolute beginners.

---

### Post by rainwalker on 2008-02-10
[www.gnome-look.org](www.gnome-look.org)

Over on the left side are the categories, here are the important ones:
GTK - These are themes for all of the controls (buttons, colors, etc.), don't bother with the GTK 1 section. You install them though System > Preferences > Appearance
Metacity - These are window border themes (unless you use Emerald), install through System > Preferences > Appearance
Beryl - These are Emerald themes, if you use the Emerald window decorator (which you don't, unless you install it)
GDM Themes - These are login screen themes, install through System > Administration > Login Window
Screenlets - These are the equivalent of OS X's widgets

---

### Post by yizuman on 2008-02-10
I got the wine installed, so how do I find it? I used the instructions on this thread.

also while it was installing, I got one particular error

W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7

How do I fix that?

Thanks

---

### Post by scorp123 on 2008-02-10
> **yizuman said:**
>  W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7

How do I fix that?  You didn't install his GPG key, so your package manager is warning you it doesn't trust that repository. As for how to fix that:

Entering the repos's address into a browser ... 
[http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) 

... and we get to Hendrik's web page where he gives instructions on how to add his GPG key:
[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

Quote from there: >  [U][B]Step 1: Add the GPG key
[/B][/U]
Packages is this repository are GPG authenticated. The key that is being used for signing the packages is **F854AFD7**. You can enter this key into the APT trusted keys database with the following command:
```
wget http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg -O- | sudo apt-key add -
``` 

---

