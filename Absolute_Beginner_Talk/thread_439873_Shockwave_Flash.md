---
title: "Shockwave Flash?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by BoysBoysBoys on 2007-05-11
I wish that I could just double click on a file and it installs. I have no Idea how to install things with ubuntu or linux for that matter. For instance I need to install the flash plugin for firefox but when I go to the download site for flash it gives me the option to download a .tar.gz or a .rpm. Where are my .EXE's!

---

### Post by Iceni on 2007-05-11
There are no .exes in ubuntu. You want a .deb file, or mainly use the synaptic package manager for your software needs.

---

### Post by Kobalt on 2007-05-11
The .exe files are more complicated and unsafe than the Ubuntu way, example for flash : go to Applications > Add/Remove. Search for *flash*, select it and press Validate. 
You're done, you've installed the latest version of the Flash plugin for you browsers :)

---

### Post by Martin on 2007-05-11
Yes, well that would be one of the many difference between linux and windows - no exe files. Some things appear a little clumsy, others are easier. My suggestion would be to visit the site [http://www.getautomatix.com](http://www.getautomatix.com) and download the automatix package for feisty (i presume yuo re using 7.04 or feisty). It is a one click install. Once installed automatix allows you to install all sorts of things like flash etc. with a simple click.

---

### Post by mcduck on 2007-05-11
Just go to Applications - Add/Remove.. Find the flash plugin, mark it & click OK. The program will be automatically downloaded & installed for you ;)

Then read this: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

You might want to install the 'Ubuntu Restricted Extras' while you have the Add/Remove open. You'll want it sooner or later anyway.. If you can't find it, open the dropdown menu in the top right corner and change it to 'All available Applications'

---

### Post by jonathan21 on 2007-05-11
install alien by doing the following

open terminal which is under applications then accessories.


type sudo apt-get install alien

put flash.tar.gz in home directory

open terminal again and type alien flash installer.tar.gz

that should convert flash from tar to deb

open file it will install

---

### Post by BoysBoysBoys on 2007-05-11
When I did the add/remove... thing and searched for "flash" I got...

Movie Player
gxine
KEduca
KEduca-Editor
KVocTrain

:(

---

### Post by ubnewbie2 on 2007-05-11
forget add/remove, it's brain dead, only knows about some of the available software.

Use Synaptic, search for flash, and you'll find lot's more stuff, including  'flashplugin-nonfree'.

---

### Post by mcduck on 2007-05-11
> **BoysBoysBoys said:**
> When I did the add/remove... thing and searched for "flash" I got...

Movie Player
gxine
KEduca
KEduca-Editor
KVocTrain

:(

Did you change the dropdown box in top right to 'All available Applications'?

---

### Post by ubnewbie2 on 2007-05-11
> **Martin said:**
> Yes, well that would be one of the many difference between linux and windows - no exe files. Some things appear a little clumsy, others are easier. My suggestion would be to visit the site [http://www.getautomatix.com](http://www.getautomatix.com) and download the automatix package for feisty (i presume yuo re using 7.04 or feisty). It is a one click install. Once installed automatix allows you to install all sorts of things like flash etc. with a simple click.

I see automatix recommended, but I don't know why.  How is it better than, say, Synaptic? If it doesn't have very significant advantages, I'd rather stay with the distribution supported programs.

---

### Post by BoysBoysBoys on 2007-05-11
> **mcduck said:**
> Did you change the dropdown box in top right to 'All available Applications'?

I changed it to all available and it now shows macromedia flash plugin but the checkbox is greyed out and I cant select it :mad:

---

### Post by mcduck on 2007-05-11
What version of Ubuntu are you running? Go to System/Administration/Software Sources and enable both Universe (Community maintained) and Multiverse (Software restricted by copyright or legal issues). After that you should be able to install flash plugin.

---

### Post by BoysBoysBoys on 2007-05-11
Im using Fiesty Fawn the 64bit edition. All of the options you mentioned are checked already.

---

### Post by BoysBoysBoys on 2007-05-11
I just read the fine print under the macromedia flash description. It says "Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type."

Should I just dump the 64bit and install the 32bit version?

---

### Post by mstlyevil on 2007-05-11
> **BoysBoysBoys said:**
> I just read the fine print under the macromedia flash description. It says "Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type."

Should I just dump the 64bit and install the 32bit version?

You can get flash to work with AMD64. 

The first thing you will need to do is install ia32libs.

```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl ia32-sun-java6-bin lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ffi4 lib32gfortran1 lib32ncurses5 lib32mudflap0 lib32objc1 lib32readline5 lib32stdc++6 lib32z1 gsfonts gsfonts-x11 alsa-oss m4 oss-compat dchroot linux32
```

The second thing you will want to do is download Flash directly from adobe.

The third thing you will want to do is move the tar file you downloaded to a safe directory away from apt.

```
sudo tar zxvf $AXHOME/install_flash_player_9_linux.tar.gz -C /opt
```

Now we will create a new folder

```
sudo mv -f /opt/install_flash_player_9_linux /opt/flash32
```

Now we will change the permissions on a couple of files.

```
sudo chmod 755 /opt/flash32/libflashplayer.so
sudo chmod 755 /opt/flash32/flashplayer.xpt
```

Now we need to create a couple of synlinks.

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo ln -s /usr/lib32/libesd.so.0 /usr/lib32/libesd.so.1
sudo ln -s /tmp/.esd-1000 /tmp/.esd
```

Now you should have flash player installed on AMD64.

Just a side note here. This is exactly what Automatix2 does to install flash on AMD64 if you do not have the confidence to do it yourself. Also sun-java6 will not work in a 64 bit browser but will in a 32 bit browser on AMD64.

---

### Post by rich.bradshaw on 2007-05-11
I wouldn't bother with 64 bit unless you have some specific reason - it's more hassle than it's worth.

---

### Post by BoysBoysBoys on 2007-05-12
I just installed the 32-bit version of ubuntu. The reason is because I couldn't get flash to work, and someone was helping me in a second thread to realign my display using xvidtune, unfortunately xvidtune also does not work with the 64-bit version.

---

### Post by jiminycricket on 2007-05-12
It's really too bad that Adobe holds so much power to make people switch away from 64 bit.  It's Adobe's fault, not ubuntu since they are closed source.

Anyways, how to install on ubuntu gnu/linux: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

nspluginwrapper allows you tro run 32 bit flash on 64 bit linux: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

Also, if you stay tuned, open source flash replacement programs called gnash and swfdec will someday be able to do this by default.

---

