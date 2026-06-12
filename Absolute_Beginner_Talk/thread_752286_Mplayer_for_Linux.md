---
title: "Mplayer for Linux?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by spiritsongtress on 2008-04-11
Lots of people have told me to get Mplayer but I don't know how to get it. (I know it sounds silly) But Its not in Synaptic packages so I am at a loss and I can't figure out how to get it from the Mplayer website.

Help please? With like numbered walk through steps.

---

### Post by stchman on 2008-04-11
> **spiritsongtress said:**
> Lots of people have told me to get Mplayer but I don't know how to get it. (I know it sounds silly) But Its not in Synaptic packages so I am at a loss and I can't figure out how to get it from the Mplayer website.

Help please? With like numbered walk through steps.

I believe MPlayer is installed by default in Ubuntu.

---

### Post by Rhubarb on 2008-04-11
> **stchman said:**
> I believe MPlayer is installed by default in Ubuntu.
Then you'd be incorrect about that statement stchman.


**To get MPlayer installed:-**
Go to:  System --> Administration --> Software Sources
Make sure the top four boxes are ticked, then go in to synaptic package manager, press reload, then do a search for mplayer, then install it!

(You don't need to set the server to be Australia, unless you live in Australia that is)

---

### Post by spiritsongtress on 2008-04-11
I'll give it a shot. Any other suggestions. I think have tried it and it wasn't too effective.

---

### Post by Tatty on 2008-04-11
> **spiritsongtress said:**
> I'll give it a shot. Any other suggestions. I think have tried it and it wasn't too effective.

What do you mean by "wasnt too effective"?  That procedure shoud have worked to install mplayer... did you get any error messages?

What do you need it for?  Personally I use VLC for most media i play, i would  reccomend getting that.

---

### Post by stchman on 2008-04-11
If Mplayer is not installed by default then use the following command:

```
sudo apt-get install mplayer
```

---

### Post by spiritsongtress on 2008-04-11
I have VLc, but it doesn't seem to want to play my Data burned DVDs I burned with Nero.

---

### Post by Tatty on 2008-04-11
> **spiritsongtress said:**
> I have VLc, but it doesn't seem to want to play my Data burned DVDs I burned with Nero.

What are on these DVDs? There might be a slight miscommunication in terminology here, but if you burned it as a "Data DVD", then it will not play in anything, as it will simply contain files as normal computer files - not as a playable DVD video

---

### Post by GOROSSI on 2008-04-11
Should be under Add remove programs Go "Applications" then click on "Add/ Remove Programs" then select "All Available Applications"  from the top right drop down menu.

If you need firefox plugin support select "MPlayer Plugin for Mozilla" aswell as "MPlayer"

Also as rubarb says check the sources are selected you can do this by clicking on the "preferences" dialog on the bottom left of "Add / Remove Programs"
the boxes should look like the attachment

hope this helps :)

---

### Post by spiritsongtress on 2008-04-11
Actually anime is on the DVDs, and Mplyer won't let me install it. (Grr). Saying that it has dependancies that aren't install able. (or thing that it depends on aren't there) but I can play my 'data' DVDs on my Windows desktop and play the files off of them no problems.

 I am apparently using Gnome OS instead of the  KDE OS for Ubuntu and I thought this: [http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html) was MPlayer, but you guys seem to be talking about a different one.  Mind tossing me some clarification?

---

### Post by Tatty on 2008-04-11
Ok, have you tried the code from stchman's post above?  Or gorossi's post?  Both methods will work to get mplayer installed for you.

---

### Post by stchman on 2008-04-11
> **spiritsongtress said:**
> I have VLc, but it doesn't seem to want to play my Data burned DVDs I burned with Nero.

VLC is a media player.  Are you trying to play audio or video files in the data DVD?

---

### Post by spiritsongtress on 2008-04-11
The Video files and Audio files (since it's anime.. I'd like to have both)

When I tried the other methods of trying to install mplayer it said that the things it depended on weren't there or something.

When I do Sudo-apt get install mplayer I get this at the end

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages

---

### Post by oldos2er on 2008-04-11
You can fix broken packages from within Synaptic; look under the 'Edit' menu.

 Which version of Ubuntu are you running?

---

### Post by stchman on 2008-04-11
> **spiritsongtress said:**
> The Video files and Audio files (since it's anime.. I'd like to have both)

When I tried the other methods of trying to install mplayer it said that the things it depended on weren't there or something.

When I do Sudo-apt get install mplayer I get this at the end

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages

It sounds like you need to re-burn the data DVD in ISO 9660.  I had a couple of data DVDs I burned with Nero on Windows that Ubuntu REFUSED to read.  I went back to a Windows machine and re-burned the disc as ISO 9660.

---

### Post by bumanie on 2008-04-11
Follow this [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html) It should solve all your problems. I suspect you haven't got multimedia codecs installed.

---

### Post by Tyke91 on 2008-04-11
you need to get libdvdcss2 in order to play dvds.

first enable your medibuntu repository
```
  echo 'deb http://packages.medibuntu.org/ [COLOR=Red]hardy[/COLOR] free non-free'  |  sudo tee -a /etc/apt/sources.list


```[COLOR=Black]replace the red word with your current version of ubuntu. it's probably gutsy but it might be feisty or edgy
[/COLOR]```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```then do 
```
sudo apt-get update
``````
 sudo apt-get install libdvdcss2
```your movies should play in vlc or mplayer or totem (or whatever you have)

the reason that it's not included by default is that dvds require a proprietary format to run and ubuntu has a philosophy of only distributing free open source software.

---

### Post by spiritsongtress on 2008-04-11
Nope still not working even after doing what was suggested by Tyke. Though I will try what Bumaine suggested. I van't make it do what Bumaine suggested so... now I am back to square one.

---

