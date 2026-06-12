---
title: "how to make dvd rom play dvds and CD?"
date: 2023-02-20
forum: Apple Hardware Users
---

### Post by 2blue on 2023-02-20
I have had lubuntu on an old macbook pro for a couple of years now, however I have not managed to make the DVD player work. I don`t use it too often, but now I have received a couple of CD and DVD I like to check out. I also have a few old CDs with stored documents I like to read and use. 

Any ideas? I have tried to install libdvdcss2, but terminal will not recognise command. I may have made a bit of a mess, I have had a bit of help in the irc channel and I have tried to follow tutorials on the ask ubuntu site. 

Should it be enough to tag off for restricteds in package manager?

---

### Post by ajgreeny on 2023-02-20
The older method of installing libdvdcss no longer works and you now have to follow the instructions at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

An outline of what is needed is:-
> Ubuntu 15.10 and newer

From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.

    Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line: 

sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg

    Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss. 

---

### Post by 2blue on 2023-02-24
I couldn`t make anything work. I wonder what it might be, it seems very much like driver issues. In any other respect, there would be no point in reinstalling the old macos on this macbook.

---

### Post by guiverc on 2023-02-24
You've not provided any Lubuntu release details, which to me is the required starting point, though I have almost no experience on apple hardware.

I keep *supported* releases of most products available so I can run quick tests & provide suggestions, but as I don't know your release I can't grab a *random movie dvd* and insert it in one of my boxes as I don't know which release to actually boot.

I will say much of the DVD drives are now getting old...  I've had to replace 3x DVD writers in burning my last 5 discs; ie. the drives are old & thus close to failing & the *write* or *burn* seems to kill them (*far more than just a read of data*)...   My PCs are generic though, and I've still got a pile of ~8 replacement drives ready to be put in (*though that stack gets smaller by 1-2 per year now*).  Are you sure your drive still works?  (ie. *can it read data off discs even if it won't play a movie for example*)

---

### Post by 2blue on 2023-02-25
I have 22.10 from last fall. It was upgraded from 22.04, which again had been freshly installed from a usb. I have kept to lubuntu on this hackintosh since about 2019 or 2020. I haven`t done much about the DVD rom, mostly because I didn`t need it until lately.  I know it worked fine with the old MacOS on just before the new SSD was put in. It is too much bother to recover macos to check at this point. 

I am not sure which model I have longer, I used to be able to check in when I had MacOS on. I think it was bought early in 2017, but it has to be one of those models that kept selling, and with a DVD rom. Officially Apple hasn`t had built in DVD since 2016. I remember most of the 15" macbooks pros had dvd at the time. It is a 13", intel i7 cpu, not entirely sure about the screen, but can stand beside a retina screen and look much the same (...the newer iMac is noticeably better though).  I don`t think it matters much, since it is old, Ubuntu tend to provide support.  Whichever model number this is, DVD roms can get damaged, but so far I lean towards driver - software issues.

---

### Post by guiverc on 2023-02-25
> **2blue said:**
> I have 22.10 from last fall. It was upgraded from 22.04

-- *off-topic fall talk*
last fall?  That's not one of the four seasons in most of world; but I think it relates to stuff falling from trees.  As an *aussie* that can be anytime (eg. when I hear a tree 'falling apart' on a walk I quickly move away then look up & expect to see a flock of large black cockatoos (yellow tailed where I live) eating thus the 'fall' of portions of the tree). Not all the world has *cockies*, so outside of that it's in the middle of summer (December & January) as if there wasn't sufficient rain leading up to summer, eucalyptus drop limbs in extreme heat when dry.  Maybe I'd appreciate better if I lived in the mountains, thus actually knew what snow & real cold is (*winter is single digit degrees Celcius; mid-low 30s in Fahrenheit*).
-- *end off-topic *

Anyway, I went & grabbed a ~random DVD from the top of a pile (*my only selection criteria was I purposely avoided piles that had DVDs I didn't want to hear/see*) and it's *Dead Bang*, a movie.

Booted a box (*which has DVD player*) and selected what I hoped was *kinetic* or 22.10; alas it's a *lunar* install (*what will be 23.04 on release; but I opted to use that anyway*)...

Inserted the DVD in the install; and VLC didn't want to play it...  This maybe what you're experiencing.

A quick search & some wiki pages maybe helpful (FYI:  *Lubuntu is a Ubuntu system, we just use a different desktop/GUI with a few different apps that share resources with our chosen desktop*)
- [https://help.ubuntu.com/stable/ubuntu-help/video-dvd.html.en](https://help.ubuntu.com/stable/ubuntu-help/video-dvd.html.en)
- [https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html.ro](https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html.ro)

I view the [second] *restricted* page as it looks helpful so I enter the following commands

```
sudo apt install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg 
apt-cache policy  libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
sudo apt install libdvdnav4 libdvdread8 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

ie. I firstly install `libdvd-pkg`, then run the `sudo dpkg-reconfigure libdvd-pkg` after that.

The `apt-cache policy` command was me just looking to see if those packages were installed (*I copy/pasted them from the restricted WIKI page I listed earlier; alas I skimmed over the output too quickly thus my first attempt of the `apt install` failed as libdvdread4 doesn't exist !!which is why I have two `apt install commands*`....)

I then do a quick scan (via CLI actually (`apt-cache search` & `rmadison`, but the output I was got can be see at [https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=libdvdread8&searchon=names](https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=libdvdread8&searchon=names) ) ie.  the libdvdread4 should be libdvdread8 for *jammy* & later... thus my second `apt install` attempt.

Personally I like watching DVDs using MPV, so I `apt install mpv` too.

I can't recall if I tested before I logged out, but regardless I did logout & login again & test (*or retest*) that it continued to work post-login, and sure enough I have *Dead Bang* on DVD playing on my box.

Do note it's not playing still on VLC (*VLC now crashes with crash report in /var/crash for me*) & I'd have to look further into that, but MPV looks different to VLC & that visual clue reminds me it's external media (*not local or network share where I prefer VLC*) which is why I prefer MPV for optical media such as DVD.

Are you happy using MPV?

*doco page bug report here - [https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/2008601](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/2008601)*

---

