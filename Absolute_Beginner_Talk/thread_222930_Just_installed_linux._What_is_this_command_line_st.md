---
title: "Just installed linux. What is this command line stuff?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by lauzsta on 2006-07-25
To be honest I wish i didnt install linux, but Im going to stick with it. I do not know anything about command line stuff and i want to install programs but i havent a clue how. A little help would go a long way with me.

Thanks in advance,
Laurie

---

### Post by sethmahoney on 2006-07-25
Click on the System menu, then on Administration, then on Synaptic Package Manager.  Most of the programs you will want to install are in there.

---

### Post by avtolle on 2006-07-25
What are you looking to install? My advice is to enable the extra repositories under Synaptic, then do a search for what you are trying to install there, and install from there. Also, there are installation scripts known as EasyUbuntu and Automatix that will install some of the more popular/requested applications. Welcome to the Forums.

The command line stuff, as you call it, is a powerful way to assume control over your system. Better to leave it alone for now until you have more experience. I suspect you are post-MSDOS in your experience w/computers, so operating from the command line is very foreign. Best of luck.

---

### Post by Jagot on 2006-07-25
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by halfvolle melk on 2006-07-25
A comprehensive one for apt on the command-line:
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by deadgobby on 2006-07-25
Here is a couple of links to get you started to know Synaptic and some Terminal fun. 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)

Remember Linux is not windows... Thank Zod for that. There is a hell of alot of freedom of Linux.

---

### Post by richbarna on 2006-07-25
Don't panic over the command line, It's just a quick way of doing things. We normally post commands that you only have to copy and paste.
Most things can be done via a GUI as well. Just be patient, keep the questions coming and we'll help you as best as we can.

Remember to title your post well, and give us as much information as you can, it makes our lives easier when trying to help.

Welcome to ubuntu forums :)

---

### Post by lauzsta on 2006-07-25
Thanks for the very speedy replies !
Help is much appreciated, I will post titles clearer in future ;) 
I was looking to install last.fm player .

---

### Post by halfvolle melk on 2006-07-25
I don't really know what last.fm is, but I can't find it in the [repositories](https://help.ubuntu.com/community/Repositories) (software that is available for Ubuntu by default). I did find this:
[http://www.newspeak.org.uk/2005/10/28/lastfm-ubuntu-package/](http://www.newspeak.org.uk/2005/10/28/lastfm-ubuntu-package/)
> ben Says: 
 January 18th, 2006 at 10:21 pm 
Paul Telford, a debian maintainer, has made recent (unofficial yet) packages of last.fm player for both debian and ubuntu linux. check them at:
[http://people.debian.org/~pxt/lastfm/](http://people.debian.org/~pxt/lastfm/)

Now installing it. Open a terminal: Applications -> Accessories -> Terminal and do the following:
```
wget http://people.debian.org/~pxt/lastfm/lastfm_1.1.4-1ubuntu1_i386.deb
sudo dpkg -i lastfm_1.1.4-1ubuntu1_i386.deb
```
The first command downloads the file to the currect directory. The second installs the program. Haven't tried it, but it should work.

edit: sudo will ask for your user password.

---

### Post by lauzsta on 2006-07-25
```
Unpacking lastfm (from lastfm_1.1.4-1ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of lastfm:
 lastfm depends on libqt4-core (>= 4.0.0); however:
  Package libqt4-core is not installed.
 lastfm depends on libqt4-gui (>= 4.0.0); however:
  Package libqt4-gui is not installed.
dpkg: error processing lastfm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lastfm

```

Came up with this ^^

---

### Post by dasunst3r on 2006-07-25
If you would like a quick guide of all the commands available, go search for the "One-Page Linux Manual."  Although it is suited better for RPM-based systems, you will find that the commands are not all nonsense stuff.  After using it some, you may even find it faster than clicking!  Good luck!

---

### Post by halfvolle melk on 2006-07-25
> **lauzsta said:**
> ```
Unpacking lastfm (from lastfm_1.1.4-1ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of lastfm:
 lastfm depends on libqt4-core (>= 4.0.0); however:
  Package libqt4-core is not installed.
 lastfm depends on libqt4-gui (>= 4.0.0); however:
  Package libqt4-gui is not installed.
dpkg: error processing lastfm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lastfm

```

Came up with this ^^

Ok, run this
 
```
sudo apt-get install libqt4-core
sudo apt-get install libqt4-gui
```
and try the dpkg thing again afterwards.

---

### Post by Sef on 2006-07-25
> Unpacking lastfm (from lastfm_1.1.4-1ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of lastfm:
 lastfm depends on libqt4-core (>= 4.0.0); however:
  Package libqt4-core is not installed.
 lastfm depends on libqt4-gui (>= 4.0.0); however:
  Package libqt4-gui is not installed.
dpkg: error processing lastfm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lastfm

The key words are 'dependecy problems'.  A dependency is a program needed to make another program work.  In your case, it would be libqt4-gui.  There are two ways to install it:  1) via synaptic - just click search type libqt4-gui and then highlight it, then click apply.  2) Applications > Accessories > Terminal and type (without the quotes) 'sudo apt-get update' and then 'sudo aptitude install libqt4-gui'.

---

### Post by richbarna on 2006-07-25
Also, Amarok media player has Last.fm.
To configure it, go to Settings/Configure Amarok/Last.fm

---

