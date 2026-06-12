---
title: "cant find bittorrent"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-03-12
hi i have a small problem here. according to synaptic package manager i have installed bittorrent but when i go to Applications->Internet it is not there and i cant find it anywhere in applications. where is it?? and can i start it somehow maybe with a command in the terminal or something if i cant find the bittorrent start icon

---

### Post by taurus on 2007-03-12
Have you tried to run it from a terminal to see if it starts/words?

```
bittorrent
```
Otherwise, you could also install the GUI add-on.

```
sudo aptitude update
sudo aptitude install bittorrent-gui
```

---

### Post by Sven Nijs on 2007-05-26
same problem here and getting no joy despite following the above instructions :(

---

### Post by ugm6hr on 2007-05-26
I think you need to install a GUI frontend for bittorrent if you want to run it with an icon.  I think BitTorrado is the one in Synaptic (sorry - I'm on a Windows machine now).  That will then have a menu icon.

Honestly, I found all the torrent GUI engines in Synaptic pretty useless, except ktorrent.  Obviously, this is designed for kubuntu rather then ubuntu, but given I run Xubuntu - it doesn't matter.  Shame I couldn't find Transmission bittorrent - I've used that in Puppy Linux - and it's simple.

---

### Post by Sven Nijs on 2007-05-26
> **ugm6hr said:**
> I think you need to install a GUI frontend for bittorrent if you want to run it with an icon.  I think BitTorrado is the one in Synaptic (sorry - I'm on a Windows machine now).  That will then have a menu icon.
Thanks. I thought I had (following the above instructions and subsequent updates) but there is no sign of it anywhere...
> Honestly, I found all the torrent GUI engines in Synaptic pretty useless, except ktorrent.  Obviously, this is designed for kubuntu rather then ubuntu, but given I run Xubuntu - it doesn't matter.  Shame I couldn't find Transmission bittorrent - I've used that in Puppy Linux - and it's simple.
I may have to take an alternative route it seems -Wine & µTorrent or stick to using a Windows box?
Thanks again.
Sven

---

### Post by RomeReactor on 2007-05-26
Hi. Sven, don't know if you'll get to read this (since you're offline at the moment), but does double-clicking on a .torrent file bring the application up? Also, on a default Ubuntu installation, BitTorrent *is* installed, but does not appear in the menu (Applications-->Internet); double-clicking on .torrent files is the common way to start or resume a download; for it to show up on the menu, right-click on the Applications-Places-System menu and select "Edit Menus"; select "Internet" on the left pane, and check the "BitTorrent" entry on the right (should be the first one).

---

### Post by Sven Nijs on 2007-05-26
Cheers RomeReactor! =D>
That's exactly what I needed to do and it all seems to work now. I'm obviously too used to µTorrent & Windows.#-o

---

### Post by nonewmsgs on 2007-05-26
right click the menu at the top of the screen select edit menu and then internet options and checkmark the box next to bittorrent.  why is this hidden by default anyway?

---

### Post by Sven Nijs on 2007-05-26
> **nonewmsgs said:**
> right click the menu at the top of the screen select edit menu and then internet options and checkmark the box next to bittorrent. 
Thanks, all sorted now.
 > why is this hidden by default anyway?
I agree, it certainly doesn't help beginners like me! ](*,)

---

### Post by Haegin on 2007-06-02
I think it's hidden as normally you will find a .torrent file on the web, click to download it and the default action is to open it with the bittorrent program.

---

### Post by Sven Nijs on 2007-06-02
It makes sense *once* you know about it but two factors conspired to confuse me:
I'm coming from a mainly Windows background and am used to using µTorrent with it's up-front GUI, multiple options etc etc &
The add & remove programs says bittorrent is installed but doesn't mention that it's hidden....

---

### Post by Haegin on 2007-06-02
Never fear - the default bit torrent client is only the default and one of the things you will (hopefully) grow to love about Linux is the sheer amount of choice. There are many other bit-torrent clients available and I have listed some below.

_Azureus_
Website: [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
Download: Available in the Ubuntu Repositories
Description: A full featured and very popular bit-torrent client written in Java. Available on Linux, Windows and Mac.

_Transmission_
Website: [http://transmission.m0k.org/](http://transmission.m0k.org/)
Download: [http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)
Description: A lightweight yet feature filled bit-torrent client available on five operating systems including Mac OSX and Linux. Currently still under active development but seems to be functional and stable.

_Deluge_
Website: [http://deluge-torrent.org](http://deluge-torrent.org)
Download: Available in the Ubuntu Repositories
Description: A nice python based client that is currently under active development. Seems less stable in my experience than transmission.

---

### Post by Sven Nijs on 2007-06-02
> **Human Prototype said:**
> Never fear - the default bit torrent client is only the default and one of the things you will (hopefully) grow to love about Linux is the sheer amount of choice. There are many other bit-torrent clients available and I have listed some below.

Thanks. Sorry if it sounded like a whinge but the smilie didn't work.
I'm giving Ubuntu a decent go and will give your suggestions a try. Ubuntu's definitely more 'user input intensive' than I thought it would be but I'm happy to stick with it.

---

### Post by Haegin on 2007-06-02
Ubuntu is more user input intensive until you are more familiar with it - then you will find you can do what you need to do without it getting in your way (or annoying apps sitting in the tray when you don't want them there hogging system resources) letting you get more done faster.

You will learn which programs are good for which things soon enough and you had to do this on Windows, you just don't remember it all as it happened slowly.

At some point you probably scoured the web finding which bit torrent client to use and finally settled on uTorrent or whichever you picked.

This will have happened for various different programs when you developed a need for them but with Windows the need developed over time so you didn't have to find all the programs at once. With Linux you know what you want to be able to do so you now need to find programs for lots of different tasks at once causing it to appear more user input intensive.

If you need to find more programs for specific tasks try looking on [http://www.gnomefiles.org/](http://www.gnomefiles.org/), an online guide to software that is available for Gnome (mostly) covering a wide variety of tasks.

---

