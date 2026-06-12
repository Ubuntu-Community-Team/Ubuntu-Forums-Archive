---
title: "Installing Firefox 1.5.0.1"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Souljah on 2006-02-19
Well I remember asking this question many many months back and now I have the same problem. When I downloaded the latest version from the mozilla website, the file name is "firefox-1.5.0.1.tar.gz". Now I extract it to my desktop. A file in the newly created folder called Firefox (it has a 'sh' abbreviation in the icon) is there. Now when I double click it, I get a few options like to run, cancel etc. I click on Run. Nothing happens, no installer, nothing. How do I install it, I'm really at a loss here. Trying to relearn linux and I'm not getting anywhere with installing applications. 

On a sidenote as well, I also downloaded the skype package which was named "skype_1.2.0.18-1_i386.deb". I also extracted that, but got an error.

For these 2 apps, how do I go about installing them. :(

---

### Post by heimo on 2006-02-19
There already exists great guide for installing 1.5-series firefox to Breezy, so I won't repeat it here:
[https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

For the skype, I suppose it should work just by running:
```
dpkg -i skype_1.2.0.18-1_i386.deb
``` 
If it's on your Desktop, this should work:
```
dpkg -i ~/Desktop/skype_1.2.0.18-1_i386.deb
```

EDIT:
[https://wiki.ubuntu.com/Skype](https://wiki.ubuntu.com/Skype)
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

---

### Post by aysiu on 2006-02-19
[QUOTE=heimo]
For the skype, I suppose it should work just by running:
```
dpkg -i skype_1.2.0.18-1_i386.deb
``` 
If it's on your Desktop, this should work:
```
dpkg -i ~/Desktop/skype_1.2.0.18-1_i386.deb
```

EDIT:
[https://wiki.ubuntu.com/Skype](https://wiki.ubuntu.com/Skype)
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)[/QUOTE] The only luck I've had with Skype is downloading the .rpm for Fedora Core and then doing this: ```
cd Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i skype*.deb
```

---

### Post by Souljah on 2006-02-19
This is what occurs when I try to install skype:

Selecting previously deselected package skype.
(Reading database ... 57601 files and directories currently installed.)
Unpacking skype (from .../skype_1.2.0.18-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /home/ryan/Desktop/skype_1.2.0.18-1_i386.deb (--install): short read in buffer_copy (backend dpkg-deb during `./usr/bin/skype')
Errors were encountered while processing:
 /home/ryan/Desktop/skype_1.2.0.18-1_i386.deb

--

A note on installing firefox, I all ready downloaded it to my desktop. Now when I try to extract it to that /opt folder it tells me I don't have permission. Those instructions are so confushing. :(

---

### Post by aysiu on 2006-02-19
Yeah, forget about the .deb.
Most of the time, when you're looking for stuff for Ubuntu, you want a .deb, but in the case, you actually want the .rpm.

---

### Post by heimo on 2006-02-19
[quote=Souljah]
A note on installing firefox, I all ready downloaded it to my desktop. Now when I try to extract it to that /opt folder it tells me I don't have permission. Those instructions are so confushing. :([/quote]

Use the instructions on wiki and it'll work. And for the skype, follow the instructions aysiu gives - you need to download rpm version and convert it to .deb (just as aysiu shows, for some reason the .deb file isn't working).

---

### Post by Souljah on 2006-02-19
[QUOTE=aysiu]Yeah, forget about the .deb.
Most of the time, when you're looking for stuff for Ubuntu, you want a .deb, but in the case, you actually want the .rpm.[/QUOTE]

Where would I get the .rpm package? Any link for that?

---

### Post by aysiu on 2006-02-19
[QUOTE=Souljah]Where would I get the .rpm package? Any link for that?[/QUOTE] Sure:
[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

Look for the Fedore Core 3 package.

---

### Post by Souljah on 2006-02-19
I'm totally confused. In the wiki, it says " Download [WWW] firefox-1.5.0.1.tar.gz from [WWW] mozilla.com, and **change to the directory you downloaded it to**." Now what do they mean by change to the directory? Do they mean copy it? I all ready downloaded it to my desktop but it won't copy to the opt folder. When I do execute the install instructions it gives me this:

ryan@PC:~$ # extract tar into /opt (you should make sure /opt already exists)
ryan@PC:~$  sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
tar: firefox-1.5.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ryan@PC:~$  # remove the package if you no longer require it
ryan@PC:~$  rm firefox-1.5.0.1.tar.gz
rm: cannot remove `firefox-1.5.0.1.tar.gz': No such file or directory

--

I'm sorry I know it might be easy for you but for me it's like a new language.

---

### Post by aysiu on 2006-02-19
```
cd Desktop
``` changes to the directory you downloaded it to.

---

### Post by heimo on 2006-02-19
These instructions are not fully tested.

Short instructions for installing skype using Dynamic binary and Static binary packages from [Skype download page]("http://www.skype.com/products/skype/linux/") Download the version you want to install to your desktop.

Extract to /opt, using this command:
```
sudo tar -C /opt -xjvf  ~/Desktop/skype-1.2.0.18.tar.bz2
OR
sudo tar -C /opt -xjvf ~/Desktop/skype_staticQT-1.2.0.18.tar.bz2

```

Copy icons:
```
sudo cp /opt/skype-1.2.0.18/icons/*.png /usr/share/pixmaps/
```

Create symlink to /usr/bin.
```
sudo ln -s /opt/skype/skype-1.2.0.18/skype /usr/bin/
```

Create launcher. In Gnome (Ubuntu default desktop) right click on panel and choose Add to panel. Choose Custom Application Launcher. For name, type "Skype".  For command, type: "skype" (without quotation marks). Choose an icon (clicking on *no icon* text).

Click on the new launcher. On my computer it took ~30 seconds to launch Skype.

---

### Post by Souljah on 2006-02-19
Thanks Aysiu, that worked. Only thing is that the firefox icon at the top is the default one. So just one quick questions, in windows to install an app you just double click on the file. Well, in linux what is the default command for installing apps? Is is sudo apt-get or what?

---

### Post by aysiu on 2006-02-19
[QUOTE=Souljah]Thanks Aysiu, that worked. Only thing is that the firefox icon at the top is the default one.[/quote] Default *icon* (blue globe) or default *Firefox* (the Ubuntu 1.0.7)? 

For the globe icon problem, try [this](http://ubuntuforums.org/showthread.php?t=34354).
For the launcher launching the proper version of Firefox make sure you don't ignore this part of the Wiki instructions: ```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

> So just one quick questions, in windows to install an app you just double click on the file. Well, in linux what is the default command for installing apps? Is is sudo apt-get or what? See the second link of my signature.

---

### Post by heimo on 2006-02-19
aysiu can probably describe much better how installing software in Linux distributions work, but I'll try anyway. The power of so called FLOSS (Free Libre Open Source Software) is source code, the actual stuff that programmers work on. You can get all the free software in source code format and compile it to binaries which can be executed by your operating system.

But you don't have to. Distributions (like Fedora, Suse, Ubuntu) compile and package thousands of applications and software libraries into collections of software. In Debian based distributions like Ubuntu is, the native package format is "deb". The other major package format is Redhats rpm. The power of packaging software for specific platform is that you can have tighter integration and tested combination of packages. Packages know what other software is needed to run it, these dependencies are called *dependencies*. ;) Package manager and Linux distributions take care of all of this for you.

Collections of packages are served using (mostly) http and ftp servers, repositories.
[https://wiki.ubuntu.com/Repositories]("https://wiki.ubuntu.com/Repositories")

As long as you use package management to install all the software on your system, your operating system can keep book on all the dependencies, can make updates and upgrades cleanly and remove software - using just one tool - front end to lower level package management tools. Best graphical user interface I've seen so far is Synaptic (I've heart about better ones for other distributions, but haven't seen them personally):
[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")
[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

For command line, there's probably no better tool than apt. 
[https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo]("https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo")

---

### Post by Souljah on 2006-02-19
I tried installing Skype through this method [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto) but it doesn't show up in my applications menu. I have tried the other link but I'll how that works out. Hiemo and Aiysu thanks for those instructions of how to install applications.

I managed to install the lower version of skype provided in the link. It's fine now. Though I haven't received a call.

---

### Post by heimo on 2006-02-19
To create shortcut to Applications->Internet menu for Skype:
```
gksudo gedit /usr/share/applications/skype.desktop
``` 
Paste this text:
```
[Desktop Entry]
Encoding=UTF-8
Name=Skype
Comment=Make internet phonecalls
GenericName=Internet Phone
Exec=skype
Terminal=false
MultipleArgs=false
Type=Application
Icon=skype_32_32.png
Categories=Application;Network
``` 
Save, exit.
(you need to have icon skype_32_32.png in /usr/share/pixmaps)

Reload panels (by shutting down, they'll restart automatically):
```
killall gnome-panel
```

---

### Post by Souljah on 2006-02-19
I reloaded the panels with the latest version of skype installed (not the downgraded version) and it kinda changed the settings for my mouse. What's happening is that the mouse functions when used in conjunction with firefox is not working. For example, if I want to close a tab if it's open, I would press the middle button and it would work but now it seems to load a webpage which appears to be in text format. Any idea how to restore the default settings for my mouse inclusive of the firefox settings?

---

### Post by heimo on 2006-02-19
[quote=Souljah]I reloaded the panels with the latest version of skype installed (not the downgraded version) and it kinda changed the settings for my mouse. What's happening is that the mouse functions when used in conjunction with firefox is not working. For example, if I want to close a tab if it's open, I would press the middle button and it would work but now it seems to load a webpage which appears to be in text format. Any idea how to restore the default settings for my mouse inclusive of the firefox settings?[/quote]
This really shouldn't happen when restarting panels, but I've seen stranger things happen. In firefox, go to address *"about:config"* search for *"middle".* Double click on the option *middlemouse.contentLoadUrl* - make sure its value is *"false".*

---

### Post by Souljah on 2006-02-19
Yes that seemed to work by changing it to false. Why did that happen anyway?

---

### Post by heimo on 2006-02-19
[quote=Souljah]Yes that seemed to work by changing it to false. Why did that happen anyway?[/quote]

I can't see any correlation with killall gnome and firefox configuration changing suddenly. Did you install updates recently? It has happened to me that I need to redo some changes to firefox settings after it has been updated (at least with major version changes).

---

### Post by Souljah on 2006-02-19
Well the only thing I really did was to downgrade the skype version. I will want to upgrade back. Since we're on this thread and instead of creating a new one, how do I prevent skype and gaim from loading up at startup. Just one more question before this thread can be put to rest... In the update manager for ubuntu, how do deselect them all at once. I had a preview release of ubuntuu and there's well over 400+ updates. Anyway of deselecting them or like pausing them.

---

