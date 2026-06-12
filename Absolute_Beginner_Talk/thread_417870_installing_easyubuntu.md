---
title: "installing easyubuntu"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-04-21
ok guys, its me the MORON again, asking for help:

i downloaded the deb
i ran the line of code in the terminal it told me to
i installed it

no media works stil

HELP PLEASE


:popcorn:  popcorn bucket

---

### Post by slickidiotfan on 2007-04-21
You restart your machine ;)?

---

### Post by thelegionnaire on 2007-04-21
ill try that now

---

### Post by thelegionnaire on 2007-04-22
nope didnt work, does it matter if im running a amd64?

---

### Post by slickidiotfan on 2007-04-22
I don't think EasyUbuntu runs with Feisty Fawn, is that what you are running?

---

### Post by thelegionnaire on 2007-04-22
yup, so what do i do otherwise? any other easy way to get the codecs?

---

### Post by slickidiotfan on 2007-04-22
What type of codecs are you looking for? The Synaptic Package Manager has plenty of files for codecs.

If you are looking for multimedia codecs I recommend this link:
[http://hivltg.co.uk/?p=8](http://hivltg.co.uk/?p=8)

---

### Post by thelegionnaire on 2007-04-22
so in feisty it automatically tries to download codecs, but now since easyubuntu is on there, it says there is conflicting software, now that

@slickidiotfan
you listen to much industrial?

---

### Post by slickidiotfan on 2007-04-22
I used to a little, Slick Idiot is still good stuff.

By the way, have you tried removing EasyUbuntu via Add/Remove.. under Applications?

---

### Post by thelegionnaire on 2007-04-22
i am VERY new at this

---

### Post by thelegionnaire on 2007-04-22
its not in there

---

### Post by slickidiotfan on 2007-04-22
Next to the Search button is "Show" click on All and try again. I have never used this so I wouldn't know exactly.

---

### Post by thelegionnaire on 2007-04-22
nope, not in there at all

---

### Post by thelegionnaire on 2007-04-22
i think i just did it in the synaptic package manager

---

### Post by slickidiotfan on 2007-04-22
Oh all right, does it allow you to install the codecs? If all else fails you could just use VLC Media Player.

---

### Post by thelegionnaire on 2007-04-22
oh really? thats what i used in windows :) can i get winamp?

---

### Post by tdrusk on 2007-04-22
> **thelegionnaire said:**
> oh really? thats what i used in windows :) can i get winamp?

No, but you can get audacious.

it's in synaptic.

---

### Post by thelegionnaire on 2007-04-22
i think this may be sending me in deeper confusion

---

### Post by slickidiotfan on 2007-04-22
Haha ok, take a step back, tell me what you want to do.

---

### Post by thelegionnaire on 2007-04-22
um, so when you try to open an mp3 it automatically send u to get the codecs, i go to install and it says there is conflicting software, i removed easyubuntu and reset, still says it, now what, forget vlc, that looked very confusing

---

### Post by slickidiotfan on 2007-04-22
Have you restarted the machine since installation? Getting VLC is VERY simple. 

```
Graphical way

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).
Command line way

You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

source: from videolan.org's website.

---

