---
title: "Questions about Add-Ons"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by 3xpl0it on 2008-03-01
Hello,

I have a few questions.

1. What are these?
[http://www.youtube.com/watch?v=ZD7QraljRfM&feature=related](http://www.youtube.com/watch?v=ZD7QraljRfM&feature=related)
On the top of his screen is like a box of quick shortcuts.  How do you enable these?

2. How does everyone get the cool widgets.  Like weather, computer monitor, etc.

Please point me in the right direction, I am very new to this.

Thank you very much in advance!
-3xpl0it

---

### Post by jken146 on 2008-03-01
The flashy effects are compiz-fusion.  Install the package **compizconfig-settings-manager** and then go to System -> Preferences -> Appearance -> Desktop Effects and click on Custom.  Then play around with the options.  You may need to install the restricted driver for your graphics card before you do this.

The thing at the top looks like a dock.  Avant Window Navigator is one such dock.

I think the widgets are connected with compiz-fusion, but there is something more to install.

---

### Post by TeoBigusGeekus on 2008-03-01
1. I think it is the Avant Window Navigator (AWN) 
[http://linuxhelp.blogspot.com/2008/02/install-avant-window-navigator-awn-in.html]("http://linuxhelp.blogspot.com/2008/02/install-avant-window-navigator-awn-in.html")
2. These are screenlets. You could use desklets but they are older and less shiny.
[http://tombuntu.com/index.php/2007/12/03/os-x-like-widgets-with-screenlets-on-ubuntu-update/]("http://tombuntu.com/index.php/2007/12/03/os-x-like-widgets-with-screenlets-on-ubuntu-update/")
For lots of screenlets
[http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=6bfe368fd03ce09ab112c229776af8c5]("http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=6bfe368fd03ce09ab112c229776af8c5")

---

### Post by Athelstan101 on 2008-03-01
If you're using the GNOME desktop, then you can get the weather, computer monitor etc. widgets by right-clicking on the gnome panel and selecting 'Add to Panel...'.

---

### Post by 3xpl0it on 2008-03-01
> **TeoBigusGeekus said:**
> 1. I think it is the Avant Window Navigator (AWN) 
[http://linuxhelp.blogspot.com/2008/02/install-avant-window-navigator-awn-in.html]("http://linuxhelp.blogspot.com/2008/02/install-avant-window-navigator-awn-in.html")
2. These are screenlets. You could use desklets but they are older and less shiny.
[http://tombuntu.com/index.php/2007/12/03/os-x-like-widgets-with-screenlets-on-ubuntu-update/]("http://tombuntu.com/index.php/2007/12/03/os-x-like-widgets-with-screenlets-on-ubuntu-update/")
For lots of screenlets
[http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=6bfe368fd03ce09ab112c229776af8c5]("http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=6bfe368fd03ce09ab112c229776af8c5")

Thank you very much, but in the guide there it says open the sources.list file?  Where would this be located?

Thanks,
-3xpl0it

---

### Post by TeoBigusGeekus on 2008-03-02
You must be talking about the screenlets guide.

Go to applications -> accessories -> terminal
Type the command of the tutorial
    sudo gedit /etc/apt/sources.list
The file sources.list will open with superuser priviledges (i.e. you can modify it)
Add this line at the end of the file
    deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
and save it.
While still in terminal type the following commands
    wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- 
    sudo apt-key     add - && sudo apt-get update
    sudo apt-get install screenlets
and you are done.

I think you can take it from here...

---

### Post by 3xpl0it on 2008-03-02
thanks, I realized that was the command to open the file. lol

Thanks again!
-3xpl0it

---

