---
title: "help with playing dvds"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by caratuco on 2007-06-17
I have been trying to enable my player/burner to play dvds for a few days now with no success. A week or so ago I installed on another system and was able after an update to follow and install all of the needed packages outlined in Adamant1988's sticky. For some reason I cannot get any of the gstreamers or restricted extras to even show up in add remove programs, they are just greyed out. I downloaded synaptic, still no go. I have tried  "sudo apt-get clean && sudo apt-get autoclean", "sudo mv /etc/apt/souces.list /etc/apt/sources.list.old" followed by  "sudo touch /etc/apt/sources list", then "sudo apt-get updates", and "cp /etc/apt/sources.list.old  /etc/apt/sources.list", and finally, sudo apt-get updates", all with no luck. I have tried "sudo aptitude update", "sudo aptutude upgrade", "sudo apt-get upgrade". in many combinations of the above,none seem to work. My sources list was created using "source-o-matic" and includes multiverse / universe . Also, I have tried using non us repositories with worse results. I'm not sure what has happened, as I said a week ago things went fine. Perhaps some legal issues?
Thanks in advance for your help.

---

### Post by p_quarles on 2007-06-17
Have you tried this? ```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list' wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

That enables the correct repository, and then you can say 
```
sudo apt-get install libdvdcss2
```

Hope this helps.

---

### Post by caratuco on 2007-06-18
thanks p_quarles,
I have that repository and did download libdvdcss2 no problem. It's the Gstreamers and restricted extras I can't get.

---

### Post by tgbrowning on 2007-06-18
Pardon me for jumping in here, but I finally got the Totem DVD player working along with a couple of other ones, yesterday. Along the way, 

I had problems using the sudo get commands and finally managed to get SPM to do what I needed, mostly as I recall, through updates. 

I did notice that in the manager, you can look and see both what is required by a package and what might possibly conflict with it. You might want to check that out.  For example, when I finally did get the xine version of Totem fixed, it required me to remove all of the gstream components before I was able to get the xine version to work. You might check that. Also, you can add to the repositories list to get Universe and Multiverse access to a number of different libraries.

One othe weird thing I noticed was, along the way, I was told that the libdvdcss2 library was listed as either "broken" or "obsolete". That got fixed when I asked SPM to get the update for xine from a Universe site.

Browning>>>

---

### Post by caratuco on 2007-06-19
Thanks Browning
I keep getting an error code (1) with universe. I'll keep trying I guess.

---

### Post by tgbrowning on 2007-06-19
caratuco,

Yeah, I've found SPM to be a bit terse in it's responses.  And cryptic in how it works. Probably the latter because I'm simply not used to it.

I ran across a VERY good walk-through a couple of days ago and I'll see if I can relocate it for you. (That's another big change from Windows -- one should keep a record of what one does...)

In the mean time, here's a list of what I finally installed that got things working. I realize that you were preferring to use gstream rather than xine, but it will give you an idea of what libraries you might be missing. 


Removed the following packages:
totem-gstreamer

Installed the following packages:
libxine-extracodecs (1.1.1+ubuntu1-2)
totem-xine (1.4.3-0ubuntu1)
totem-xine-firefox-plugin (1.4.3-0ubuntu1)
xine-ui (0.99.4-0ubuntu6)

---

### Post by Nezing on 2007-06-19
This is how I got my DVD's to play in Ubuntu.Cut and paste this in Terminal:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

Let the package unpack.Then cut and paste this in Terminal:

sudo /usr/share/doc/libdvdread3/install-css.sh


For me,play back is fine.  :popcorn:

---

### Post by tgbrowning on 2007-06-19
> **caratuco said:**
> Thanks Browning
I keep getting an error code (1) with universe. I'll keep trying I guess.

Here's a good walk through, but I'm still looking for that first one that turned the trick. 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Pay secial attention to:

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

 The line above is specific to Feisty, not Dapper.

Browning>>>

---

### Post by tgbrowning on 2007-06-19
> **Nezing said:**
> This is how I got my DVD's to play in Ubuntu.Cut and paste this in Terminal:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

Let the package unpack.Then cut and paste this in Terminal:

sudo /usr/share/doc/libdvdread3/install-css.sh


For me,play back is fine.  :popcorn:

-----------------------------------------------------------------

Looks a bit scary -- Ugly? Bad?

You got any idea why someone, somewhere, decided to characterize those particular commands so?

:)

Browning>>>

---

### Post by p_quarles on 2007-06-19
"Ugly" and "bad" refer to various proprietary and lossy codecs. Unfortunately, you need a lot of these to get certain things to work. Nothing to be scared of, though. ;-)

---

### Post by tgbrowning on 2007-06-19
> **p_quarles said:**
> "Ugly" and "bad" refer to various proprietary and lossy codecs. Unfortunately, you need a lot of these to get certain things to work. Nothing to be scared of, though. ;-)

I'll keep that in mind.

---

### Post by caratuco on 2007-06-19
You guys are terrific!
I try all mentioned solutions and let you know.

---

### Post by caratuco on 2007-06-20
I used source-o-matic and changed to Costa Rican servers. Everything updated fine and I downloaded tgbrowning's suggested packages and all my players function now. 
Thanks guys for all your help!!

---

