---
title: "Customizing Ubuntu"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Sanchopinky on 2007-03-16
On windows I used to have windowblinds and that was alright, but looking at some vista screenshots and having used OS X at school.. I was wondering.. are there anyways besides beryl I can customize ubuntu? Like add widgets, rss feeds to desktop, and stuff like that? 

If you guys could redirect me in the right direction it would be most appreciated.

---

### Post by qpwoeiruty on 2007-03-16
For widgets, [gDesklets](http://www.gdesklets.de/) is nice...

---

### Post by Sanchopinky on 2007-03-16
I downloaded it.. took a look at the installation guide.. and ... how do I install it? 

My eyes hurt just from looking at it.. looks so complicated..

---

### Post by qpwoeiruty on 2007-03-16
Open up a terminal and type this in:
```
sudo apt-get install gdesklets gdesklets-data
```

You may need to add the universe and/or multiverse repositories if it's not found. You can most easily do this by opening Synaptic (System/Administration/Synaptic Package Manager) and checking the box in the repositories menu item.

---

### Post by zanglang on 2007-03-16
For the easy stuff you can add simple 'applets' to your panel by right-clicking and select "Add to Panel". And then there's Themes, Icons, Fonts, Screensaver, change your preferred applications.

For more advanced stuff you have conky and gdesklets:
[http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky)
(Didn't find a tutorial for gdesklets, but just install it, run it and try to play around with it. It's hard to mess up.)

Looking at the monthly desktop thread is good inspiration too ;)
[http://www.ubuntuforums.org/showthread.php?t=373055](http://www.ubuntuforums.org/showthread.php?t=373055)

---

### Post by Sanchopinky on 2007-03-16
Thanks Qpwoeiruty for the help on installing.

I'm playing around with gdesklets so far it's awesome.  Thanks guys for the help, btw how do I get that mac OSX-looking dock?

---

### Post by qpwoeiruty on 2007-03-16
gnome-dock or engage, maybe kxdocker. There may be others. I don't use any.
I'm not sure how to install engage in Gnome and kxdocker is a KDE app, so loading will be slower in Gnome.

For gnome-dock, follow the tutorial [here](http://ubuntuforums.org/showthread.php?t=302570)

---

### Post by Sanchopinky on 2007-03-16
Things never seem to go my way.. and beinga  complete linux n00b doesn't help either.

I was following the tutorial and I got this far:

Step 4. Install Cairo 1.2.6-

drake@drake-desktop:~$ ./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
bash: ./configure: No such file or directory

I also tried installing Build Essential but no luck

---

### Post by Sanchopinky on 2007-03-17
Why is it so hard to install stuff on linux? :/

---

### Post by qpwoeiruty on 2007-03-17
> **Sanchopinky said:**
> Why is it so hard to install stuff on linux? :/

Most things can be had from the repositories and is easy to install, but some you just have to do it yourself... and this eye candy stuff takes a whole lot of steps to install.

A little bit more detailed on the install starting from where you are:

You will first need AIGLX to install. 
[AIGLX/Beryl installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29): Make sure to follow the instructions for your card (Nvidia or ATI).

```

wget http://cairographics.org/releases/cairo-1.2.6.tar.gz
tar xvf cairo-1.2.6.tar.gz
cd cairo-1.2.6
./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
make
sudo make install

```

Then download the file [here](http://ubuntuforums.org/showthread.php?t=302570&highlight=cairo-dock.tar.gz) to your desktop and continue:

```

sudo tar xvf ~/Desktop/cairo-dock.tar.gz -C /opt
cd /opt
make clean
make

```

Then change your virtual vertical size in Beryl from 1 to 2. 
Go to Beryl Settings Manager/General Settings/Numeric Values tab and change Vertical Virtual Size to 2.

To run the dock:
```

./cairo-dock --no-glitz

```

You can clean up some of those files you downloaded if you like:
```

rm -iR ~/Desktop/cairo-dock.tar.gz ~/cairo-1.2.6.tar.gz ~/cairo-1.2.6

```

If I'm not missing something, that should be it.
These are the same as in the tutorial, just expanded a little bit.

---

### Post by loanrangie on 2007-03-17
> **Sanchopinky said:**
> Why is it so hard to install stuff on linux? :/

 I with you on this one, as much as i'm loving the Linux experience, the main detraction is the installing process. Its easy if a program you want is in the add/remove section but otherwise its a real pita, i tried to install the flashplayer 9 update to FF and no matter what i try i cant get it to work. Terminal to me is for experienced programmers not the average bloke that doesnt have time to EF around using scripts for what should be simple tasks.

---

### Post by Sanchopinky on 2007-03-21
Do I need Beryl to use Gnome/Cairo dock? Because beryl is p##sing me off right now.. So I would rather like to use independant customization things than to depend on Beryl..

Is there a way?

---

