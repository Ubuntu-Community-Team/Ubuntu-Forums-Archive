---
title: "[SOLVED] Soundkonverter issues in Gutsy"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by andybleaden on 2008-02-04
Well I am back after my pc crashed with nasty partition issues which came after upgrading to gutsy  ( not necessarily connected)

I have got gutsy working again and had to reinstall soundkonverter which worked ok but cannot convert to mp3 files or any other format other than wav/ogg. Tried to download the plugins but to no avail. Is there a trick I am missing. I installed this previously and the plugins were all there. 

Maybe there is a script I can run in konsole that can illustrate this easier for you guys to advise me on?

I have three plug ins in the kde/share folder but cannot seem to get them to work and in the environment section there is only options for ogg files?

Any help would be gratefully appreciated.

Andy

---

### Post by emarkd on 2008-02-04
I'm not a KDE user, so this may not be the correct move, but did you install the ubuntu-restricted-extras metapackage?  I know that's where the most common non-free media/dvd/fonts are grouped together, including lame.

---

### Post by andybleaden on 2008-02-04
Umm?:confused:


nope ...how do I go about that?

I would like to do this via konsole if possible ( less problems) . I take it I do a sudo get install thing?

---

### Post by emarkd on 2008-02-04
On a hunch, I searched for a kubuntu version of that package, and sure enough there it is!  Try this:

```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by stooshbunutu on 2008-02-04
It sounds like you're missing either the *lame* codec or the *ffmpeg* codec installed which handles converting mp3 files. Also try checking the packages.ubuntu.com website and look under the [soundkonverter section ]("http://packages.ubuntu.com/gutsy/kde/soundkonverter")for nescessary dependencies and recomended plugins.

Hope this helps:)

---

### Post by andybleaden on 2008-02-04
Yeh I tried to install these but could not get it sorted at all. Tried to install and d/l the lame on Sunday but got nowhere. Tried to get it from sourceforge 

I will try the sudo apt-get install kubuntu-restricted-extras command and see what happens then

I will also then go to the other site

---

### Post by emarkd on 2008-02-04
Lame is installed by the kubuntu-restricted-extras package.  It's also available separately from the repositories.  Unless you have a real good reason, you should try to stick to the software in the repositories.  Not only is it MUCH easier to install, it's more likely to work properly with your system.  The software repository is a strange thing for some Windows users to get used to, but it's well worth it.  Keeping things simple and using pre-packaged software as much as possible will make your Linux transition much smoother.

---

### Post by andybleaden on 2008-02-04
SO I should be able to get it via the adept installer facility then?

I am sure i tried that approach and nothing came up with Lame...there was a glame if I remember.....

---

### Post by emarkd on 2008-02-04
Do you have all of the extra repositories enabled.  Lame is restricted, so it's either in Multiverse or Universe, I'm sure.  I don't use Adept, but in Synaptic, you'd click on Settings > Repositories and select them from there.  Remember that you have to click Reload after you make changes to the repository list before your searches will use the new locations.

---

### Post by andybleaden on 2008-02-04
I tried that one. I think my repositories are all up to date. i get a little confused I must admit with adept . i thought it used to list all of my programmes but since I upgraded it does not seem to show so many. I think I had better try to use the restricted thing suggested earlier. I will post the result later on when I get home to ensure I get this right.

I really liked soundkonverter and would be a shame if I c annot use ti. I also tried to use the other programme soundconverter but could not get it running...starts to run then crashes so I prefer Konverter

By your question about repositories being enabled do you mean I can extend the range? I have ticked to show unsupported ones ?

---

### Post by kaiju on 2008-02-04
to enable repositories, open up a terminal (konsole) and type
```
kdesu kate /etc/apt/sources.list
```
you will be prompted for your password and after typing it in you will be able to edit sources.list (this is the file your package manager adept uses to know where to look for installable packages).
in that file, remove the "#" from the beginning of lines containing "universe" and "multiverse". save the file and close kate.

back to konsole, type
```
sudo apt-get update
```
after this, kubuntu-restricted-extras should show up in adept. if you want to get it faster, just type
```
sudo apt-get install kubuntu-restricted-extras
```
in konsole (same thing as opening up adept, finding kubuntu-restricted-extras, selecting it and installing).
as emarkd already pointed out, since you are this way installing many of the important restricted codecs and other apps, this should get you going.

---

### Post by andybleaden on 2008-02-04
Wow

Just what I needed 

I will sort this out when I get home and post the response on here positve or negative. I did not know that the reinstall had stopped restricted kubuntu areas

Thanks to all who have helped with this issue

Andy

---

### Post by andybleaden on 2008-02-04
I think the adept thing is this...is this correct  ( not for upgrading but saw it and it looked like what you say

[http://www.kubuntu.org/~jriddell/kubuntu-upgrade/snapshot1.png](http://www.kubuntu.org/~jriddell/kubuntu-upgrade/snapshot1.png)

---

### Post by andybleaden on 2008-02-04
Tried it via the adept manager model and it worked a treat so thank you all very much. Downloading lame as we speak:)

---

