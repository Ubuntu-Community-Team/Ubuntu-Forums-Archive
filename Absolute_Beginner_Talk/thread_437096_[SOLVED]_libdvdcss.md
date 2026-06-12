---
title: "[SOLVED] libdvdcss"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by johnnylong on 2007-05-08
Hello again everyone. I would again like to thank those who have provided me with some much need guidance in making the transformation from Windows. All is going well and my transformation is almost complete, but I need just a little more help. Xine Movie Player has given me the best results with dvd playback with only one problem. I can't get past the encryption. I have noticed references to installing libdvdcss but can't find it in the repositories. Oh, did I forget to say that I am running the latest version of Ubuntu. Welcome all help.
Hack the Planet!

---

### Post by Campingman on 2007-05-08
Could be wrong, but it looks like this is included in libdvdread3 which is included in synaptic package manager (although I would have thought it should have been installed with gxine).  Have a look anyways:
System>Administration>Synaptic package manager and do a search for libdvdcss and libdvdread3 will come up.  There is a box next to it if it is green it is already installed, if not click on the box (mark for installation) and then apply.

---

### Post by compmodder26 on 2007-05-08
libdvdcss isn't in the default repositories.  You have to include the medibuntu repositories to get it.  Here are instructions: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626).  Scroll down to the part about DVD playback.

---

### Post by rai4shu2 on 2007-05-08
Or use:

sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by Campingman on 2007-05-08
Yeah, sorry, I did say I could be wrong!  I mis read the description of Libdvdread3

---

### Post by johnnylong on 2007-05-08
Thanks gentlemen, I have made the necessary change but I am still get the following message:

  ' The source seems encrypted, and can't be read. 
  Your DVD is probably crypted  According to your country law, you
  can or can't install/use libdvdcss to be able to read this disc, which
  you bought. (Media stream encrypted/scramabled).

  By the way, I already had libdvdread3 installed so I knew that wasn't the problem. 
  Any thoughts?

   Hack the Planet!!

---

### Post by jbor7755 on 2007-05-10
> Or use:

sudo /usr/share/doc/libdvdread3/install-css.sh

I have just got totem-xine up and running. But I cannot get libdvdcss using the above command. Ubuntu can't seem to connect to the external website via my dial up connection.

I can however access the page via firefox so what is going on here?

Is there an alternative method for installing libdvdcss (and associated files)?

---

### Post by AnRa on 2007-05-10
You can use the Medibuntu repository: [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) ;)

---

### Post by johnnylong on 2007-05-11
HI Everyone, finally found all the necessary codecs and have ALL my media-players working like a charm.
Thanks for the community Help. Much Appreciated!

Hack the Planet!!

---

### Post by russo.mic on 2007-05-16
Well,

What all codecs did you have to use?  I'm about to break my computer over the desk!!!

Russo

---

### Post by esoterica on 2007-05-16
These instructions work perfectly, you can just copy and paste the commands into your terminal window...

Playing commercial DVD's:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Additional info for stuff like mp3's etc...:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And a tip that isn't mentioned anywhere in the documentation and I learned and had to figure out on my own the hard way. If you haven't enabled "Desktop Effects" already then don't do it, it causes problems when trying to play DVD's like you can hear the sound, but not see anything but a black screen while your movie is playing.

---

