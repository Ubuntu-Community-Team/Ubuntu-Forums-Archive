---
title: "Two and a half cheers for Ubuntu. Should I stay or go?"
date: 2012-10-17
forum: Any Other OS
---

### Post by the big e on 2012-10-17
I like Ubuntu most of the time, but I am still not sure whether the grass is greener on the other side of some other fence when I feel frustrated by some things.

Things I like:
It's Linux.
It's reliable.
Most software I need is in the handy one-click install Software Center. Will any other distro have such a comprehensive and easy software installing process?
I like the Classic interface.
Installing was easy. Will it be easy if I picked another distro?
Ubuntu has a good website and forums. I look up some other distros on the web and the sites are rough around the edges or not oriented to the questions people like me might have.

Things I don't like:
I don't like the Unity interface and I have to figure out how to revert to the old one whenever there is a version upgrade
Extremely cluttered font menus, with too many foreign language fonts I don't need
Scribus crashes frequently. (Is that Ubuntu's fault or Scribus's?)
The fonts I have don't match the ones other people have (usually Microsoft) so there is a lot of font-defaulting when I send or receive files by email, post resumes, etc.
Not sure I like the default coloring of the desktop.
Can't watch DVDs or synch my ipod without going to my Windows boot.
Short battery life (on a laptop). Not sure if this is due to old battery or whether there is a software issue due to lack of hardware-specific battery-control software.

Any ideas about whether some other product has something better or whether I am better off tweaking what I already have, will be appreciated.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
here are your windows fonts
```
sudo apt-get install ttf-mscorefonts-installer
```dvds ([reference]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"))
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```[http://www.ubuntuupdates.org/ppa/medibuntu_non_free](http://www.ubuntuupdates.org/ppa/medibuntu_non_free) - medibuntu ppa


don't like unity:
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/) - xubuntu ([changeing the default panels](http://ubuntuforums.org/showthread.php?t=2065340))
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/) - lubuntu
[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/) - kubuntu
[http://mate-desktop.org/install/](http://mate-desktop.org/install/) - mate desktop
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable) - cinnamon desktop
[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta?action=show&redirect=UbuntuGNOME%2FReleaseNotes]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta?action=show&redirect=UbuntuGNOME%2FReleaseNotes") - gnome ubuntu


as for your battery, try a newer kernel
[http://ubuntuforums.org/showthread.php?t=2071903](http://ubuntuforums.org/showthread.php?t=2071903) - for 12.10 (the attached script should be universal, but was only tested on 12.10)

---

### Post by 2F4U on 2012-10-18
> Installing was easy. Will it be easy if I picked another distro?

Strongly depends on the distro, but Ubuntu is among the easiest to install. On the other end would be distros such as Archlinux, where you have to do everything yourself.

> Not sure I like the default coloring of the desktop.

Install other themes. If you google, you will find plenty of alternatives.

> Short battery life (on a laptop). Not sure if this is due to old battery  or whether there is a software issue due to lack of hardware-specific  battery-control software.

How old is it and what make and model is the laptop. Most batteries are aging rapidly and don't have their initial capacity after only a year.

---

### Post by the big e on 2012-10-21
pqwoerituytrueiwoq, I tried your command for installing Microsoft fonts, and it went a little wrong. It gave me a Eula, but when I tried to click "accept" it somehow read me as having hit "decline" and refused to put them in. Running the command again didn't work. And now I get an "internal error" warning message now and then and my font menu looks the same.

So I don't know what I'm doing wrong or how to recover from it.

I'm not blaming you for anything. Just to say bushwhacking through command line is not something I am used to doing, so forgive me if I grouse a little.

---

### Post by OrangeCrate on 2012-10-21
<Inadvertent double post, sorry.>

---

### Post by OrangeCrate on 2012-10-21
> **the big e said:**
> I like Ubuntu most of the time, but I am still not sure whether the grass is greener on the other side of some other fence when I feel frustrated by some things.

<snip>

**Any ideas about whether some other product has something better or whether I am better off tweaking what I already have, will be appreciated.**

To offer an honest answer to your question, since you appear to be having fair to poor results with Linux/Ubuntu, stick with windows. I would think Windows 7 is a good choice for you. In addition to the typical malware/antivirus solutions, you can make it pretty secure by following these guidelines:

[http://www.unixwiz.net/techtips/win7-limited-user.html](http://www.unixwiz.net/techtips/win7-limited-user.html)

---

### Post by offgridguy on 2012-10-21
>   Ubuntu has a good website and forums. I look up some other distros on  the web and the sites are rough around the edges or not oriented to the  questions people like me might have.I recently checked out the linux forum, and I much prefer ubuntu as well.

---

### Post by the big e on 2012-10-22
Orange Crate, you misread me. I have exactly seven problems dealing with Ubuntu, as described above. I have an infinite number of problems dealing with Windows, which I only go near when I absolutely need some piece of commercial software.

Ubuntu opened the world of Linux to me, and the only question is, did I pick the best form of Linux, or is there something better?

---

### Post by Linuxisfast on 2012-10-22
For battery life try Jupiter applet from their ppa at [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

### Post by bra|10n on 2012-10-22
> **the big e said:**
> I like Ubuntu most of the time, but I am still not sure whether the grass is greener on the other side of some other fence when I feel frustrated by some things.

The grass is always greener on the other side of the fence, until you go over the fence of course...  :popcorn:

Let's assume though that you'll be staying a while longer. It would help to know what hardware you are using. Knowing this will allow others here using the same or similar setups to highlight some pitfalls or things to watch out for, as well as help make a start on diagnosing short battery life.

As for your issue list, let's see...

Have you looked at the Gnome desktop? It's in the standard Ubuntu repositories and quite a few here on these forums use/prefer and support it. Worth checking it out...
The font menus issue is an odd one. Most people set up their chosen font and then pay little attention to font options. As pqwoerituytrueiwoq posted, Microsoft fonts are what your looking for, however your install didn't work out too well. Try the following to uninstall what you have and try again with,
```
sudo apt-get purge ttf-mscorefonts-installer
```and then,
```
 sudo apt-get install ttf-mscorefonts-installer
```Use the Tab key to select ok for accepting the EULA this time ;)
While we are talking fonts, many of the Thai and Indic fonts can be removed from your system. I'm not on Unity, but using a friendly Software Centre? GUI for this is probably best.

> Scribus crashes frequently...Try starting it from a terminal, and look for any errors messages that might highlight any problems.

Changing wallpapers, themes etc is a fairly simple process. There are many posts here on the forum that go through the hows and whats...

Can't watch DVD's?
Have you got ubuntu-restricted-extras installed? This meta-package contains many of the non-free media codecs/formats for most situations. Let us know...

Battery life will depend on your hardware, the state of your hardware, your install and feature set. This of course will be the same on any distro you use. Perhaps Windows has a specific set of drivers supporting your hardware while your Ubuntu install is currently using a generic set. But let's cross that fence when we get to it...

HTH

---

### Post by bailout on 2012-10-22
> **the big e said:**
> 
Extremely cluttered font menus, with too many foreign language fonts I don't need


This is very annoying. Having the different language fonts available is obviously good but installing them all by default is not. The installer should just install the ones applicable to your locale.

The font config in KDE allows you to disable any fonts you don't want and is one of the first things I do on a new install. Unfortunately I don't think gnome has the same facility. You may be able to uninstall some through Synaptic and then delete more directly.

---

### Post by lykwydchykyn on 2012-10-22
Nearly every problem you describe sounds solvable to me, perhaps with the exception of Scribus (I've only used it a handful of times myself, and it never seemed that stable to me).

You could spend a lot of time jumping around from distro to distro trying to find one that suits your needs, but honestly it's better in the long run to learn how to tweak one distro to do what you want.

I'm not saying other distros aren't worth a try, or that your distro of choice should be Ubuntu; but if you're expecting to find a distro that fits your needs like a glove from hardware support to color scheme, you'll be searching for the rest of your life.

---

### Post by Psyael on 2012-10-22
I've felt a bit like our OP in the past.

I'd consider trying another version of Ubuntu with a different window manager if you plan to ignore Unity permanently. I like GNOME Shell with extensions and menus (adding Docky and Cardapio with it's menu extension makes the current GNOME far more enjoyable in my experience), and in the past went to Debian.

The thing is, too much software in development is made for or around Ubuntu. If you want the latest open source projects, the latest WINE builds, and so on; you're probably better off with Ubuntu or maybe Mint. Using Debian I found myself having to mix in a lot of Ubuntu packages and earn the scorn of their message boards. ;)

I say, try Ubuntu GNOME and Mint with Cinnamon. Both of these are distros with up to date and modern window managers, though GNOME really does take the Browser approach where you need to load it up with your personalized extensions before you'll be truly happy.

---

