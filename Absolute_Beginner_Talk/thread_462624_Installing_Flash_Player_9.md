---
title: "Installing Flash Player 9"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Gummyman on 2007-06-02
[http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux")
I'm trying to follow the instructions for installing the beta... But I am completely and utterly lost, possibly because I don't have some of the needed files, but I don't know how to install those either, or what I'm missing for that matter :/

Thanks in advance.

---

### Post by deadgobby on 2007-06-02
try this
[https://help.ubuntu.com/community/FlashPlayerStandalone](https://help.ubuntu.com/community/FlashPlayerStandalone) Or this


Install the package flashplugin-nonfree

---

### Post by taurus on 2007-06-02
Try this, [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash).

---

### Post by Seisen on 2007-06-02
Its a lot easier to install Flash Player through synaptic or apt. 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Gummyman on 2007-06-02
> **Seisen said:**
> Its a lot easier to install Flash Player through synaptic or apt. 

```
sudo apt-get install flashplugin-nonfree
```
So I put that in synaptic? Apparently I'm even more clueless than I thought, because I don't think I even have synaptic... I suppose I did choose the right section though

Edit: Never mind... Figures, right after I post, I find it...

---

### Post by taurus on 2007-06-02
You can access synaptic through System -> Administration -> Synaptic Package Manager.  Then in the Search field, type in 

```
flashplugin-nonfree
```

---

### Post by bobplano on 2007-06-02
synaptic is under system>administration>synaptic package manager
that is a graphical way to install things so just search for flash player then look for flashplayer-nonfree
the command, you enter into the terminal, which is in applications>accessories>terminal
then just copy and paste (using right click). these paths are for ubuntu(gnome) and not kubuntu(kde) or xubuntu (xfce)

---

### Post by Gummyman on 2007-06-02
Two things:
1) Apparently I have less menus than you guys, because I don't have to go to this 'administration' menu, it's just System....
2) For some reason flashplugin-nonfree is not showing up

---

### Post by whistlerspa on 2007-06-02
Do you have Applications - Accessories-Terminal   ?

If so go open a terminal and then enter the command 

sudo apt-get install flashplugin-nonfree

there. (I am assuming that you're running Feisty)

---

### Post by Gummyman on 2007-06-02
I have Konsole, and it's under System

Here's what I've been getting (hence why I was confused)
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate


---

### Post by taurus on 2007-06-02
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Gummyman on 2007-06-02
Didn't see the link the the second page until now :/
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


---

### Post by taurus on 2007-06-02
Edit /etc/apt/sources.list

```
kdesu kate /etc/apt/sources.list
```
and add these two repos at the end of it.

```
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Save it and then run

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by Dougie187 on 2007-06-02
I have the same sources.list you have but i have the package. what happens if you type```
Sudo apt-get update
``` in your konsole?

Edit:
I guess 16000 more posts then me means your 16000 times faster. heh

---

### Post by Gummyman on 2007-06-02
@taurus
When typing > kdesu kate /etc/apt/sources.list into the console, I get> kdesu: cannot connect to X server

When directly trying to edit it, it just plain won't let me...
However, I was able to do the first run, but the second ("sudo aptitude install flashplugin-nonfree") came up with> Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up j2sdk1.4-doc (1.4.2.02-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing j2sdk  

@Dougie187
> -su: Sudo: command not found

---

### Post by taurus on 2007-06-02
Are you logged in as root?

It should be 

```
**[COLOR="Blue"]s[/COLOR]**udo apt-get update
```

---

### Post by Gummyman on 2007-06-02
I'm using root shell, and that command ran (sudo apt-get update).

What do I do from here now, exactly?

Edit: You know, I just realized, this might be helpful: I have x86-64 bit :/

---

### Post by Dougie187 on 2007-06-03
and your on kubuntu too right? I am just assuming from all the k things. I dont know if its radically different then gnome.. never used it.

---

### Post by Gummyman on 2007-06-03
Yes, I am running Kubuntu *points at the upper right corner of post*. Besides from the different programs (Konqueror as the default web/folder browser, and other differences)
Overall, I'm happy with the K :)

After looking up the open a file as root, I was able to follow the instructions given by taurus

So is that the end of that? Or is there yet another step hidden over the horizon?

---

### Post by Gummyman on 2007-06-03
Slight correction:
Whenever I type in:
```
sudo aptitude install flashplugin-nonfree
```
I get:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by ageilers on 2007-06-03
Maybe you want to try going into Kmenu > System > Adept Manager. Paste

```
flashplugin-nonfree
```

in the Search field. If you are running Feisty, it should return a result. Expand it by clicking the  ">", Clikc the Request Install button, click apply changes and you are all set. If you are running root console su or sudo will do you no good as you are the superuser.

---

### Post by Gummyman on 2007-06-03
It's not showing up :/

(I am running x86-64, but I know there are some flash versions that work...)

---

### Post by Gummyman on 2007-06-04
Well, I think I figured out why it doesn't seem to be working :/
Apparently my dad (who did the download of the iso file), as far as I can tell, picked the wrong one...

I was just too clueless to figure out what was going wrong...

I'm going to try Ubuntu, as it seems to have what I have (AMD 64 bit Athlon)...

Hopefully this time it will have more than one layer of menus, and thus let me follow instructions much clearer ;)

---

