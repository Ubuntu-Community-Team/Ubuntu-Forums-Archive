---
title: "Installing GNUCASH in ubuntu 7.10"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by cp1969 on 2007-11-23
Hi everybody, I am new to Linux, so bear with me.  Trying to kick the XP habit.

I want to install Gnucash to see if I can quit using MS Money.  If I can, then that will be one less reason to use XP that I have installed on this system with Ubuntu.

I click on the Applications tab, then find Gnucash in the right hand pane.  But when I click on the box to include or install it, I can't, and get a message to hit the Reload button.  There is no reload button that I see.  There is a refresh button, and when I hit it, some activity takes place but nothing changes.  I try to click the box and the cycle repeats.

???

Thanks.

---

### Post by Pumalite on 2007-11-23
Try Synaptic.
(i don't know if it is there, but I know it is the best way to install software.)

---

### Post by scrooge_74 on 2007-11-23
Last time i check it was there.  It is very simple to use, last time I sed (one year ago) I had a couple of bad habits from using Peachtree which made me stop using Gnucash, but for home use is very simple to use

---

### Post by cp1969 on 2007-11-23
I don't see it listed in the available applications.

Gnucash is listed there.  I thought all one had to do was click on it's box to include it in the list of installed applications.

---

### Post by cp1969 on 2007-11-23
My last post was a lie.  Not only is it listed, it is checked as being installed on my system.

WTF,O?

Is Synaptic the behind the scenes installer that is supposed to work when you check the box on an available application?

---

### Post by cp1969 on 2007-11-23
Bump.

This has got to be a simple problem than anyone with two brain cells rubbing together (leaves me out) can diagnose.  If not, I'm wondering how I go about getting any new applications other than those that came with ubuntu.

---

### Post by scrooge_74 on 2007-11-23
Take it easy, dont bump every other hour, people do have other things to do besides this forums. And Gnucash is not an app everybody uses so not everybody can help you.  In fact I know about it because I was looking to replace Peachtree as my accounting system (but since it runs under wineI am keeping it for the moment)

I don't have Ubuntu system I can check against at this moment to see in what repository it is listed.

If synaptic says it is already installed then it should be in your menus. If it does not appear in your menus, open a terminal and type gnucash to run it.

Maybe you need to log out and back in to refresh the menus so it gets listed.

If I am not mistaken (if I am please someone correct me) the apps you see in the add/remove are the standard ubuntu packages the rest are in the multiverse repositories which you need to enable.

You can also try from a terminal sudo apt-get install gnucash  to install it

---

### Post by Pumalite on 2007-11-23
gnucash-2.2.1

---

### Post by pigwot on 2007-12-06
The following packages have unmet dependencies:
  gnucash: Depends: libgoffice-0-4 (>= 0.4.2) but it is not installable or
                    libgoffice-gtk-0-4 (>= 0.4.2) but it is not installable
           Depends: libofx3 but it is not going to be installed
           Depends: guile-1.6-slib but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable

Any way to find out how to satisfy these unmet dependencies in 7.10 ?

---

### Post by Bothered on 2007-12-06
> **cp1969 said:**
> I don't see it listed in the available applications.

Gnucash is listed there.  I thought all one had to do was click on it's box to include it in the list of installed applications.

You need to have universe enabled in your /etc/apt/sources.list (can be configured from System->Administration->Software Sources - universe needs to be checked). In synaptic, gnucash can be installed by checking the box left of the "gnucash" package and clicking the "Apply" button. From the command line gnucash can be installed with the command:

```
sudo apt-get install gnucash
```

Gnucash should then appear on your applications menu under Applications->Office->Gnucash Finance Management. If it doesn't appear on the applications menu it can be launched with the command:

```
gnucash
```

If it is already installed, there could be a problem with your menu configuration. Try looking in ~/.local/share/applications/ and see if there is a file called Gnucash or similar in that directory. If there is, delete it and see if the menu item appears.

Are you using ubuntu/kubuntu/xubuntu/other?

---

### Post by Bothered on 2007-12-06
> **pigwot said:**
> The following packages have unmet dependencies:
  gnucash: Depends: libgoffice-0-4 (>= 0.4.2) but it is not installable or
                    libgoffice-gtk-0-4 (>= 0.4.2) but it is not installable
           Depends: libofx3 but it is not going to be installed
           Depends: guile-1.6-slib but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable

Any way to find out how to satisfy these unmet dependencies in 7.10 ?

Do you have main and universe enabled in your /etc/apt/sources.list? Try looking under System->Administration->Software Sources and see if they are checked.

---

### Post by confused1 on 2008-02-03
i would like to install the latest version of gnucash but i keep getting the 2.2.1. version 

so i uininstalled it-

if i start over and reinstall 2.2.1. is there a way to update it to the 2.2.3. version

---

### Post by Bothered on 2008-02-05
You can, but it's probably not worth it. You'd need to download the latest source (from [http://www.gnucash.org/](http://www.gnucash.org/)) and compile it yourself. You can then install it with checkinstall (see [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)).

---

### Post by jpaltan on 2008-02-27
> **pigwot said:**
> The following packages have unmet dependencies:
  gnucash: Depends: libgoffice-0-4 (>= 0.4.2) but it is not installable or
                    libgoffice-gtk-0-4 (>= 0.4.2) but it is not installable
           Depends: libofx3 but it is not going to be installed
           Depends: guile-1.6-slib but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable

Any way to find out how to satisfy these unmet dependencies in 7.10 ?

I was having the same problem and I was able to resolve it by going to system->software sources and checking all those boxes for universe and multiverse. after that I went to terminal and did sudo apt-get update and it took a couple minutes for everything to update. Then I did the gnucash install by sudo apt-get install gnucash and it worked. Have no clue why it worked or what was wrong in the first place. Only have been using ubuntu for about 2 hours so I don't even know what the commands actually mean. Hope it helps you.

---

