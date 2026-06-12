---
title: "What OS do you prefer?"
date: 2013-05-11
forum: Any Other OS
---

### Post by nsync on 2013-05-11
I am now using ubuntu 12.04 lts and it seems that ubuntu made me very satisfied, maybe because of its style and features

but can you suggest another OS that i can install to my other partition? im thinking now of Pear linux ? or maybe windows xp?

---

### Post by excollier on 2013-05-11
Try Linux Mint 13 KDE, based on Ubuntu / Kubuntu 12.04, but  different. Or very different is CrunchBang #!

---

### Post by iamkuriouspurpleoranj on 2013-05-11
Try Fedora or openSUSE because they will give you something quite different.

According to Mutkwear, openSUSE is a elite dsitro, which either means it's very good or that Mutkwear needs to engage more with the concept of proofreading.

I prefer Fedora but expect to be puzzled how to set up Flash etc.

---

### Post by xoomer.ap on 2013-05-11
If you choose to be advanced ubuntu user try to learn Debian. I think it is valuable to know it because Ubuntu, Mint are derivatives of it.

---

### Post by Hawk999 on 2013-05-11
> **iamkuriouspurpleoranj said:**
> 

I prefer Fedora but expect to be puzzled how to set up Flash etc.

I see this remark all the time when people talk about Fedora.
The answer however is as easy as this:

[http://www.fedoraforum.org/?view=fedora_setup](http://www.fedoraforum.org/?view=fedora_setup)

---

### Post by exploder on 2013-05-11
I am a big PCLinuxOS fan because it has worked so many times where other distros have failed me. I always have current applications and I never have to jump through hoops to have things working like they should. Plymouth always displays right and the bfs kernel is great. The PCLInuxOS Team really put a lot of thought and hard work into making PCLinuxOS.

---

### Post by mips on 2013-05-11
[img]http://www.gregdonner.org/workbench/images/wb_20.gif[/img]

---

### Post by iamkuriouspurpleoranj on 2013-05-11
> **Hawk999 said:**
> I see this remark all the time when people talk about Fedora.
The answer however is as easy as this:

[http://www.fedoraforum.org/?view=fedora_setup](http://www.fedoraforum.org/?view=fedora_setup)

Don't like encouraging the use of third party software like Easylife.

**How to install Flash on Fedora**

1. Visit [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

2. Select YUM package from dropdown

3. Save package

4. Change to your downloads directory, for example:
```
cd Downloads
```

5. Finally, type the following commands into the terminal

```
su -c 'rpm Uvh adobe-release.etc.etc.etc.rpm'

su -c 'yum update'

su -c 'yum install flash-plugin' (press "y" when prompted to accept Adobe's key)

su -c 'yum install bsd-games' (optional)
```


You can directly install the adobe package from the site via Yumex (and update and install flash-plugin) but I had problems with that for some reason this week, so I don't want to recommend that.

Not difficult but harder than a tickbox during installation.

---

### Post by pfeiffep on 2013-05-11
> **nsync said:**
> I am now using ubuntu 12.04 lts and it seems that ubuntu made me very satisfied, maybe because of its style and features

but can you suggest another OS that i can install to my other partition? im thinking now of Pear linux ? or maybe windows xp?
Since you like Ubuntu, then possibly install Saucy (Ubuntu 13.10) to keep up with changes in Ubuntu. This is a development version that I'm currently testing on a flash drive.
I've installed Linux Mint 14 also.

The decision should be based on your purpose of installing another OS.:)

---

### Post by kiyop on 2013-05-11
> **nsync said:**
> I am now using ubuntu 12.04 lts and it seems that ubuntu made me very satisfied, maybe because of its style and features
Write more concretely what you need.

FYI, [http://distrowatch.com/](http://distrowatch.com/)
[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)

---

### Post by ibjsb4 on 2013-05-11
Your here, why not try the Buntu flavors first?

Lubuntu
```
sudo apt-get install lxde
```

Xubuntu
```
sudo apt-get install xfce4
```

Classic
```
sudo apt-get install gnome-session-fallback
```

They can all be installed on your current Ubuntu install and you can choose which one to run at login by clicking on the login icon.

---

### Post by Hawk999 on 2013-05-11
> **iamkuriouspurpleoranj said:**
> Don't like encouraging the use of third party software like Easylife.

Because? 

Both Easylife and AutoTen have always worked fine for me. I never had any problem with them. But if you have different en better info on this I am happy to hear it.
Now it seems you are making a baseless assumption without any argument or explanation. 

Besides you claimed that:

> **iamkuriouspurpleoranj said:**
> 

I prefer Fedora **but expect to be puzzled how to set up Flash** etc.

Seems you are moving the goalposts. 

First you claim that you have to "expect to be puzzled how to set up Flash".
Then when I show that it is in fact very easy to do, you switch context and claim now to have a unspecified problem with Easylife.


That however is a personal preference and has nothing to so with being puzzled when installing  Flash.
Installing Flash on Fedora is a simple two click process. Nothing puzzling about it.

---

### Post by iamkuriouspurpleoranj on 2013-05-12
^I run Fedora and CentOS as main systems. I also know what it's like to be new and to find it confusing to look for things where they were in Ubuntu and not find them. The new user might think the Adobe package is Flash and wonder why it's still not working or why there are both YUM and rpm choices in the dropdown.

Third party software is inherently a security risk. It's nothing personal against Easylife. In addition, I'm a reformed slacker and my inner critic is turned off by concepts like "easy life". There are even some unnecessary packages in there, some related to the developer's home country Brazil.

I accept third party for libdvdcss2 and mscorefonts because there's no other way but then again I don't have either right now so you can live without them.

Don't attack me for trying to set a potential new Fedora user's expectations at the right level. Fedora is a great distribution but it can be frustrating for those who don't yet know the lay of the land. It also targets a more technically minded person than Ubuntu does and doesn't seek to woo the casual home user who just wants everything to work with as little effort as possible.

I sometimes wish Fedora had these things but like you say, it's not really difficult when you know how.

When you know how.

---

### Post by ibjsb4 on 2013-05-12
> **iamkuriouspurpleoranj said:**
> Third party software is inherently a security risk.

That must only apply to Fedora, nothing inherent about it in Ubuntu.  There's lots of good third party software out there, just look at [launchpad PPA]("https://help.launchpad.net/Packaging/PPA").

---

### Post by iamkuriouspurpleoranj on 2013-05-12
PPAs are installed at the user's discretion. They are maintained by the individual developers themselves and there is nothing intrinsically safe (or unsafe) about them. It's no safer than installing random freeware from Sourceforge, for example.

Ok, I understand the real risk with PPAs is dependency-related. However, they still represent an additional layer of trust. Why run a safe and secure operating system and then take unnecessary risks for an additional menu item or something in an existing piece of software? If Ubuntu does something wicked/stupid, I at least know who/what/where they are.

But back on topic, Fedora is a good choice for sitting alongside Ubuntu, as are openSUSE and Debian. Arch might be your cup of tea but experiment with it in VirtualBox first.

---

### Post by iamkuriouspurpleoranj on 2013-05-12
[http://askubuntu.com/a/52882](http://askubuntu.com/a/52882)

---

### Post by pootan on 2013-05-12
I'm a bit confused with the Fedora talk here and flash. I installed Fedora 18 last week and flash worked out of the box.

Edit: on second thought I may have enabled 3rd party repositories.

---

### Post by ibjsb4 on 2013-05-12
> **iamkuriouspurpleoranj said:**
> But back on topic

Thats funny :)

---

### Post by taidoka on 2013-05-12
Well I'm running Linux Mint 13 Cinnamon edition (3.2.0-kernel) with latest version of cinnamon running.
I like it but it's always the same: Linux is tweaking because it's rough around the edges.
It's not Mac OS X but it's configurable. And it's not 'blinky' like other OS are ;)

---

### Post by terry_gardener on 2013-05-12
you could try something something different like manjaro

---

