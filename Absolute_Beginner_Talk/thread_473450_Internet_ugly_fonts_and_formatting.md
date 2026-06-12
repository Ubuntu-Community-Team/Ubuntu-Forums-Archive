---
title: "Internet ugly fonts and formatting"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-06-14
Is there anyway to make fiesty render websites like windows? Most websites are noticably uglier in ubuntu then they are in windows.

The fonts aren't as clear or something and almost all buttons and forms look terrible. Its sort of like being back on netscape 4 or something.. everything is square and jaggy.

---

### Post by Bachstelze on 2007-06-14
Install the correct fonts :

```
sudo apt-get install gsfonts-x11 msttcorefonts
```

---

### Post by Unreal223linux on 2007-06-14
Thanks its downloading now. Do I need to do anything else once its installed or will it just apply on its own?

---

### Post by Bachstelze on 2007-06-14
Maybe just restart your browser or log out and log back in. Restart X if you want to play it safe :p

---

### Post by coffeecat on 2007-06-14
If you are using a flat screen monitor, try this. From a terminal:

```
sudo dpkg-reconfigure fontconfig-config
```Choose 'autohinting' from the  first choice and the default for the next two. For autohinting to work you must restart the Xserver - clt-alt-backspace is the quick way.

If you don't like autohinting, just run that command again and switch it off. If you do, now that you have installed the microsoft core fonts, go into System > Preferences > Fonts and change all the system fonts to Verdana or Verdana bold for Window title. Don't change the monospace one. Now, in firefox, goto Edit > Preferences > Content, then 'Advanced' and change Sans-Serif to Verdana and Proportional to Sans-Serif.  Close firefox and restart.

The choice of Verdana is a personal one. You may or may not like it, but in my view font rendering set up this way is superior to an Apple Mac. And before an Apple fanchild objects let me say that I have two Linux boxes and a Mac Mini connected to the same good quality 1680x1050 monitor through a KVM switch. The font rendering on the Mac desktop is predictably good. On my Linux desktops it is absolutely stunning. And Windows? Acceptable. :lol:

---

### Post by mcduck on 2007-06-14
For the firefox widgets, that's a known issue with Linux version of Firefox. For some reason it's using it's own very ugly widgets instead of supporting GTK2 or even having a bit nicer widgets of it's own.

But no worries, they are easy to replace. Just follow the link: [http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets]("http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets")

---

### Post by ecs_pf5 on 2007-06-14
How would I change the size of this text? This is the only part I can't seem to make a little larger. The actual text within a post..

---

### Post by mcduck on 2007-06-14
> **ecs_pf5 said:**
> How would I change the size of this text? This is the only part I can't seem to make a little larger. The actual text within a post..
Try setting the minimum font size in Firefox's font settings.

---

### Post by ecs_pf5 on 2007-06-14
[LEFT]Spot on, thanks :p
[/LEFT]

---

### Post by sandeep108 on 2007-06-14
This should be a sticky. Lots of people reporting font rendering issues and I also had to search a lot before I could get ubuntu/ff looking cleaner/sharper.

---

