---
title: "3gp video"
date: 2005-06-24
forum: Art &amp; Design
---

### Post by tikal26 on 2005-06-24
Hey i just received an e-mail with video in 3gp formatt. i never used it before and i can't open it with mplayer. anyone knows how to open this formatt all the players i find are for windows

---

### Post by Hokputooy on 2005-06-24
I found this website in a google search, [http://www.saunalahti.fi/~laakkon1/linux/3650_vid.php](http://www.saunalahti.fi/~laakkon1/linux/3650_vid.php) , it shows how to convert 3gp to divx.

---

### Post by tikal26 on 2005-06-28
thanks

---

### Post by abhaysahai on 2005-06-29
run ubuntusetup.sh and 3gp files run properly in Totem/Kaffine.

Regards,
Abhay

---

### Post by Kimm on 2005-06-29
I'm pretty sure it runns under RealPLayer (for Linux), I have successfully played a file of this format before on my Ubuntu installation anyway

---

### Post by rajeshgautam on 2005-07-04
[QUOTE=Kimm]I'm pretty sure it runns under RealPLayer (for Linux), I have successfully played a file of this format before on my Ubuntu installation anyway[/QUOTE]
i am sucessfully playing .3pg file with the real player

---

### Post by tikal26 on 2005-07-04
[QUOTE=tikal26]Hey i just received an e-mail with video in 3gp formatt. i never used it before and i can't open it with mplayer. anyone knows how to open this formatt all the players i find are for windows[/QUOTE]
 Ok thanks to all of you because it works now. I just did not that Real player provided a linux software

---

### Post by coolworld on 2006-01-12
Installed RealPlayer 10 for linux but I can't seem to play 3gp video. Do I still need to install additional plugins, if yes, where can I download them?

---

### Post by sabitha on 2006-01-12
just installed w32 codecs will be just fine, you can open the .3gp with realplayer or totem-xine ;) . install w32codecs from the synaptic

---

### Post by coolworld on 2006-01-14
[QUOTE=sabitha]just installed w32 codecs will be just fine, you can open the .3gp with realplayer or totem-xine ;) . install w32codecs from the synaptic[/QUOTE]

Just new with ubuntu, but sorry for this dumb question, but how do I install the w32codecs? I open synaptic and try to search for w32codecs by it can't find it. What should I do?

---

### Post by george_apan on 2006-01-14
[QUOTE=coolworld]Just new with ubuntu, but sorry for this dumb question, but how do I install the w32codecs? I open synaptic and try to search for w32codecs by it can't find it. What should I do?[/QUOTE]
In a terminal window write:

$ sudo gedit /etc/apt/sources.list

and add this line at the end:
```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```
then in the terminal again:

$ sudo apt-get update
$ sudo apt-get install w32codecs

and you're done.

---

### Post by imagine on 2006-01-14
Rather use a repository made for Ubuntu than Debian (Sarge).

Add this to your  /etc/apt/sources.list:
```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

---

### Post by kakashi on 2006-01-14
compile you own mplayer. work for me. plays every single thing i throw at it.

---

### Post by ubuntian on 2006-08-13
> **imagine said:**
> Rather use a repository made for Ubuntu than Debian (Sarge).

Add this to your  /etc/apt/sources.list:
```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

for .3gp file,i can play in mplayer but no sound, n one more extension is .wma(songs), can't play also....can somebody help???

---

### Post by likes2skate on 2009-04-19
A one-shot install solution is mplayer; it will show 3gp videos but the sound does not play for me because of a codec error.

---

### Post by andrew.46 on 2009-04-20
Hi likes2skate,

> **likes2skate said:**
> A one-shot install solution is mplayer; it will show 3gp videos but the sound does not play for me because of a codec error.

You have brought a somewhat elderly thread back to life :-). Try installing the Medibuntu MPlayer and the w32codecs and you should be able to hear the sound as well.

Andrew

---

### Post by hairy one on 2009-04-28
Hi All
Now we can play 3gp's my question is how do we convert TO 3gp? 
Please

---

### Post by andrew.46 on 2009-04-28
Hi hairy one,

> **hairy one said:**
> Now we can play 3gp's my question is how do we convert TO 3gp?

Are you sure you *really* want to? The video is usually not good and the sound even worse... Having said that I have used FFmpeg in the past to produce such files for a very old phone that belonged to my wife. Her newer phone is more capable so it has been a while since I dug out the following.

If you are keen to try FFmpeg by commandline you will need to compile against the amr libraries that can be found in Medibuntu and I would advise following the Fakeoutdoorsman's great guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

but don't forget to add:

```
--enable-libamr-wb --enable-libamr-nb
```

The syntax I used for my wife's phone was:

```
ffmpeg -i input.avi -s qcif -vcodec h263 -sameq \
-acodec libamr_nb -ac 1 -ar 8000 -r 25 -ab 12200 output.3gp
```

and this worked well enough but you would need to tailor this to your specific needs. There may be a gui alternative to all of this if this all looks a bit much, but my wife was certainly happy with the results :-).

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-04-28
> **andrew.46 said:**
> 
but don't forget to add:

```
--enable-libamr-wb --enable-libamr-nb
```
In addition, I believe you will also need to add *--enable-nonfree*.

---

### Post by theterabyteboy on 2011-08-18
TRY THIS TO FIX YOUR PROBLEM:

Totem worked as root, not as user. Fix was, as user:
rm ~/.gstreamer-0.10/*
then
gst-inspect
to rebuild the gstreamer registry

---

