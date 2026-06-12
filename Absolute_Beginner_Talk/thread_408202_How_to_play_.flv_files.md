---
title: "How to play .flv files"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-04-13
I just downloaded Firefox's videodownloader plugin. Every file stream it downloads is in the .flv format. I would appreciate if you could walk me through the steps about how to actually play an .flv file.
Thanks

:guitar:

---

### Post by nudnik on 2007-04-13
> **jprb85 said:**
> I just downloaded Firefox's videodownloader plugin. Every file stream it downloads is in the .flv format. I would appreciate if you could walk me through the steps about how to actually play an .flv file.
Thanks

:guitar:

You need to install Adobe's Flash player. If you are running a 32bit Ubuntu its very easy, if you arent, I'd forget about it:D 

In the lucky event you are running 32bit, navigate to the Adobe site, download the Linux Flash Player in "tar.gz" format (as opposed to the Red Hat RPM package) to your desktop. Extract the file folder. Navigate to the file folder using the terminal:

cd Desktop/(filename)

go root to ensure permissions are set correctly

sudo -s
(password)

Find the flashplayer-installer  file and type:

./(filename)

Follow the directions and all should be well. (the directory of your browser the installer needs should it request is likely "/usr/lib/firefox/plugins")

---

### Post by D!mon on 2007-04-13
it's quite easy to set up flash player (at least, firefox plugin) even if you are running 64bit as described here: [http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+amd64](http://ubuntuforums.org/showthread.php?t=341727&highlight=flash+amd64)
I tried this guide both with Edgy and Fiesty beta and it worked like a charm for me.
Btw, I can play .flv with default mplayer, though can't change the position of a play(

---

### Post by dmizer on 2007-04-13
actually, if you're not against using the command line, you might find it easier to simply convert the flash video to avi format.  use this command:

```
ffmpeg -i videoname.flv -vcodec msmpeg4v2 outfilename.avi
```

---

### Post by StefanoCole on 2007-04-13
To play downloaded *.flv files install MPlayer or Vlc.

Stefano

---

### Post by Bloch on 2007-04-13
mplayer plays *.flv files fine.

You can play *.swf games etc with  gflashplayer.

I never tried the videodownloader plugin becasue I use the UnPlug plugin. - It also downloads streaming video,and I've found it does all I want.

---

