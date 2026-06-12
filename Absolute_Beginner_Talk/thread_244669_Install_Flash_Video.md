---
title: "Install Flash Video"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-08-26
I need to install flash player so that I can view online video/movie.  When I attempt to watch now all I get is the sound.  I am new to ubuntu and need some detailed help, please!!  I have tried to look through old posts but I am apparently an idiot, can't get it to work.

---

### Post by gn2 on 2006-08-26
The best way is to use Automatix. This gives options to install a raft of useful bits and pieces.

[http://getautomatix.com/wiki/index.php?title=Installation#Automatic_Automatix_Installer_.28does_not_work_on_Mepis_yet.29](http://getautomatix.com/wiki/index.php?title=Installation#Automatic_Automatix_Installer_.28does_not_work_on_Mepis_yet.29)

The section Automatic Automatix Installer is what you need.

It tells you to copy and paste the lines into a terminal one after the other.

The first line includes a URL.

The next bit confused me at first, because you need to copy the next two lines as one line.

You will be presented with a range of options to install.

Hope this helps.

---

### Post by TFX360 on 2006-08-26
Lack of knowledge doesn't make you stupid. Ignorant more probably.

Download flash from [here]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz"). Firefox will put it on the Desktop automatically.

Open a terminal and type


```
cd /home/**yourusernamehere**/Desktop
```
```

sudo tar -xvzf install_flash_player_7_linux.tar.gz
```

```
cd install_flash_player_7_linux
```

```
sudo ./flashplayer-installer
```

And follow the instructions.

You should install the following fonts according to the installer

Again type in your terminal:

```
**aptitude install gsfonts**
```

```
**aptitude install gsfonts-X11**
```


Kind regards,


TFX

---

### Post by bvexen2 on 2006-08-26
I followed the instructions above and Terminal told me this:

Preconfiguring packages ...
(Reading database ... 63205 files and directories currently installed.)
Preparing to replace automatix 5.8.3 (using .../automatix_6.4-6-5.10breezy1_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (6.4-6-5.10breezy1) ...
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
robert@ubuntu:~$


what next?

---

### Post by TFX360 on 2006-08-26
> **bvexen2 said:**
> I followed the instructions above and Terminal told me this:

Preconfiguring packages ...
(Reading database ... 63205 files and directories currently installed.)
Preparing to replace automatix 5.8.3 (using .../automatix_6.4-6-5.10breezy1_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (6.4-6-5.10breezy1) ...
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
robert@ubuntu:~$


what next?

Try my post, or open a terminal and type:


```
sudo aptitude update; sudo aptitude upgrade
```

And if you want to dist-upgrade (new kernel if available)

```
sudo aptitude dist-upgrade
```


Kind regards,


TFX

---

### Post by gn2 on 2006-08-26
Go back to the Automatix page and try the next option down,Installing with Apt.

The Automatic version worked for me.

---

