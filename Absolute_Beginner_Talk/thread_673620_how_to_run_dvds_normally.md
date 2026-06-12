---
title: "how to run dvds normally?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by nashphyl on 2008-01-20
Hi i am a new ubuntu user.I have no problems except for the fact that the totem movie player that i got with ubuntu does not run dvds like windows media player or real media player. I cant select things from a title menu or choose subtitles like a normal dvd player. Is there any way to fix this or is there a better dvd player than totem available? Thanks a ton!

---

### Post by jleaker01z on 2008-01-20
Click applications>add/remove

Search for gstreamer plugin

Install anything that says gstreamer plugin 
(Check boxes then click ok)

You will now be able to play anything you need

---

### Post by st33med on 2008-01-20
If you live in the US, you can't **legally** play DVDs on Ubuntu. Yeah, I know. Sucks. Blame it on the MPAA and other companies. Else, if you do not live in the US, install this without worry:

```
sudo apt-get install libdvdcss2
```

Just remember, this is not legal in the US.

---

### Post by LaRoza on 2008-01-20
> **st33med said:**
> If you live in the US, you can't **legally** play DVDs on Ubuntu. Yeah, I know. Sucks. Blame it on the MPAA and other companies. Else, if you do not live in the US, install this without worry:

```
sudo apt-get install libdvdcss2
```

Just remember, this is not legal in the US.

Actually, it seems to be a grey area.

You can find the threads that discuss it.

(My opinion is: you bought the movie, you bought the computer, you can watch it whenever and wherever you want, as long as you don't violate the license in the beginning of the movie)

[http://en.wikipedia.org/wiki/DMCA](http://en.wikipedia.org/wiki/DMCA)

The exceptions to this, in my opinion, allow US citizens to watch movies using the available programs. I don't know of anybody getting in trouble for using it.

**I am not a lawyer**

---

### Post by nashphyl on 2008-01-20
I still cant run dvds normally. I was given this message:
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

and i already have all of the things found under "gstream" installed. Is there any other way to run dvds normally? And dont worry about legality. I am in Mexico

---

### Post by Hospadar on 2008-01-20
You need to get libdvdcss from the medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

do the "Adding the Repositories" then try and install libdvdcss, that should get you working with encrypted dvds

---

### Post by Lord Illidan on 2008-01-21
After you install libdvdcss2, install totem-xine from Synaptic.

---

### Post by Iehova on 2008-01-21
The default totem install is based on the gstreamer engine which has some bugs regarding DVD playback, if you insert a disk into a drive it'll play, but if you open totem and select via the menu to play the DVD it'll complain about missing plugins.

Lord Illidan has it right, install totem-xine (it'll uninstall totem-gstreamer) and you'll be able to get the full DVD experience. :)

---

### Post by 3rdalbum on 2008-01-21
Or you could install libdvdcss2 and then try VLC - that's a very good DVD player.

---

### Post by SMA11784 on 2008-01-21
Alright, I had totem-gstreamer installed and popped in a DVD and I had sound but no video.  I install totem-xine which did uninstall totem-gstreamer, and now I get "Totem could not play 'dvd:///media/cdrom0'. - There is no plugin to handle this movie."

I've been googling solutions for a few days now telling me to install this package from that repository and nothing's working.  I'm running 7.10.

---

### Post by Majorix on 2008-01-21
You could look at ogle.. It is the only "real" DVD Player I could find... I haven't tested it yet myself though.

---

### Post by Lord Illidan on 2008-01-21
> **SMA11784 said:**
> Alright, I had totem-gstreamer installed and popped in a DVD and I had sound but no video.  I install totem-xine which did uninstall totem-gstreamer, and now I get "Totem could not play 'dvd:///media/cdrom0'. - There is no plugin to handle this movie."

I've been googling solutions for a few days now telling me to install this package from that repository and nothing's working.  I'm running 7.10.

Did you install libdvdcss2 and libdvdread?

---

### Post by SMA11784 on 2008-01-22
Yes, I have both installed.  I also installed gxine, totem-xine, libxine1 and now I can play DVDs in gxine.  They still don't play in Totem Movie Player, though.

If there's some quick way for me to copy/paste a list of the packages I have installed, lemme know.

---

### Post by stchman on 2008-01-22
> **nashphyl said:**
> Hi i am a new ubuntu user.I have no problems except for the fact that the totem movie player that i got with ubuntu does not run dvds like windows media player or real media player. I cant select things from a title menu or choose subtitles like a normal dvd player. Is there any way to fix this or is there a better dvd player than totem available? Thanks a ton!

I have a tutorial to play your Hollywood DVDs in Ubuntu.

First install your proprietary codecs.
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Then install the libdvdcss2 package from Medibuntu.
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by Incense on 2008-01-22
> **SMA11784 said:**
> Yes, I have both installed.  I also installed gxine, totem-xine, libxine1 and now I can play DVDs in gxine.  They still don't play in Totem Movie Player, though.

If there's some quick way for me to copy/paste a list of the packages I have installed, lemme know.

Check this page for copy and paste love. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by mdpalow on 2008-01-22
> **SMA11784 said:**
> Yes, I have both installed.  I also installed gxine, totem-xine, libxine1 and now I can play DVDs in gxine.  They still don't play in Totem Movie Player, though.

If there's some quick way for me to copy/paste a list of the packages I have installed, lemme know.

Give the link in my signature below a try. Assuming you have no hardware issues, my script should do it all for you and work.

Good luck

---

### Post by SMA11784 on 2008-01-22
> **mdpalow said:**
> Give the link in my signature below a try. Assuming you have no hardware issues, my script should do it all for you and work.
How long should this be taking?  Because it's been "Installing Codecs" for a while now.

EDIT: Nevermind.  Spoke too soon.  It works perfectly now, thanks.

---

### Post by rosegarden78 on 2008-01-22
VLC Media Player works for some people.  I would agree with LaRoza but keep in mind the DMCA is a new law this administration passed.  What's legal today may not be legal tomorrow and vice-versa.  It just depends on the initiative of those who influence and write the bills into law.

---

