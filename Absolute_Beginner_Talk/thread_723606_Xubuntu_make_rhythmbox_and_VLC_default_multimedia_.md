---
title: "Xubuntu make rhythmbox and VLC default multimedia programs"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by nickpaton on 2008-03-13
I have Xubuntu 7.10 installed.

Currently inserting a music CD or DVD film causes Totem to run by default.

However I want Rhythm box to run music CD's by default and VLC for DVD's.

In Ubuntu this is straightforward to do by the usual methods, however since Xubuntu is stripped down, the options are far less.

For instance right clicking on a CD or DVD and properties only shows  the name of the file as being audio CD or DVD with no other useable options.

I decided to Look within 

```
gksu mousepad /etc/gnome/defaults.list
```

(mousepad is like gedit in ubuntu) and changed all references to totem audio to rhythmbox, and for totem video to VLC.

These packages now work by default for all audio and video codecs but still not when running a CD or DVD.

Where is the file located to change the default totem settings to rhythmbox and VLC respectively?

Or has anyone any suggestions?

Many thanks in advance.

Nick

---

### Post by dokdoom on 2008-03-13
I am not familiar with Rhthym Box but can you run it and open the file from there? That might make Rhthym Box appear under the open with section (tab or w/e).

---

### Post by nickpaton on 2008-03-13
Yes I can open Rhythmbox and VLC and run the cd's dvd's from within them, but I would like them to automatically open when a CD or DVD is inserted.

I cannot make either program do this and need to modify a file somewhere to remove totem and replace with rhythmbox and VLC respectively.

---

### Post by nickpaton on 2008-03-13
Note that typically this:

[http://ubuntuforums.org/showthread.php?t=703870#4]("http://ubuntuforums.org/showthread.php?t=703870#4")

because in Xubuntu, System > Preferences > Removeable Drives and Media dows not exist as an option.

---

### Post by nickpaton on 2008-03-14
Can anyone help?

---

### Post by linux phreak on 2008-03-15
Hi.If you want to make Rhythmbox the default for mp3,just right click on the file then select properties at the bottom.There is an option 'Open with'.Choose Rhythm box/VLC as default.Now mp3s will be opened in either of these. Or choose 'open with other'.Choose VLC/Ryh box.
TO configure removable media,open Thunar the select edit>preferences>Advanced.Then under volume management click the 'configure'.

---

### Post by nickpaton on 2008-03-18
@ Linux Phreak - many thanks for that.  I'll be installing Xubuntu on another  PC in the next week and will try this.

If / when I find it works, I'll mark as SOLVED.

Nick

---

### Post by RJ Hythloday on 2008-03-18
> **nickpaton said:**
> @ Linux Phreak - many thanks for that. I'll be installing Xubuntu on another PC in the next week and will try this.
 
If / when I find it works, I'll mark as SOLVED.
 
Nick
did you have any problems getting the codec installed? in Kubuntu amarok installed the codec for me, totem just told me it wasn't installed. I searched here and did ```
sudo apt-get install ubuntu-restricted-extras

``` and I had to do a restart any way since I had done update/upgrade, but mp3's you tube etc still don't work. Flash finally works though after installing from the adobe site, the nonfree in the repos didn't work.

---

### Post by Bubba64 on 2008-03-19
You can also use the Firefox edit preference content and click on configure how Firefox handles certain types of files, for your online playing.

---

### Post by nickpaton on 2008-03-19
> **RJ Hythloday said:**
> did you have any problems getting the codec installed? in Kubuntu amarok installed the codec for me, totem just told me it wasn't installed. I searched here and did ```
sudo apt-get install ubuntu-restricted-extras

``` and I had to do a restart any way since I had done update/upgrade, but mp3's you tube etc still don't work. Flash finally works though after installing from the adobe site, the nonfree in the repos didn't work.

For all flavours of ubuntu, add medibuntu to the repos.
When you do the apt-get update, if medibuntu is not upgraded, change where you download from via System > Administration > Software Sources > Ubuntu Software tab and change 'Download from' to another source.

(Xubuntu is slightly different but don't have a working PC with it on to give the instructions)

Also check within the repos that nonfree is not '#-ed' out.

---

### Post by RJ Hythloday on 2008-03-19
I finally decided to follow my own advice

[URL="https://help.ubuntu.com/community/RestrictedFormats/MP3"][LIST]
[*] Open Amarok and play an mp3 file. Amarok will ask you if you would like to add mp3 support and then install the **libxine1-ffmpeg** package.
[*] To play mp3's with Amarok, install the package **libxine1-ffmpeg** (which will install **libmad0** as well).[/LIST][/URL]

I'm still not getting any mp3 output! every time I do a sudo-apt get it says 0 installed 0 updated already newest version. **What am I doing wrong?**

---

### Post by nickpaton on 2008-04-09
RJ - sorry only just got back to this thread.

Don't know the exact solution to your mp3 problem, but couple of ideas - what happens if you try & play then with another player?

Secondly have a look at [this post]("http://ubuntuforums.org/showthread.php?t=513058#7") which may help you.

Re the original problem I had with making Rythmbox and VLC default players, I have Rhythmbox working but VLC is still not detected as the default DVD player despite trying every switch under the sun!

Cant yet mark as solved.....:(

---

