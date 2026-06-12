---
title: "dvd playback!!"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-07-08
ok, i'm about to run my head into a wall.

i cant get dvd movies to play on dapper. ive installed every possible plugin i can think of, including the libcssdvd and w32codecs from the mediabuntu. ive also installed lots of different versions of dvd players, and all of them are giving me the same (or almost the same) error message, saying that i dont have the correct plugins or license to play an 'encrypted' dvd. shouldnt the libdvdcss have fixed that? heeeelp.

---

### Post by eternalsword on 2007-07-08
I'm guessing you're using totem, try installing totem-xine, this should remove totem-gstreamer.  You can just install via synaptic or from terminal ```
sudo apt-get install totem-xine
```

---

### Post by irishgoth8822 on 2007-07-08
i have totem-xine. it wont play them either. it says that its an 'encrypted' or 'faulty' dvd, just like some of the other programs have told me.

---

### Post by eternalsword on 2007-07-08
you may need libdvdread but I cant remember.  I use mplayer for all my media so I never had to deal with that ;)  I'm sure vlc could play it back as well.  Neither of those should require additional decryption libraries as they are built in.

---

### Post by irishgoth8822 on 2007-07-08
ive tried mplayer, it starts like its going to play it, then blanks out. i also have vlc, which wont even open the disc or detect it. 

i have libdvdread.

im totally at a loss here lol

---

### Post by Medieval_Creations on 2007-07-08
I use VLC, but this should work for totem or mplayer as well.
I'm not sure if you tried it yet, but libdvdcss2 is the one you need for most of the newer DVDs.

I use the Medibuntu repo's.  Try this:

Add these lines to your apt sources.list.  You can change out dapper to any any version up to fiesty.  I don't think gutsy is up yet, but I haven't tried.
```

## Mediabuntu
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

```

**EDIT** - Sorry, forgot this step.
Get their gpg key.
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```

Do an update.
```

sudo apt-get update

```

Here is the script that I run when I have to do a new install that takes care of all the codecs.
```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui libdvdcss2 w32codecs

```

Hope this helps.

---

### Post by MoebusNet on 2007-09-04
me@my-desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
me@my-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate
[/COLOR]

---

### Post by marco123 on 2007-09-04
Try  "sudo /usr/share/doc/libdvdread3/examples/install-css.sh"  in the terminal then restart.  It's always worked for me.:)

Edit: Or "sudo/usr/share/doc/libdvdread3/install-css.sh"

---

### Post by albeano2004 on 2007-09-07
> **MoebusNet said:**
> me@my-desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
me@my-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate
[/COLOR]

I think your problem is you forgot to 
```
sudo apt-get update
```
If I'm wrong, then :confused:. I'm still a Linux newbie really:lolflag:

---

### Post by andrew.46 on 2007-09-07
Hi,

 Good to see a fellow Dapper user and sorry to see your frustration. I have published a page of my own Dapper setup which includes setting up repositories and DVD playback:

[http://people.aapt.net.au/~adjlstrong/dapper.html](http://people.aapt.net.au/~adjlstrong/dapper.html)

 You could easily ignore some of the stuff on the page which is a little idiosyncratic but there is a DVD playing section about halfway down that should get you out of trouble :-)

                         Andrew

---

