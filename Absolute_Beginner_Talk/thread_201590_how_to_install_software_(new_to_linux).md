---
title: "how to install software (new to linux)"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Fringe on 2006-06-22
Okay, recently got Ubuntu installed on my computer (5.10, waiting for 6.06 CD to come in) and I'm an absolute beginner to Linux.  I tried doing a search in the forums on how to install software but can't seem to find anything with the keywords I used. So, I decided to just ask straight out. If I can get a sort of walkthrough with one installation, maybe I can do the rest myself, I was thinking. So, I thought I'd try installing the Opera web browser. The file I downloaded from the official Opera website is titled:

opera-9.0-20060616.6-share-qt.i386-en-344.tar.gz (is .deb easier?)

I opened it with the Archive Manager and see some folders and files.. 

folders:   bin, config, images, ini, java, lib, locale, man, plugins, skin, styles

files: html40_entities.dtd, svg-mo.dat, svg-mobd.dat, svg-sa.dat, svg-sabd.dat, svg-se.dat, svg-sebd.dat, LICENSE, lngcode.txt, opera6.adr, search.ini, install.sh, opera (sh), chartables.bin

I clicked on the install.sh file and it asked if I wanted to run "install.sh", or display its contents? I selected "Run in Termal" and it showed this in what I assume is the terminal:

Files will be installed as follows:
-----------------------------------------------------------
 Wrapper Script : /home/vincent/bin
 Binaries       : /home/vincent/lib/opera/9.0-20060616.6
 Plugins        : /home/vincent/lib/opera/plugins
 Shared files   : /home/vincent/share/opera
 Documentation  : /home/vincent/share/doc/opera
 Manual page    : /home/vincent/share/man
-----------------------------------------------------------
Is this correct [ y,n,c | yes,no,cancel ] ?

I typed "y" and pressed enter, it showed some text flash really quick that I couldn't read and it closed.  I assume it installed?   If it did, how do I run the actual program now?

Any other hints or tips would be appreciated as well, maybe links to tutorials, etc.  Also, I was trying to install xmms (mp3 player, I believe, which i hope to use until I learn how to install programs.. and am able to find an mp3 / ogg converter) and it says this in the readme:

cd xmms-1.2.8
./configure
make
make install

This will put the binary in /usr/local/bin and plugins in
/usr/local/lib/xmms/

How do I do the configure and make, make install thing?  And is the binary the actual program I run? 

Another thing (sorry, lol), when I try adding files to folders besides my home folder and folders created therein, it says I don't have permission, only "root" can write to those folders.  Am I not supposed to put files in these folders?  What if I have to?  Can I change these settings so I can write to the folders?  But my main question is how to install programs, so dont worry about this question unless I need to know in order to install programs.  Thanks everyone!

---

### Post by aysiu on 2006-06-22
.deb is a lot easier.
Opera makes a .deb specifically for Ubuntu.
Download that to your desktop and double-click it.

For XMMS, try ```
rm -rf xmms-1.2.8
sudo aptitude update
sudo aptitude install xmms
```

[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) will tell you everything you need to know about installing software.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) will tell you about permissions.

---

### Post by BoneKracker on 2006-06-22
Edit:  Okay ayisu covered that fully already.  My other two cents...

Before you go any further, I strongly suggest you click System > Help > Online Documentation (and read the Desktop Guide) if you haven't.  Exploring that help menu thoroughly will save you a lot of time and frustration and make your experience much more enjoyable.

---

### Post by Fringe on 2006-06-22
> **aysiu].deb is a lot easier.
Opera makes a .deb specifically for Ubuntu.
Download that to your desktop and double-click it.[/QUOTE]

Okay, I read that Ubuntu install site you gave me and it says a Package Installer should show up (on Dapper, should it do it on Breezy too?), but mine just opens in the Archive Manager and shows:

control.tar.gz
data.tar.gz
debian-binary

So, I tried the manual install of a .deb file I read on that site, using this:

vincent@ubuntu:~$ sudo dpkg -i /home/vincent/Desktop/opera_9.0-20060616.6-shared-qt_en_i386.deb
Selecting previously deselected package opera.
(Reading database ... 57520 files and directories currently installed.)
Unpacking opera (from .../opera_9.0-20060616.6-shared-qt_en_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) said:**
> For XMMS, try ```
rm -rf xmms-1.2.8
sudo aptitude update
sudo aptitude install xmms
```

Okay, for the XMMS, when I entered the code it said a bunch of "done"'s after everything in the terminal, any idea where I can run the program from now?  I used that Alt + F2 run application thing but couldn't find it in the list, I assume you can only find programs using that when you install the program with the package manager? I'm not sure. Sorry, I've been reading the sites you gave me over and over to see if I missed something but it doesn't say where I can find the program once installed, only when I use that Package Manager, it says I should find it in my Applications menu usually, but I don't.

---

### Post by Gustav on 2006-06-22
If you are on breezy you need to install .deb files via the terminal, type this to install a file.```
sudo dpkg -i <file>.deb
```

---

### Post by ZiZi on 2006-06-22
[QUOTE=Fringe]Okay, for the XMMS, when I entered the code it said a bunch of "done"'s after everything in the terminal, any idea where I can run the program from now?  I used that Alt + F2 run application thing but couldn't find it in the list, I assume you can only find programs using that when you install the program with the package manager? I'm not sure. Sorry, I've been reading the sites you gave me over and over to see if I missed something but it doesn't say where I can find the program once installed, only when I use that Package Manager, it says I should find it in my Applications menu usually, but I don't.[/QUOTE]

The Application menu must get refreshed before it displays new software installed, the easiest thing is to log out and log in, then the new apps should be listed. If simply don't want to, you can do the Alt-F2 and just type "xmms", that should do it. The system is searching for executable binaries in /bin, /sbin, /usr/bin, /usr/local/bin, most of the apps are in /usr/bin. You can locate the app's executable and some more types by typing ```
whereis <appname>
``` or ```
which <appname>
``` in terminal, the output will be something like this ```
xzilt02@xzilt02-laptop:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz
xzilt02@xzilt02-laptop:~$ which firefox
/usr/bin/firefox
``` However, you typically don't have to know where the application is, it is executed by just typing its name to the "Run application" dialog or to the console. In fact, this is my favorite feature, sometimes I tend to use Alt-F2 even in windows;)

---

### Post by ZiZi on 2006-06-22
Installing Opera in Dapper is a bit tricky, because it depends on some libraries which are no more available for Dapper. The easiest way is to add ```
deb http://deb.opera.com/opera/ stable non-free
``` repository using Synaptic (see [adding repositories in Synaptic]("http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29")), then update, then finally install "opera-static" package, which has the libraries compiled in itself. It is slightly larger, the fonts of the GUI are not as pretty as in the normal version, but for me it was much more convenient to install just one package than to have installed some more, which I don't need. 

If you find the unaliased fonts ugly, try this [Opera in Dapper HOWTO]("http://www.ubuntuforums.org/showthread.php?t=177449&highlight=Opera+Dapper"), which should do the trick.

The last possibility is to wait until the new Opera packages are issued. These are said not to depend on the old libraries any more, so the installation should just-work.

In your first post I saw that you had been trying to compile apps from source, which is not necessarry in my opinion. There are plenty of apps in Ubuntu repositories, which should suit most of any user's needs, just [enable restricted, universe and multiverse]("http://ubuntuguide.org/wiki/Dapper#Repositories") repositories and install the app by Synaptic. It is great, installation by just a few clicks, no fees, no catches, all you need is to be online.

---

### Post by linuxa on 2006-06-22
[QUOTE=Fringe]
The site says I have to handle the dependencies myself..  any ideas about that? Or is there a way I can use that synaptic package installer? I couldn't find a way to add Opera to it.  I keep getting that error when I try and an icon at the top right with a red circle and when I hover my mouse over it it says:

[/QUOTE]

Hi Fringe, Opera simply didn't install properly, no point in running it partially installed, since all it will do is give your errors.

Two packages that you need to install for your version of opera.
1) libqt3-mt. Type:
**sudo apt-get install libqt3-mt**

2) xlibs. Ubuntu 6.06 no longer uses xlibs as the default graphics library. So type:
**sudo apt-get install xlibs**

After installing the 2 packages. Remove opera
**sudo dpkg -r opera**

reinstall using the dpkg -i command you used on opera earlier.

It should hopefully work now.

The version of opera that you installed is the "shared" version (as indicated in the file name), which requires the xlibs package. There's also a "static" version which can ONLY be removed from the package manager, and doesn't require xlibs. 

AFAIK, if you download directly from opera.com you get the "shared" version.
Static version can be found here:
[http://snapshot.opera.com/unix/Weekly-320/intel-linux/](http://snapshot.opera.com/unix/Weekly-320/intel-linux/)

An old link that's no longer linked from anywhere I think.

Good luck.

---

### Post by Fringe on 2006-06-22
[QUOTE=ZiZi]The Application menu must get refreshed before it displays new software installed, the easiest thing is to log out and log in, then the new apps should be listed. If simply don't want to, you can do the Alt-F2 and just type "xmms", that should do it.[/QUOTE]

Okay, I think I got it where it will work, soon..    I had that red icon appear at the top again and it said I needed to fix my language files, like.. language-pack-en, language-pack-en-base, language-pack-gnome-en, language-pack-gnome-en-base.   I have 20051010 installed, but the ones it told me to uninstall are all 20051011, which I assume is newer?   Because I got a bunch of libs installed that the programs (xmms, opera, etc) said I needed and they intsalled fine, but when I run the program installs again, they all say:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Did I accidently uninstall the language support I need?  Remember, it asked me to fix them and I did.. but I realize that if I keep installing more libs.. they usually fix the problem and say I don't need to fix anything anymore.  I found this out AFTER uninstalling the language files though. I try installing them again but it will only let me select one at a time and they all say they depend on the other one to be installed too and I can't click them both at once..  how can I fix this, any ideas?  BTW, I'm on Breezy right now, I don't know if you read that in my first post or not.

---

### Post by Fringe on 2006-06-22
Okay, nevermind everyone!  I figured it out, thank you all so much.  :)   Everything was helpful and led me to finally learning how to install programs, any of them I want now! Yay

---

