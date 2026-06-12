---
title: "Is there a functionality difference between GNOME and KDE?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by fireworld2406 on 2007-07-30
I was wondering if there is a major functionality difference between KDE and GNOME. I have both Kubuntu and the Ubuntu Feisty Fawn live CD, and I was wondering if there is any reason to use Kubuntu over Ubuntu in terms of functionality.

---

### Post by Rocket2DMn on 2007-07-30
It's really a matter of preference over the GUI interface.  You can install one and download ubuntu-desktop or kubuntu-desktop to try out GNOME and KDE.  GNOME is the typical install with Ubuntu, whereas Kubuntu has KDE instead.  However, they are not mutually exclusive to have installed, though you can only use one at any specific moment in time, of course.
Most people use GNOME but that doesn't necessarily make it better or more functional than KDE.  Xfce is another environment, hence Xubuntu.

---

### Post by oilchangeguy on 2007-07-30
> **fireworld2406 said:**
> I was wondering if there is a major functionality difference between KDE and GNOME. I have both Kubuntu and the Ubuntu Feisty Fawn live CD, and I was wondering if there is any reason to use Kubuntu over Ubuntu in terms of functionality.

it depends on what you like. kde looks like windows, whereas gnome looks like a mac. i've used kde on other linux distro's. but went with the default ubuntu setup (gnome) when i installed it. and have no problems with it. since kde and gnome are not windows, you still have to learn where everything is located.

---

### Post by silent1643 on 2007-07-30
> **fireworld2406 said:**
> I was wondering if there is a major functionality difference between KDE and GNOME. I have both Kubuntu and the Ubuntu Feisty Fawn live CD, and I was wondering if there is any reason to use Kubuntu over Ubuntu in terms of functionality.

you can try kde for yourself,
```
sudo apt-get install kde-core
```

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

and uninstall it if  you do not like 
```
sudo apt-get remove kde-core
```

---

### Post by fireworld2406 on 2007-07-31
Thank you for all of your advice. Unfortunately, I have dial-up and I believe the KDE files are quite large. Is there a way I can install the KDE files from the Kubuntu Live CD?

---

### Post by Rocket2DMn on 2007-07-31
Yes, the cd can act as a repository
```
sudo apt-cdrom add
``` from [http://ubuntuguide.org/wiki/Ubuntu:Feisty/Repositories#Adding_a_CD-ROM_or_DVD_repository](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Repositories#Adding_a_CD-ROM_or_DVD_repository)

---

### Post by aysiu on 2007-07-31
The Kubuntu live CD does not have the packages necessary to add KDE to an existing Ubuntu installation. It can only install *over* (i.e., replace) an existing Ubuntu installation.

In answer to your original question, KDE has some functionality that Gnome doesn't, but it's up to you whether you think that added functionality is important or not. Here are some examples:

* Konqueror allows you to preview images in the upload dialogue. Firefox does not. You could use Konqueror in Gnome, of course, but it'll be non-native, looking ugly and loading up a lot of extra libraries

* KDE allows you an easy way to have separate wallpapers for each desktop or to have a website be your desktop

* KDE allows you an easy way to have a Mac-like "universal toolbar."

* Konqueror has a "restore from trash" feature. In Gnome, if you accidentally delete something, you have to remember where the file used to be and then manually move it back there.

* In KDE, you can specify window settings per application.

* In KDE, you can make the entire toolbar transparent. In Gnome, the handles will still be filled for most themes.

Now, all that said, I now prefer Gnome to KDE. I've used both extensively, and I like the simplicity of Gnome. Things are organized the way I like them. To see what I'm talking about, just compare configuring removable drives in Gnome to doing the same in KDE. I also like how F2 renames only the name in Gnome. in KDE, F2 renames the entire file, including the extension.

There are lots of little things that are different. For more information, including screenshots, read this:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by Rocket2DMn on 2007-07-31
When I setup Ubuntu, I think KDE came installed, though I never use it.  Doesn't this mean the Ubuntu live CD should have the necessary packages for KDE (rather than using the Kubuntu cd)?

---

### Post by aysiu on 2007-07-31
> **Rocket2DMn said:**
> When I setup Ubuntu, I think KDE came installed, though I never use it.  Doesn't this mean the Ubuntu live CD should have the necessary packages for KDE (rather than using the Kubuntu cd)?
Did you have the DVD?

If you have only a CD, you will **never** get both KDE and Gnome. The Desktop CDs do not contain packages for either desktop environment, actually. If you want to use a CD to add KDE or Gnome, you'll need the KDE Alternate CD or Ubuntu Alternate CD, respectively.

Desktop CDs just have images of installations. They do not contain packages for everything they install. Thus, they cannot be used to **add** desktop environments (KDE or Gnome) to existing installations. They can only **replace** (i.e., erase) existing installations.

---

### Post by Rocket2DMn on 2007-07-31
I'm not even sure which I used, I'll check when I get home.  I thought I just used the LiveCD, but I'll have a look when I get home.  I certainly didn't use the alternate cd.

---

