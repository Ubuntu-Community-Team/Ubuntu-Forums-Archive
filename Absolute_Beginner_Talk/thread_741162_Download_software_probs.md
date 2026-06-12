---
title: "Download software probs"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Sandro Batelli on 2008-03-31
Hi, I just installed Ubuntu but I can't download a thing! I've tried (as suggested by some forum replies to others) through Synaptic, Add/remove software (who doesn't allow me to " apply" ubuntu restricted extras) and finally Terminal  but no luck. For example gst basic plugins, GStreamer, Skype. Any ideas folks? What am i doing wrong? 
Peace&strenght
Sandro:confused:

---

### Post by wolfen69 on 2008-03-31
what errors are you getting? we need details.

---

### Post by kellemes on 2008-03-31
Have you enabled your repositories?
Goto System -> Administration -> Software Sources

---

### Post by Sandro Batelli on 2008-03-31
Thx guys.
U mean enable all the downloadable under Ubuntu software in Software sources?

---

### Post by Oldsoldier2003 on 2008-03-31
> **Sandro Batelli said:**
> Thx guys.
U mean enable all the downloadable under Ubuntu software in Software sources?

yes enable the first four repos on the first tab. also select a download location.

---

### Post by Sandro Batelli on 2008-03-31
These are some  errors i get:


 Ubuntu restricted extras

The use, modification and distribution of Ubuntu restricted extras is restricted by copyright or by legal terms in some countries.

In Terminal I get:

E: Couldn't find package skype
sandro@sandro-laptop:~$ sudo apt-get install GStreamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package GStreamer
sandro@sandro-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Reading package lists... Done
sandro@sandro-laptop:~$ sudo apt-get update sudo apt-get install skype
E: The update command takes no arguments
sandro@sandro-laptop:~$ sudo apt-get install gst-plugins-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gst-plugins-base
sandro@sandro-laptop:~$

---

### Post by Sandro Batelli on 2008-03-31
Hi, ubuntu is installing restricted extras. It has been almost half an hour. How long does it take? My processor is Intel P. 1,4 GHz

---

### Post by .nedberg on 2008-03-31
You need to enable more repositories.

Go to System->Software sources or similar on Synaptic (I use Kubuntu so I don't know the exact location). Select at least the top four, and select a location to download from.
You should also have a look at the updates tab.

---

### Post by billgoldberg on 2008-03-31
Restricted extras is a pretty big package, on an old computer it can take some time.

Skype is in the medibuntu repo, you'll want that repo and some of it's apps[URL="http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/"].

LINK[/URL]

---

### Post by fela on 2008-03-31
@ Sandro Batelli

to install skype from repositories, you have to enable a third party repository called medibuntu.

---

### Post by Sandro Batelli on 2008-03-31
I did enable the first 4 in software sources and selected the location, I was then able to update and download the restricted extras. It is taking a long time now to install the downloaded software. Is that normal?

---

### Post by fela on 2008-03-31
sometimes when installing upgrades/more software using apt-get or aptitude, a process called 'scrollkeeper-update' happens to use all the cpu time while installing the software, cause of some nasty bug. When this happens, although occasional, it can make it take minutes to complete even on a very fast machine, or hours on a less high end computer.

---

### Post by forrestcupp on 2008-03-31
Skype isn't in the normal repositories that we have available to enable.  You need to add the medibuntu repos to get skype this way.

Check out [this post](http://ubuntuforums.org/showpost.php?p=4490074&postcount=3) to find out how to add the medibuntu repos and install skype.

---

### Post by Sandro Batelli on 2008-03-31
Thanks again guys!
Great support.
I guess I'll let my old laptop keep installing and go for dinner!

---

### Post by Sandro Batelli on 2008-04-01
Hi again,
1) I let my laptop installing restricted extras for almost 12 hours but hasn't finished yet! It is still reconfiguring packages.

2) Another window (c below) popped up:do I need it?
"Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.

The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required".

3) Can I enable  Medibuntu repos while the computer is still installing the extras or shall I wait? 
Thx!
Thx!

---

### Post by ramjet_1953 on 2008-04-01
What is your Internet connection?

is it Dial-up, or ADSL?

If you are using a dial-up connection, I'm not surprised that things are taking so long.

Regards,
Roger :cool:

---

### Post by .nedberg on 2008-04-01
The install will not finish as long as you do not click ok in the pop-up window.

You can add the repositories now, but I advise you to wait

---

### Post by forrestcupp on 2008-04-01
> **.nedberg said:**
> The install will not finish as long as you do not click ok in the pop-up window.

You can add the repositories now, but I advise you to wait

Lol.  That's exactly what I was thinking.  The same thing happens with other non-free software like Java that asks you to accept their license.  Until you click the window, it will just hang there forever.

---

### Post by Sandro Batelli on 2008-04-01
Hi again,
there is no pop-up window on the applying changes/installing software window. It doesn't allow me to close the window either. Shall I turn the computer off and try again?
Thx!!

---

### Post by Sandro Batelli on 2008-04-02
Hi guys,
i was able to install ubuntu extras and some softwares. At some point one of this installation I got this notification in terminal: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
How do I run it manually?
is it because of this that I can't install software for DVD?
Thanx!

---

### Post by kellemes on 2008-04-02
> **Sandro Batelli said:**
> Hi guys,
i was able to install ubuntu extras and some softwares. At some point one of this installation I got this notification in terminal: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
How do I run it manually?
is it because of this that I can't install software for DVD?
Thanx!

Just open a terminal window and type..
```
sudo dpkg --configure -a
```

---

