---
title: "New to Ubuntu"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Aspra on 2007-02-11
I'm as new as it comes to Ubuntu. I just need some basic help on installing, and updating programs. I almost get how to use Synaptic and add/remove. But i need help on things like installing plugins on Firefox manually. Download it from the site and installing it from the Terminal, I really need help on that kind of thing. Id really like to use Fluxbox and i have it installed and I switched the session but all there is a blank screen one tool bar and i cant right click and get to programs. when i click right is just comes up with a box that says "Fluxbox" and wont let me get to any programs Id like some basic tips and steps about how to work Ubuntu. I really like it and want to become really good at it someday.

---

### Post by nickoli_02 on 2007-02-11
I'm not very familiar with fluxbox so I'm not sure what it takes for configurability. Search google/forums for a guide on setting up fluxbox.

For installing plugins on firefox, what exactly do you need? Things like flash and mulitmedia plugins can be installed with automatix pretty easily. Again, search the forums on how to install automatix.

To keep programs up to date, this is all you need to do:

```
sudo apt-get update
sudo apt-get upgrade
```

Though Ubuntu automatically checks to see if there are new upgrades for your installed packages from time to time.

---

### Post by aysiu on 2007-02-11
I, too, have been baffled by Fluxbox.

I've found IceWM far easier to configure for new users.

---

### Post by empthollow on 2007-02-11
i use gnome primarily but i too am mezzmerized by fluxbox, the menu is the hardest obstical when starting out. the menu is in the ~/.fluxbox/menu file. you may need to create it in gedit or using fluxmenu (sudo apt-get -y install fluxmenu). i found alot of useful info on [http://fluxbox.org/](http://fluxbox.org/)  i can post my menu here but i am at work right now.
have fun!

---

### Post by Aspra on 2007-02-11
alright, so i guess ill wait awile befor I use Fluxbox. But I want help on things like comands, basic ones that I really should know. Im also having trouble with playing videos. AVIs and such.

oh and automatrix helped some. thanks. got flash working in pages.

---

### Post by nickoli_02 on 2007-02-11
Here's a user's guide for Debian. Ubuntu is debian's child of sorts, so much of the information is relevant.

[Debian Users Guide]("http://www.debian.org/doc/manuals/users-guide/users-guide.en.html")

---

### Post by Aspra on 2007-02-11
Much thanks.

---

### Post by Ozitraveller on 2007-02-11
FYI

Fluxbox Anyone?
[http://ubuntuforums.org/showthread.php?t=328138](http://ubuntuforums.org/showthread.php?t=328138)


enjoy..... :)

---

### Post by Sunflower1970 on 2007-02-11
> **aysiu said:**
> I, too, have been baffled by Fluxbox.

I've found IceWM far easier to configure for new users.

I'll second IceWM (I'm using it with Thunar). Spent the day configuring it. Took about an hour to get the hang of editing all the files, but once I started, it was much simpler than I could have imagined. :)

---

### Post by Aspra on 2007-02-11
> **Sunflower1970 said:**
> I'll second IceWM (I'm using it with Thunar). Spent the day configuring it. Took about an hour to get the hang of editing all the files, but once I started, it was much simpler than I could have imagined. :)

Very intresting. think some one new to linux can figure it out?

---

### Post by aysiu on 2007-02-12
> **Aspra said:**
> Very intresting. think some one new to linux can figure it out?
Yes, especially if she installs *iceme* and *icepref*--graphical frontends for the menu and preferences configuration files.

---

### Post by Sunflower1970 on 2007-02-12
> **Aspra said:**
> Very intresting. think some one new to linux can figure it out?

I would think so. I've been using Ubuntu for over a month, now, still have lots to learn, yet once I learned where all the files were in icewm, I was able to go in and configure them. Kind of felt like I was setting up a webpage, actually. :)

I tried the GUI interfaces, and although I used them for some items (like changing fonts) I found it easier to just go in and edit the text files manually.

---

