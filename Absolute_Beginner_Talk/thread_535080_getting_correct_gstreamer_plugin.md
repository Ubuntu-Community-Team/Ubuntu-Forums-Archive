---
title: "getting correct gstreamer plugin?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-08-26
I am trying to get my sound to work. When I click the volume icon it gives me the pop-up that says I don't have the correct gstreamer plug-in installed. I am using the sound on the motherboard which is a biostar tforce tf520-a2 amd motherboard.

I checked out the repositories and added some extra gstreamer plug-ins thinking that those were correct but I have had no luck.

What do I need to install or configure to get the audio or video working?

---

### Post by InGunsWeTrust on 2007-08-26
Update to 7.04, A lot of hardware problems (like sound cards) were fixed in the new realase. 

```
sudo apt-get dist-upgrade
```

Then it can't hurt to have EXTRA plugins as all plugins are used so do

```
sudo apt-get install gstreamer*
```

---

### Post by chaddiesel on 2007-08-26
So, I need to type that into terminal so it will update.....Then run the second code to get the plugins to work?

---

### Post by InGunsWeTrust on 2007-08-26
Yes that would be correct the first line will upgrade you from Ubuntu 6.06 to Ubuntu 7.04 and the second will install all of the gstreamer plugins.

---

### Post by chaddiesel on 2007-08-26
Thanks for the help :guitar:

---

### Post by InGunsWeTrust on 2007-08-26
anytime! Just let me know if there are any problems with the upgrade process or gstreamer plugins and I'll do my best to help

---

### Post by chaddiesel on 2007-08-26
I tried to use the code for the upgrade and nothing really happened. It displayed this... 

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What do I do?

---

### Post by InGunsWeTrust on 2007-08-26
Then you probably already have Ubuntu 7.04 I just assumed that your signature meant you had 6.06 :-) just do the second line then haha

---

### Post by chaddiesel on 2007-08-26
cool.... I don't even know what I have.

This is what the second line displayed....

Reading package lists... Done
Building dependency tree... Done
Note, selecting gstreamer0.10-alsa for regex 'gstreamer*'
Note, selecting totem-gstreamer-firefox-plugin for regex 'gstreamer*'
Note, selecting gstreamer0.8-jpeg for regex 'gstreamer*'
Note, selecting libgstreamer0.8-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-audiosink for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-doc for regex 'gstreamer*'
Note, selecting gstreamer0.8-swfdec for regex 'gstreamer*'
Note, selecting libgstreamer0.8-0 for regex 'gstreamer*'
Note, selecting gstreamer-tools for regex 'gstreamer*'
Note, selecting gstreamer0.10-x for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-fluendo-mpegdemux for regex 'gstreamer*'
Note, selecting gstreamer0.8-festival for regex 'gstreamer*'
Note, selecting libgstreamer-plugins0.8-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-doc for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly for regex 'gstreamer*'
Note, selecting gstreamer0.10-colorspace for regex 'gstreamer*'
Note, selecting gstreamer0.8-hermes for regex 'gstreamer*'
Note, selecting gstreamer0.8-misc for regex 'gstreamer*'
Note, selecting libgstreamer-gconf0.8-0 for regex 'gstreamer*'
Note, selecting gstreamer0.8-ffmpeg for regex 'gstreamer*'
Note, selecting gstreamer0.8-theora for regex 'gstreamer*'
Note, selecting gstreamer0.8-gnomevfs for regex 'gstreamer*'
Note, selecting gstreamer0.8-wavpack for regex 'gstreamer*'
Note, selecting gstreamer0.8-misc instead of gstreamer0.8-wavpack
Note, selecting libgstreamer-gconf0.8-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse for regex 'gstreamer*'
Note, selecting gstreamer0.8-audiosink for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer0.8-plugin-apps for regex 'gstreamer*'
Note, selecting gstreamer0.8-doc for regex 'gstreamer*'
Note, selecting gstreamer0.8-dvd for regex 'gstreamer*'
Note, selecting gstreamer0.8-artsd for regex 'gstreamer*'
Note, selecting gstreamer0.8-esd for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good for regex 'gstreamer*'
Note, selecting gstreamer0.8-mikmod for regex 'gstreamer*'
Note, selecting gstreamer0.8-gsm for regex 'gstreamer*'
Note, selecting gstreamer0.8-gtk for regex 'gstreamer*'
Note, selecting gstreamer0.8-speex for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins for regex 'gstreamer*'
Note, selecting gstreamer0.8-mad for regex 'gstreamer*'
Note, selecting gstreamer0.8-caca for regex 'gstreamer*'
Note, selecting gstreamer0.8-mms for regex 'gstreamer*'
Note, selecting gstreamer0.8-a52dec for regex 'gstreamer*'
Note, selecting gstreamer0.8-oss for regex 'gstreamer*'
Note, selecting gstreamer0.8-alsa for regex 'gstreamer*'
Note, selecting gstreamer0.8-sdl for regex 'gstreamer*'
Note, selecting gstreamer0.8-cdio for regex 'gstreamer*'
Note, selecting gstreamer0.10-ffmpeg for regex 'gstreamer*'
Note, selecting gstreamer0.8-sid for regex 'gstreamer*'
Note, selecting gstreamer0.10-videosink for regex 'gstreamer*'
Note, selecting gstreamer0.8-audiofile for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-lame for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
Note, selecting gstreamer0.10-plugins-good-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-doc for regex 'gstreamer*'
Note, selecting gstreamer0.8-arts for regex 'gstreamer*'
Note, selecting gstreamer0.8-aa for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good-doc for regex 'gstreamer*'
Note, selecting gstreamer0.8-dv for regex 'gstreamer*'
Note, selecting gstreamer0.8-colorspace for regex 'gstreamer*'
Note, selecting totem-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad for regex 'gstreamer*'
Note, selecting gstreamer0.8-plugins for regex 'gstreamer*'
Note, selecting libgstreamer0.8-ruby for regex 'gstreamer*'
Note, selecting libgstreamer0.6-ruby for regex 'gstreamer*'
Note, selecting gstreamer0.10-doc for regex 'gstreamer*'
Note, selecting gstreamer0.8-flac for regex 'gstreamer*'
Note, selecting gstreamer0.10-fluendo-mp3 for regex 'gstreamer*'
Note, selecting gstreamer0.10-gl for regex 'gstreamer*'
Note, selecting gstreamer0.10-esd for regex 'gstreamer*'
Note, selecting gstreamer0.8-videosink for regex 'gstreamer*'
Note, selecting gstreamer0.8-tools for regex 'gstreamer*'
Note, selecting gstreamer0.8-x for regex 'gstreamer*'
Note, selecting gstreamer0.8-mpeg2dec for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-apps for regex 'gstreamer*'
Note, selecting libgstreamer-plugins0.8-0 for regex 'gstreamer*'
Note, selecting libgstreamer0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer-editor for regex 'gstreamer*'
Note, selecting gstreamer0.8-vorbis for regex 'gstreamer*'
Note, selecting gstreamer0.10-sdl for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnomevfs for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnonlin for regex 'gstreamer*'
Note, selecting gstreamer0.10-tools for regex 'gstreamer*'
Note, selecting gstreamer-plugins for regex 'gstreamer*'
Note, selecting gstreamer0.8-musepack for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.8-cdparanoia for regex 'gstreamer*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly-multiverse: Depends: liblame0 (>= 3.96.1-1) but it is not installable
E: Broken packages

---

### Post by InGunsWeTrust on 2007-08-26
Try

```
sudo apt-get install liblame0
```

If it doesn't work at least it will tell us why that dependency can't be satisfied

---

### Post by chaddiesel on 2007-08-26
This looks like a problem....

Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package liblame0 has no installation candidate

---

### Post by InGunsWeTrust on 2007-08-26
Visit this site

[http://packages.ubuntu.com/feisty/libs/liblame0](http://packages.ubuntu.com/feisty/libs/liblame0)

Download the package for your architecture (if you don't know what that is just download each one til one of them works). If you receive any error messages other than "wrong architecture" let me know.

If that works and you install that package try again with

```
sudo apt-get install gstreamer*
```

---

### Post by chaddiesel on 2007-08-26
ok, I got the gstreamer plugin to install....

Do I need to restart for it to work?

---

### Post by InGunsWeTrust on 2007-08-26
Nope, it should just work now. If it doesn't you could always try restarting it can't hurt!

---

### Post by chaddiesel on 2007-08-26
Also.... I used Dapper which is for 6.06.....

I wonder why it wouldn't upgrade to 7.04?

---

### Post by InGunsWeTrust on 2007-08-26
That is a very good question actually, but that is a whole extra topic, you'd have to open a new thread to get that one answered. But the sound works now right?

---

### Post by chaddiesel on 2007-08-26
Just got through restarting and there is still no sound and still the same error....

I used dapper.... and it had to errors in terminal, It claimed that it was done.

What do I do?

---

### Post by InGunsWeTrust on 2007-08-26
Are you saying that the install of the gstreamer plugins was sucessful and you still have no sound? Or are you saying there were errors in the install of gstreamer?

---

### Post by chaddiesel on 2007-08-26
I successfully installed gstreamer and I have no sound.

When I click the volume control it says that I don't have the plugin.

---

### Post by meborc on 2007-08-26
just a quick hint... if you do "sudo apt-get dist-upgrade" it will only upgrade to the latest version of files on the sources list file... you need to change all dapper to feisty in that file in order to upgrade, but it will probably give you headaches as you will be skipping a release (edgy)

read this how to dapper -> edgy [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
read this how to edgy -> feisty [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by InGunsWeTrust on 2007-08-26
Thanks to memborc for the tip but sorry to chadiesel I just don't know why it would give you an error message that obviously cannot be correct seeing as you have all of the gstreamer plugins. I'd say follow the tutorial on upgrading your distro and see if your hardware is better supported.

---

### Post by chaddiesel on 2007-08-26
I am dual booted on one drive with XP.

Will this upgrade affect what I have already setup?

---

### Post by InGunsWeTrust on 2007-08-26
No, the upgrade process will only update Ubuntu files such as the Linux kernel, Gnome Panel and other things of that nature. It should even leave all of the documents you have on Ubuntu intact.

---

