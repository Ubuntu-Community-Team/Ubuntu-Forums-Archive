---
title: "How do I play DVDs in Ubuntu?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by wog on 2007-07-06
gxine comes up with an error when I try to play The Musketeer.
"Error reading NAV packet"
...whatever that is.

Totem tells me I don't have the proper plugins to play it, but doesn't specify what plugins those are.

VLC doesn't seem to do anything at all after I choose DVD (menus).

What do I need to do to play this?

---

### Post by defrex on 2007-07-06
Either search synaptic (system>administration>synaptic package manager) for libdvdread, or enter this into a command prompt:

sudo apt-get install libdvdread3

Should clear up the problem.

Also, if you try and open most media types in totem, you'll be prompted to install the appropriate packages.

---

### Post by Bachstelze on 2007-07-06
Most likely, you will also need lindvdcss. It is not in the officiel repositories, check teh almighty Wiki.

---

### Post by wog on 2007-07-06
> **defrex said:**
> Either search synaptic (system>administration>synaptic package manager) for libdvdread, or enter this into a command prompt:

sudo apt-get install libdvdread3

Should clear up the problem.

Also, if you try and open most media types in totem, you'll be prompted to install the appropriate packages.

I installed the above file. Totem insists it still does not have what it needs to play the file. VLC still sits there doing nothing. gxine still gives the same error message.

Just what **is** a NAV file, anyway?

---

### Post by linuxwizard on 2007-07-06
Using these will get you all the codecs you need to play anything.

[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats)

[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Use the individual packages to install libdvdcss2 and w32codecs

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by wog on 2007-07-06
> **HymnToLife said:**
> Most likely, you will also need lindvdcss. It is not in the officiel repositories, check teh almighty Wiki.

I can't seem to find lindvdcss unless you mean libdvdcss which is already installed.

Your icon is lovely. Who is that?

---

### Post by wog on 2007-07-06
> **linuxwizard said:**
> Using these will get you all the codecs you need to play anything.
[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats)
[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Use the individual packages to install libdvdcss2 and w32codecs
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After installing all those, gxine plays the DVD and Totem still doesn't. Go figure. :)

Would it be okay to uninstall Totem, or am I going to need it for something?

---

### Post by RomeReactor on 2007-07-06
Hi. If you already have libdvdcss installed, and did:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
then you probably still have **totem-gstreamer**, which will give you a little bit more trouble with DVDs than **totem-xine**; so I suggest checking you have totem-xine and the extra libraries:
```
sudo apt-get totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
Since you already have the Medibuntu repository, it wouldn't hurt to also have **mplayer** and **w32codecs**. Also take a look at [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), it's a great resource.

All of this, assuming you have Feisty.

---

### Post by por100pre1 on 2007-07-06
Why not to use Automatix2?

[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

It can help you with many codec issues.

---

### Post by wog on 2007-07-06
> **RomeReactor said:**
> Hi. If you already have libdvdcss installed, and did:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
then you probably still have **totem-gstreamer**, which will give you a little bit more trouble with DVDs than **totem-xine**; so I suggest checking you have totem-xine and the extra libraries:
```
sudo apt-get totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
Since you already have the Medibuntu repository, it wouldn't hurt to also have **mplayer** and **w32codecs**. Also take a look at [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), it's a great resource.

All of this, assuming you have Feisty.

Invalid operation totem-xine?

---

### Post by wog on 2007-07-06
> **por100pre1 said:**
> Why not to use Automatix2?

[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

It can help you with many codec issues.

I can't figure out how to use it without messing up my system. One time I used it and discovered it uninstalled things I hadn't checked (since I knew I had them already), forcing me to go back and install them again.

Needless to say, as a new user I still haven't worked out what to do with an error message that doesn't involve ignoring it or bringing it here, so I opted not to use Automatix ever again.

---

### Post by RomeReactor on 2007-07-06
> **wog said:**
> Invalid operation totem-xine?

Sorry; forgot to add **install**:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```

---

### Post by wog on 2007-07-06
Weird. There were some updates about 5 minutes ago, and when they were done, I switched DVDs. Of course I had to close gxine to select a different DVD to play, and when I put in the new DVD, I expected to have to start gxine again to play it.

Instead, Totem started up and started playing the new movie.

Um, okay. :)

This issue appears to be resolved. I'll know for sure after I test it out on another 50 disks or so... :)

Thanks everyone!

---

### Post by whiteguysamurai on 2007-07-06
I assume you used the codecs provided with automatix?

---

### Post by wog on 2007-07-07
> **whiteguysamurai said:**
> I assume you used the codecs provided with automatix?

Actually, no. When I used Automatix last was two installs ago. When I first got Ubuntu it was Hoary, because that was the latest version I could get my hands on. Then I tried to update from that to Breezy, and it all went horribly wrong and I had to reinstall. Automatix was part of Hoary going all wrong in the first place.

The update from Breezy to Dapper went okay, and I used Automatix to get going again, but the update from Dapper to Edgy went badly too, so I had to reinstall *again*.

Now I'm on Fiesty, and I haven't had any problems, but if the pattern holds, I'm going to make sure I back up thoroughly before I update to whatever's next, since it should all die again, requiring another reinstall. But just to make sure, I'm really not going to use Automatix again if I can help it, since I really don't know what it's doing, and I really don't want to have to learn the scripting skills to be able to find out for myself.

---

