---
title: "My first time..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Win2Mac2Linux on 2007-01-14
Hello to all!!!  I am a long time Windows user, tried Mac OSX for the past year (believe it or not, VERY disappointed.  A number of problems with the system locking up, etc.), and now I'm trying Ubuntu.  I have heard so much about Linux (esp. Ubuntu being so popular it seems) and thought i would give it a try.  I am experienced from an end user standpoint, but when things start getting really technical, I might start panicking.  I am eager to dive into the Linux world and see what it is all about.  My background is healthcare so...
I am writing this simply to say "hello" and to document my first experience with Linux (Ubuntu).  Overall, pretty good, but some problems.  I know I have a bit to learn to correct them, but you have to start somewhere.  
I have an Apple Aluminum Powerbook G4 (v5.9).  I installed Ubuntu 6.10 (Edgy?) and wiped out OSX.  I was very excited that my wired connection was working so I installed all the updates (92 of them).  My initial "bumps" in the road are: 
1.) DVD won't play.  I get the message   "Totem could not play 'dvd:///media/cdrom0' "
                   No URI handler implemented for "dvd"
      Music CD plays fine though...

2.)Pointer moves VERY slowly with trackpad (even though I set acceleration to 100%).  "Tapping" function on trackpad doesn't work.  It kills me to have to move my finger across the trackpad 20 times to move all the way across the screen.

3.)Wireless doesn't work (Broadcom BCM 4318).  I believe I set it up correctly by activating it and entering the Essid (I'm assuming that is the same as SSID), but still nothing.  

That's it for now.  I'm not necessarily looking for answers (although I would ignore them if they are posted), but rather to comment my first experiences.  I figure I'll have to post each problem in the appropriate forum.  From what I can tell, the first thing i need to do is become familiar with "terminal" (flashback to DOS days...) and how to install tar.gz files.  I tried a little, but realize I don't quite get it yet.  

So as not to make this post any longer, thank you to those that read this and I look forward to
evolving into a newbie (right now I consider myself less than a Linux newbie).  Any suggestions on a good book for a newbie to learn the Linux basics would be appreciated.  I don't have the time or inclination to get into hardcore programming, but I am willing to learn whatever is necessary to be able to complete the basic tasks.  Thanks again.  

P.S.  I just have to add here (from something I read in another post) that I hope Ubuntu always supports the PPC platform.  I would hate to get all into this and then down the road find out PPC isn't supported anymore.  Just my "I'm nobody" 2cents worth...

---

### Post by aysiu on 2007-01-14
You may find this link helpful:
[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/)

---

### Post by Sef on 2007-01-14
> P.S. I just have to add here (from something I read in another post) that I hope Ubuntu always supports the PPC platform. I would hate to get all into this and then down the road find out PPC isn't supported anymore. Just my "I'm nobody" 2cents worth...

My feeling is that the PPC platform will be supported for 5-10 years.   Maybe longer if there are others who are using that chip (other than sony's playstation.)

---

### Post by riven0 on 2007-01-14
For your wireless card; have you tried [this howto]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM+4318") get it working? I believe you need the ndiswrapper. 

For DVD's, make sure the universal and commercial repositories are enabled. Then try this in the terminal:

> sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh

If it still doesn't work, try using VLC. Sometimes Totem gives problems...

---

### Post by Win2Mac2Linux on 2007-01-14
aysiu:  thank you for your link.  I check it out and I'm trying to do the suggestions for the trackpad.  My goal is to get that fixed first, then the wireless.  However, I'm having trouble finding where the "Input Device" part is that needs to be changed.  I first checked the using Device Manager, but that didn't seem to be it.  Then I tried looking around using "Computer", but seemed a little lost there also.  I admit I'm cheating here a little bit asking for help early on, but I'm just looking for help to get the basics set up and running, then I'll start digging deeper on my own.  I can't believe how quick I got a response to my post.  Thanks again.  Time to jump back to that link and keep plugging away!!!

Sef:  thanks for the feedback.  I was reading on one of the posts about concern that the PPC platform might only be supported in the short run.  That would be a shame considering how many coputers are out there using the PPC.  I hope you are right.  I would love to learn and use Linux on my Powerbook for years to come.  Maybe eventually I'll put it on my desktop (currently WinXP Pro) someday.

---

### Post by aysiu on 2007-01-14
That's in a file called /etc/X11/xorg.conf

Press Alt-F2 and type ```
gksudo nautilus
``` This will open the file browser as root, allowing you to make system-wide changes. Go to the /etc/X11 folder and make a back up copy of (and then edit) the xorg.conf file.

I can't stress enough that you should make a backup copy of it first.

If you somehow mess it up and are at only a command-line, log in and type (assuming your backup copy is named xorg.conf.backup) ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` The terminal is case-sensitive.

---

### Post by jimrz on 2007-01-14
> **Win2Mac2Linux said:**
> aysiu:  thank you for your link.  I check it out and I'm trying to do the suggestions for the trackpad.  My goal is to get that fixed first, then the wireless.  However, I'm having trouble finding where the "Input Device" part is that needs to be changed.  I first checked the using Device Manager, but that didn't seem to be it.  Then I tried looking around using "Computer", but seemed a little lost there also.  I admit I'm cheating here a little bit asking for help early on, but I'm just looking for help to get the basics set up and running, then I'll start digging deeper on my own.  I can't believe how quick I got a response to my post.  Thanks again.  Time to jump back to that link and keep plugging away!!!

Sef:  thanks for the feedback.  I was reading on one of the posts about concern that the PPC platform might only be supported in the short run.  That would be a shame considering how many coputers are out there using the PPC.  I hope you are right.  I would love to learn and use Linux on my Powerbook for years to come.  Maybe eventually I'll put it on my desktop (currently WinXP Pro) someday.

don't think that there is a gui for what you need... the "input device" section you are looking for is in the config file /etc/X11/xorg.conf... to edit go to Terminal then:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak
```



ALWAYS a good idea to backup your conf files, then

```
sudo gedit /etc/X11/xorg.conf
```

this will give you su priviledges in the gedit text editor and open the file for you to implement the changes from aysiu's link

EDIT: shoulda known ay would be too fast for me ;-)

---

### Post by aysiu on 2007-01-14
If you're going to give the terminal route, this one command will both back up your xorg file *and* allow you to edit it: ```
sudo nano -B /etc/X11/xorg.conf
``` Of course, it's probably better to edit it graphically, since you're cutting and pasting in text...

---

### Post by Win2Mac2Linux on 2007-01-14
I get the message  "Failed to run nautilus as user root."

"The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator."

One of the things that confused me earlier ( I did a restart) was a message came up saying I couldn't login as "root" from the regular startup screen when I tried to login as "root".  I figured I would try and start off as "root" and take it from there.  I could only login under my normal user name.  Thanks for the help.  Sorry if I'm looking a little stupid here.  As things have been explained they seem pretty straight forward (thank goodness I have the "cut and paste" thing down).  I'm just trying to figure out what I'm missing and why this "root" thing has become a problem.  One thing...when I first installed the OS I was never asked to setup an administrator password.  Earlier I was doing something (I forget exactly what) that asked for a "root" password.  I just entered my regular account password and that worked.  Anyway, just trying to mention as much as possible to hopefully help.  Thanks.

P.S.  I will eventually get back to everyone (thanks to everyone for being so helpful).  It's late and i can only handle one message/problem at a time.   ;)

---

### Post by Win2Mac2Linux on 2007-01-14
> **aysiu said:**
> That's in a file called /etc/X11/xorg.conf

Press Alt-F2 and type ```
gksudo nautilus
``` This will open the file browser as root, allowing you to make system-wide changes. Go to the /etc/X11 folder and make a back up copy of (and then edit) the xorg.conf file.

I can't stress enough that you should make a backup copy of it first.

If you somehow mess it up and are at only a command-line, log in and type (assuming your backup copy is named xorg.conf.backup) ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` The terminal is case-sensitive.


Sorry, my last post was regarding the above...

---

### Post by Win2Mac2Linux on 2007-01-14
I just found a "HowTo" regarding logging in as "root" in the initial graphical startup.  However, when I go to the Users and Groups section, I get the message
"The configuration could not be loaded"
You are not allowed to access the system configuration.

I can't login the beginning as root and I can't access the Users and Groups section to change the properties.  I'm guessing I screwed something up somewhere...

Mabye I should go to sleep now before I unknowingly do something else wrong.  Hopefully with everyones (wonderful) help here I will sort it out tomorrow.  Thanks again.

---

### Post by jimrz on 2007-01-14
> **Win2Mac2Linux said:**
> Sorry, my last post was regarding the above...

are you sure you did [COLOR="Red"]gksudo[/COLOR] and not just sudo from the Terminal, it should work.  not sure why it would not but, if not you can use what i posted above to acheive the same ends (just a bit more cli though).

---

### Post by Win2Mac2Linux on 2007-01-14
> **jimrz said:**
> are you sure you did [COLOR="Red"]gksudo[/COLOR] and not just sudo from the Terminal, it should work.  not sure why it would not but, if not you can use what i posted above to acheive the same ends (just a bit more cli though).

I did it using the "Alt-F2" method (graphical?).  I guess I'll try using terminal...

Thanks.

---

### Post by Delkster on 2007-01-14
> **Win2Mac2Linux said:**
> I just found a "HowTo" regarding logging in as "root" in the initial graphical startup.

Not asking for a root password (and thus disabling root login) is purposeful. Instead of logging in as root to do administration, the default setup of Ubuntu is to use [sudo](http://wiki.ubuntu.com/RootSudo).

Unless you specifically want to have an enabled root account for some reason, it's probably a good idea to leave it disabled and stick with sudo. It works quite nicely, and you won't have to remember yet another password for the root account.

---

### Post by Win2Mac2Linux on 2007-01-15
> **aysiu said:**
> You may find this link helpful:
[http://joona.kuori.org/ubuntu-powerbook/](http://joona.kuori.org/ubuntu-powerbook/)
Thanks again.  I finally edited the x11 file and the trackpad is now working much better.  I know it sounds silly, but having learned this little bit for me and getting the trackpad up and running was a little exciting for me.  The wireless thing is another story...

---

### Post by Win2Mac2Linux on 2007-01-15
> **riven0 said:**
> For your wireless card; have you tried [this howto]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM+4318") get it working? I believe you need the ndiswrapper. 

For DVD's, make sure the universal and commercial repositories are enabled. Then try this in the terminal:



If it still doesn't work, try using VLC. Sometimes Totem gives problems...
Followed the steps for wireless.  Wasn't working after running script so I rebooted.  I noticed under "networking" that the wireless option was no longer there.  PreviouslyI had tried to get the wireless working by entering in the ESSID and key for the connection (and checked the box to activate it), but it still wasn't working.  I'm really confused now that the wireless option under "networking" is no longer there.  Any suggestions?  Once I get the wireless going I promise to dig deeper on my own and learn about other stuff.  On a side note, I came across two html files of Ubuntu books that I can read on my  Windows desktop, but won't open on this laptop.  I tried doing a search for "reading html files with linux", but nothing useful (as far as I can tell) came up.  Thanks for your patience and any help you can provide.

P.S. I'm using WPA (AES?) on my home wireless network.  Are there limitations on the security capabilities with wireless cards and linux?

---

### Post by Win2Mac2Linux on 2007-01-15
Forgot to ask about the line below:

<<make sure the universal and commercial repositories are enabled>>

Don't know what they are and what that means.  Thanks.

---

### Post by aysiu on 2007-01-15
> **Win2Mac2Linux said:**
> Forgot to ask about the line below:

<<make sure the universal and commercial repositories are enabled>>

Don't know what they are and what that means.  Thanks.
It means follow [these instructions](http://www.psychocats.net/ubuntu/sources)

---

### Post by chaplanger on 2007-01-15
For DVD playback -- install automatix -- it will put int the proper codecs.  You will find this in the Synaptic Package Manager.  System>Administration>Synaptic Package Manager.  Use the search function and in the field type in automatix and then choose and install automatix2.

---

### Post by Win2Mac2Linux on 2007-01-16
> **chaplanger said:**
> For DVD playback -- install automatix -- it will put int the proper codecs.  You will find this in the Synaptic Package Manager.  System>Administration>Synaptic Package Manager.  Use the search function and in the field type in automatix and then choose and install automatix2.
Thank you for the help.  It appeared to be pretty straightforward, but I don't know if I'm doing something wrong.  I opened the Synaptic Package Manager, did the search.  It showed the name in the left hand column, but nothing on the right.  I'm guessing for some reason it's not there or am I doing something wrong?  I searched under "All" so I figure I'm searching everything, but still nothing.  Any help to point me in the right direction would be appreciated.  Thanks again.

---

### Post by riven0 on 2007-01-16
The thing with Synaptic is that the program names sometimes don't make sense. Like libvdcss. How are we supposed to know that's a dvd codec? So it takes a lot of searching to get the right results.

In either case, try this in the terminal and see if it works:
> 
sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh


---

### Post by Win2Mac2Linux on 2007-01-16
> **riven0 said:**
> The thing with Synaptic is that the program names sometimes don't make sense. Like libvdcss. How are we supposed to know that's a dvd codec? So it takes a lot of searching to get the right results.

In either case, try this in the terminal and see if it works:
I did what you suggested and after entering the password got this back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

Thoughts?  Thanks for your help.

P.S. I have two Ubuntu books in HTML format.  How do you read HTML files with linux?  I Google'd it, but nothging worthwhile came up.  I could just read them on my (Windows) desktop, but I want to put them on this laptop and start reading up on Ubuntu...

---

### Post by riven0 on 2007-01-16
> **Win2Mac2Linux said:**
> I did what you suggested and after entering the password got this back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3



Are your repositories enabled? Try this: open Synaptic Package Manager >> Settings >> Repositores. Now make sure everything under the header Internet is checked. Then Reload , close Synaptic and try again through the terminal. 

Usually this should work, but if it doesn't, open your sources.list: **sudo gedit /etc/apt/sources.list** and paste the contents here.

---

### Post by Win2Mac2Linux on 2007-01-16
> **riven0 said:**
> Are your repositories enabled? Try this: open Synaptic Package Manager >> Settings >> Repositores. Now make sure everything under the header Internet is checked. Then Reload , close Synaptic and try again through the terminal. 

Usually this should work, but if it doesn't, open your sources.list: **sudo gedit /etc/apt/sources.list** and paste the contents here.

I did what you said and it seemed to go ok, but when searched again under the Synaptics Package  Manager for "automatix", still nothing came up on the right hand upper box.  I've included below the results of the command you told me to run (even though it seemed to work) and the results of the sources.list

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libdvdcss2
The following NEW packages will be installed:
  libdvdread3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.3kB of archives.
After unpacking 201kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe libdvdread3 0.9.6-3ubuntu1 [59.3kB]
Fetched 59.3kB in 0s (88.4kB/s)
Selecting previously deselected package libdvdread3.
(Reading database ... 91977 files and directories currently installed.)
Unpacking libdvdread3 (from .../libdvdread3_0.9.6-3ubuntu1_powerpc.deb) ...
Setting up libdvdread3 (0.9.6-3ubuntu1) ...

--01:58:51--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_powerpc.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_powerpc.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,760 (27K) [text/plain]

100%[====================================>] 27,760        73.02K/s             

01:58:52 (72.92 KB/s) - `/tmp/libdvdcss.deb' saved [27760/27760]

Selecting previously deselected package libdvdcss2.
(Reading database ... 91986 files and directories currently installed.)
Unpacking libdvdcss2 (from /tmp/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.5-1) ...


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


I'm not sure if this has anything to do with whether or not Totem should function properly, but I still get the "No URI handler implemented for DVD" message...

Thanks.

---

### Post by Delkster on 2007-01-16
> **riven0 said:**
> The thing with Synaptic is that the program names sometimes don't make sense. Like libvdcss. How are we supposed to know that's a dvd codec? So it takes a lot of searching to get the right results.

Well, to be exact, it isn't a codec. It's a library that provides functions for operating with (or getting around) the Content Scramble System that's used to encrypt DVDs.

It's true, though, that the package names are a bit developer-oriented. That's probably one reason why there's Add/Remove Applications (a.k.a. gnome-app-install) which gives the packages (or applications) more humane names. Synaptic should be the "advanced" mode, not the primary source for finding software. (Not to mention that libdvdcss isn't available in Synaptic in a default Ubuntu setup because Ubuntu doesn't distribute that package.) Obviously Add/Remove Applications and other means of finding and obtaining software still need improvement.

---

### Post by Delkster on 2007-01-16
> **Win2Mac2Linux said:**
> I'm not sure if this has anything to do with whether or not Totem should function properly, but I still get the "No URI handler implemented for DVD" message...

Totem comes in two flavours: one has been compiled to use the gstreamer multimedia framework for playback functions and the other uses the xine engine for that purpose. They differ a little in their capability of playing different audio and, in particular, video formats.

Ubuntu has the gstreamer version installed by default, but Xine is generally better at DVD playback than gstreamer. If you haven't tried that yet, you may want to try replacing the totem-gstreamer package with totem-xine. Open Synaptic, search for "totem" and mark totem-xine for installation. Totem-gstreamer should be automatically marked for removal. Apply the changes and try again (remember to restart Totem).

---

### Post by Win2Mac2Linux on 2007-01-16
[QUOTE=Delkster;2021571]Totem comes in two flavours: one has been compiled to use the gstreamer multimedia framework for playback functions and the other uses the xine engine for that purpose. They differ a little in their capability of playing different audio and, in particular, video formats.

Ubuntu has the gstreamer version installed by default, but Xine is generally better at DVD playback than gstreamer. If you haven't tried that yet, you may want to try replacing the totem-gstreamer package with totem-xine. Open Synaptic, search for "totem" and mark totem-xine for installation. Totem-gstreamer should be automatically marked for removal. Apply the changes and try again (remember to restart Totem).[/QUOTE

Works perfect!!  Thank you for your help!!!  :-D 

Now back to my wireless problems...

---

