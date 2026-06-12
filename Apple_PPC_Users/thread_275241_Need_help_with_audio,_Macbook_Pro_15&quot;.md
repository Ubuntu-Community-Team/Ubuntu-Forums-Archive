---
title: "Need help with audio, Macbook Pro 15&quot;"
date: 2006-10-11
forum: Apple PPC Users
---

### Post by commonmanthemes on 2006-10-11
I've been following this way of making the 15" Macbook Pro's audio work:
[http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39](http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39)

Yes, it works, but it's been a couple months since that was posted and I wanted to see if there's been a better way discovered that allows the headphone jack and speakers AND the bypass (turns off speakers when headphones are in) to all work.

Thanks.

---

### Post by melvis02 on 2006-10-13
I've had luck on my 15" MBP with the newest alsa-drivers ([alsa-driver-1.0.13]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2")).  There is no need to edit hda_codec.c like with Gendo's trick.  I compiled them using ```
./configure --with-cards=hda-intel --with-sequencer=yes
make
sudo make install
``` Reboot, and if your sound driver isn't loaded, run ```
sudo modprobe snd-hda-intel
```  Once restarted, I opened Gnome Mixer, went into the preferences and added all the tracks.  Then I went into the Switches tab in Gnome Mixer and ticked the box 'Line In as Output.'  Once that was ticked, I had audio, and was able to use the 'Side' and 'PCM' sliders to adjust the volume.  The audio sounds a little tinny, and the occasionally crackles, but there is audio nevertheless.  I'm not quite sure if this is the way it's suppposed to work, but it's better than nothing I suppose.  Hope this helps someone other than me...

---

