---
title: "Need plug ins for movie player"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-07-21
I tried to use Movie payer and got the message that I needed plug ins to play the media.  No mention of what the plug ins might be or where to get them so that wasn't much help.

---

### Post by lisati on 2007-07-21
There are a number of options. [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) has some ideas about things which might be useful.

---

### Post by henthorn on 2007-07-21
Thanks, but that site is absolutely useless to the uninitiated.  It is about as useful as the notice that I needed plug ins.  All kinds of talk about the different repositories but I didn't find a single link to the repostories. Thanks for the attempted help though.  I am too dense to handle this stuff.

---

### Post by toasterofirony on 2007-07-21
[Try here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by pyros on 2007-07-21
[QUOTE=henthorn]Thanks, but that site is absolutely useless to the uninitiated. It is about as useful as the notice that I needed plug ins. All kinds of talk about the different repositories but I didn't find a single link to the repostories. Thanks for the attempted help though. I am too dense to handle this stuff.[/QUOTE]

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) is the best place to look for information on this

it links to [here](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f) where you can find instructions on how to add the repositories with simple one-line terminal commands.

---

### Post by Bigadada_saba on 2007-07-21
ok I will give you the following advice
1) search for easyubuntu and follow instructions on this sight
it will help you install all the codecs that is needed for playing dvds, mp3, ect.

 good luck

---

### Post by henthorn on 2007-07-22
Easyubuntu sounds like it might help an idiot like me.  Every one of the above suggestions ended in faillure.  Either there were more steps than described or the steps that were followed led to blind alleys.  The restricted formats link led to a forbidden site.  Can I just download the easyubuntu, follow the instructions  and have it become part of my regular ebuntu?

---

### Post by pyros on 2007-07-22
> **henthorn said:**
> Easyubuntu sounds like it might help an idiot like me.  Every one of the above suggestions ended in faillure.  Either there were more steps than described or the steps that were followed led to blind alleys.  The restricted formats link led to a forbidden site.  Can I just download the easyubuntu, follow the instructions  and have it become part of my regular ebuntu?

I Don't understand what you mean by a forbidden site...
to add the medibuntu repositories, go to Applications>Accessories>terminal and type:
```

echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
Or they can also be added through the "third party software" tab of the software sources window described below.
If you have not already enabled the universe and multiverse repositories, there is an easy grapical utility to add it:
[quote=ubuntuguide.org]
You can add extra repositories using the Software Sources application, which can be found in the menu: System -> Administration -> Software Sources. Check the repositories you think you will need (main, universe, restricted, multiverse).[/quote]

Then you can just install the codecs through add/remove programs. Or, to install flash, sun's java, microsoft web fonts, dvd support, acrobat reader and pretty much every codec available, type 
```

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs gstreamer0.10* mozilla-acroread

```

The advantage of this method is that all of the installed programs will update with the rest of your operating system, and many more programs will be available for install through add/remove applications or synaptic.

---

