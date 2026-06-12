---
title: "How do I get WMV's to play?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-11-12
Yes, I know there are a dozen topics or so talkiing about this, and more than a few How To's.  However, I've tried everyone I could get my hands on, and have only came away with a system cluttered with non-working programs (mplayer crashed and wouldn't run, Xine crashes when triyng to play a file, Totem still can't play them).  I've also tried downloading and installing the codecs to no avail.  Can someone give me a hand?  This is very frustrating, as I'm doing everything each one of these walkthroughs suggests, but nothing happens...

---

### Post by apjone on 2005-11-12
goto synaptic and search for gstreamer - install what you need , wmv's work with my totem and mplayer & mplayer firefox pluggin

---

### Post by Animus on 2005-11-12
When I open synaptic, I get the following error:

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Animus on 2005-11-12
Alright, I went ahead and installed gstreamer.  Now when I go to open my WMV files with totem, they just run through the entire time in about 1 second, without ever playing anything, and having a black screen.

---

### Post by Animus on 2005-11-12
I'm getting this error msg whenever I try to install or update anything, could someone tell me what it is?

This is from me typing sudo apt-get update:

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


This is from me trying to install Xine:

W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xine has no installation candidate


And I get many more, varied errors when trying to install other programs.  Anyone have a thought or two about this?

---

### Post by SSTwinrova on 2005-11-12
My guess is that there's something wrong with the Apt repo on  [http://antesis.freecontrib.org](http://antesis.freecontrib.org) -- is there any specific reason why you have that in there instead of only using the official Ubuntu ones?

---

### Post by Animus on 2005-11-12
bump

---

### Post by CyiPherX on 2005-11-12
Try this-


In terminal "sudo gedit /etc/apt/sources.list"

Then copy the text below OVER your existing list.(This is for the Breezy 5.10 version).

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 


Once you have done that save the file , then go into the package manager and go to the settings section, then repositories, and then click the "setting" button and make sure that "show disabled software sources" is ticked.

Click OK, then try seaching for your software.


For video codecs, download and install the following.

Libraries (multiverse) > gstreamer0.8-plugins-multiverse
Libraries (universe) > gstreamer0.8-plugins
Libraries (universe) > gstreamer0.8-ffmpeg
Libraries (universe) > gstreamer0.8-mad
Multimedia > vorbis-tools
Multimedia (multiverse) > lame
Multimedia (multiverse) > faad
Multimedia (multiverse) > gstreamer0.8-lame
Multimedia (universe) > sox
Graphics (multiverse) > mjpegtools
Graphics (universe) > ffmpeg
GNOME Desktop Enviroment (universe) > totem-xine


Then once they are all installed, register the G-Streamer in terminal by "gst-register-0.8"

After that install the w-32 codecs-

Install “xine-ui” in the package manager.

Launch Xine (or Totem) and try to play a video (this will create a .config file)

Download the codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the “essential codecs package”)

if the link above is temporarily down try this mirror:
[http://www4.mplayerhq.hu/homepage/design7/dload.html](http://www4.mplayerhq.hu/homepage/design7/dload.html)

Open the terminal and follow these steps:

a) Get to the directory where you have downloaded the file 

"cd /home/yourusername/yourfolder"

b) Create the directory in which you are going to put the codecs 

"sudo mkdir /usr/lib/win32"

c) Now, assuming the file you downloaded is “essential-20050412.tar.bz2”

"tar -xjf essential-20050412.tar.bz2" (this will extract the file)

"sudo mv essential-20050412/* /usr/lib/win32" (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!

I did all this yesterday, having just done a clean install, and it worked pefectly.

CyiPherX:)

---

### Post by darkblue1893 on 2005-11-13
I also had a problem getting wmv files to play and seem to have tried most of the above, none of which seemed to work. The main problem involved wmv files as embedded video files on websites.

Finally got them to play by installing Automatix and choosing all the multimedia options.

this is the link for it [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


It works with Firefox, but i am still gettin a grey screen with OPera.

---

### Post by Animus on 2005-11-13
Well, I tried following your instructions exactly.  I had most of the plugins, but I reinstalled them anyway, just to make sure.  Neither Xine nor Totem work however when asked to play WMV's, they still tell me the file is encrypted.  This is really getting annoying, as no one else seems to be having this much trouble getting them to play properly...

---

### Post by Animus on 2005-11-13
Thanks, but I already tried the automatix media filed with no effect.  i also installed Easy Ubuntu, with no luck.

---

### Post by joergenlie on 2005-11-25
Hi!
I've followed the steps listed above and this works almost fine with my Dell desktop but on my compaq presario 1400 notebook I only get sound and the colors pink and pbue in mixed stripes at the video screen. This problem only occurs when playing media from websites using wmv. The odd thing is that ican play wmv's from my harddrive?

The only issue I have with my dell is that some tv programs that i want to view have been cut down to pieces so you don't have to watch the entire program, but my players will only allow me to see the entire program from the beginning of it. :confused: 

I use firefox 1.5 RC3 with mediaconnectivity plugin.

Anyone solved these problems? This is the only thing preventing me from deleting my XP partition.

Jørgen

---

### Post by polo_step on 2005-11-25
I never had any luck with WMVs either, though I tried a whole load of suggestions.  Multimedia in almost any format has been a headache to get right, at least in 5.04.  Poor A/V synch even in formats that worked finally did it for me and I went back to XP for videos.

---

