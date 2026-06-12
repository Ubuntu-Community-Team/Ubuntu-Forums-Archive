---
title: "MAJOR DVD playback problems!"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by IHeartLinux on 2007-03-09
I have done everything I can possibly think of to get dvd playback working, to no avail.

I am running Ubuntu 6.06 on an IBM Thinkpad T30.

I have downloaded every codec imaginable, and tried as many programs as possible, and none of them work right.

Totem: Tries to play.  Gives me the "Are you sure libdvdcss is installed?" message during the menus.
MPlayer: Flashes a window for about half a second, then does nothing.
Xine: Tries to play.  Gives me the "Error reading NAV packet" message during the menus.
VLC: Doesn't do ANYTHING.  Not even a video window.
gxine: Tries to play.  Locks up so I have to force quit.
Ogle: Plays sound, but not video.
Kaffeine: Tries to play.  Gives me the "Error reading NAV packet" message during the menus.

Urghhh...I've been trying to get this to work for almost a week!

---

### Post by overdrank on 2007-03-09
> **IHeartLinux said:**
> I have done everything I can possibly think of to get dvd playback working, to no avail.

I am running Ubuntu 6.06 on an IBM Thinkpad T30.

I have downloaded every codec imaginable, and tried as many programs as possible, and none of them work right.

Totem: Tries to play.  Gives me the "Are you sure libdvdcss is installed?" message during the menus.
MPlayer: Flashes a window for about half a second, then does nothing.
Xine: Tries to play.  Gives me the "Error reading NAV packet" message during the menus.
VLC: Doesn't do ANYTHING.  Not even a video window.
gxine: Tries to play.  Locks up so I have to force quit.
Ogle: Plays sound, but not video.
Kaffeine: Tries to play.  Gives me the "Error reading NAV packet" message during the menus.

Urghhh...I've been trying to get this to work for almost a week!

Hi I feel you pain in the issue. This is what I do to get the video and sound to work. 
Install Vlc, flash,and  codecs from automatix, This has worked for me on dapper and edgy. Hope this is some help. Good luck!

---

### Post by taurus on 2007-03-09
Have you seen this?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by IHeartLinux on 2007-03-09
taurus: Yes, I have seen that page, and it has not helped during any of the last 2103809832098  times I've visited it.

paul capps: Automatix isn't working right now.  Their site got hacked and deleted the other day.

As a last-ditch effort, I'm trying EasyUbuntu, and if this doesn't work I think I'm gonna have a stroke.  This is SO frustrating!

---

### Post by igknighted on 2007-03-09
> **IHeartLinux said:**
> taurus: Yes, I have seen that page, and it has not helped during any of the last 2103809832098  times I've visited it.

paul capps: Automatix isn't working right now.  Their site got hacked and deleted the other day.

As a last-ditch effort, I'm trying EasyUbuntu, and if this doesn't work I think I'm gonna have a stroke.  This is SO frustrating!

I heard a rumor automatix was back up today... in fact after checking the site I know it is

---

### Post by IHeartLinux on 2007-03-09
igknighted: The Automatix home page is back up but when I click on the download link I get a message saying that the server is busy.

EasyUbuntu has, not surprisingly, failed to resolve any of my DVD playback issues.  I'm beginning to think that this whole playing-DVD's-in-Linux thing is more trouble than it's worth.  I now have a massive headache.

---

### Post by panch0 on 2007-03-12
Is it just one DVD or any DVD?

If you run

mplayerm -vo xv dvd://

from the command line, what output do you get? Post it here.

---

### Post by IHeartLinux on 2007-03-19
panch0:

I ran that from the command line and it said
bash: mplayerm: command not found

OMG WTF BBQ

---

### Post by DoorGunner on 2007-03-19
actually I think does work. Here is how i got it to go.

go to here [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)
(this is a link from the site taurus provided)


download the libdvdcss2_1.2.5-1_i386.deb  (it is hard to read the listing ...be carefull)
and save it to Desktop (If you are have a 64bit machine use the 64bit version instead of the i386)

> 
sudo dpkg -i ~/Desktop/libdvdcss2_1.2.1-1_i386.deb

I have Xine and totem and they now work fantastic..... Thanks Taurus!!!

---

### Post by IHeartLinux on 2007-03-19
DoorGunner: Nope.  Tried it.  Still doing the same thing.

---

### Post by DoorGunner on 2007-03-20
Sorry IHeartLinux..... I am running Feisty not Dapper......

Im not sure what you have tried all together. I did see this on the Dapper Wiki.
You have probably tried  that as well.

sudo apt-get install libdvdread3
sudo apt-get install dpkg-dev fakeroot debhelper # If you have AMD64.  You need dpkg-source.  Otherwise skip.
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install totem-xine

It seems to me it may be a problem of getting the codec to the devices. You may need to look at an experiment by placing the codec (dynamic links with ln -s) into the plugin or codec portions of the Media players handraulicly. If the libdvdcss2_1.2.5-1_i386.deb didnt work for me that would have been my next step. 

I would try that with the libdvdcss2 codex though. They seem to work.

---

### Post by IHeartLinux on 2007-03-21
DoorGunner: You might as well be speaking Esperanto, cos I don't understand a word of what you just said in that last paragraph.  Dynamic links?  I'm so clueless...^_^

---

### Post by fenian on 2007-03-21
Open the synaptic package manager (system>administration>synaptic package manager) in the window that opens find the settings menu click it and go to repositories check universe,multiverse and restricted close the settings window and click the reload button on the upper left.Click the search button and type libdvdread3 in the box..The libdvdread3 package should then be listed check he box and click the apply button after it installs close synaptic and type the following in a terminal window...

> sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by DoorGunner on 2007-03-21
dynamic links are a way of keeping a file in one location and being able to use them in another. its kind of like a telephone. You can talk with a person in a remote location with out being there. 

you would do that with a code similar to this

ln -s /path/of/origional/file  /path/to/clone/

---

### Post by jim12 on 2007-03-24
I think this might not be helpful to you but...
I also have a T30 and just tonight installed ubuntu from a CD I got with an book. DVD playback did not work at first. I found this forum and this thread. I followed Taurus's link to the RestrictedFromats page, and followed the instructions there. Namely the libdvdcss2 package (my first download had an error, I eventually picked the package libdvdcss2_1.2.5.1_i386.deb) and also the additional windows codecs, w32codecs_20061022-0.0_i386.deb. 

Still Totem would not play the dvd. So I installed Ogle from the add/remove programs list. And, it worked!!! I have played both a copied DVD (which I think my uncle removes the region coding) and also a movie from blockbuster. All pretty good so far.

I empathize with you and I do hope your DVD problems will resolve themselves soon. 

All the best,

jim

---

### Post by euler_fan on 2007-03-24
[VLC on Ubuntu]("http://www.videolan.org/vlc/download-ubuntu.html")


I hate to put it this way, but there is no reason to re-invent the wheel . . .

Visit the link above and try that. The VLC in the repos is very old for your distro (6.06) and the instructions provided should work.

---

### Post by IHeartLinux on 2007-03-25
SQUEEEEEEEEE!

euler_fan: Your advice worked perfectly, as does my DVD playback in VLC now.  You rock.

Chocolate covered espresso beans to everyone who tried to help!

Thanks a bunch!

---

### Post by Steve H on 2007-04-22
> **taurus said:**
> Have you seen this?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks for that, it worked beautifully for me. But i did have to restart the desktop for it to do it. Mplayer is still a bit dodgy with DVD´s but VLC works fine.

Thanks again

---

