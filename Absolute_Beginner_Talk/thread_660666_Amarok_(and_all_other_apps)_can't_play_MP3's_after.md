---
title: "Amarok (and all other apps) can't play MP3's after upgrade"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Aikanar on 2008-01-07
This morning after a small system update, I suddenly lost the ability to play MP3 files in **any** application.

I have completely reinstalled the codecs (win32 as well as the Ubuntu standard), but the problem is just as it was before.  When Amarok tries to play an MP3, it throws up a dialog asking if I want to install support for MP3's.  If I say yes, Amarok will hang most of the time -- occasionally, I can get it to say something like 'missing amux' (or something of that sort).

Sorry I cant be more specific, but I have been mucking around for hours here and getting no closer to a solution.  Hopefully, someone here can help.

I'm running Kubuntu Feisty 32 bit.

The version of Amarok I'm using is the one in the repos.

///Dave

---

### Post by Aikanar on 2008-01-07
Actually, I just discovered that VLC can play them if I manually select them in its file dialog.

Also, all of my movies (mostly *.avi's) play correctly in Kaffeine.

I'm at a loss to understand what's going on here.

///Dave

---

### Post by the Didey on 2008-01-07
i know that you have to install "commonly used restricted packages" from the add/remove or from synaptic for gutsy. but I'm afraid that's all i got.

---

### Post by forestpixie on 2008-01-07
I needed libxine1-ffmpeg to get amarok going

---

### Post by Aikanar on 2008-01-07
> **forestpixie said:**
> I needed libxine1-ffmpeg to get amarok going

I have libxine1-ffmpeg installed (apt-get reports this).

As I said this just happened on an ordinary update, **not** a version upgrade.

I really like Amarok and want to continue to use it, but that will require getting this codec problem or whatever it is fixed, as my other MP3 players don't function either.  The only other app that plays MP3's at the moment is VLC -- which is not really an MP3 player.

Some help with this would be greatly appreciated.

///Dave

---

### Post by forestpixie on 2008-01-07
all I can say is that I do tend to get all the gstreamer- codecs, thew good the bad and the ugly ones as well - and as they're all on a list I use when I do a reinstall the only one that appeared to cause a problem last time was the libxine1

sorry I can't be of more help :(

have you looked at the amarok forum - it's been a help to me in the past

---

### Post by DarkDancer on 2008-01-07
Ok, so the OP has had the ability to play MP3's, until he did an update. Now he can not play an MP3 in any application except VLC (but of course VLC comes with it's own codecs and such). It seems the update broke something.

OP, do you know what got updated. Does anyone know how to tell what got updated in the last update (is there a file listing it or something somewhere?)?

---

### Post by forestpixie on 2008-01-07
you could check in /var/apt/cache/archives and see which is the latest dated deb - probably from the cli too but no idea

---

### Post by DarkDancer on 2008-01-07
Does anyone think we'd get better answers for Multimedia and Video? Can someone move this?

---

### Post by bhold on 2008-01-07
This might be worth a try, good luck...

[http://ubuntuforums.org/showthread.php?t=421527&highlight=amarok+%2B_sAm_](http://ubuntuforums.org/showthread.php?t=421527&highlight=amarok+%2B_sAm_)

---

### Post by forestpixie on 2008-01-08
you could try reinstalling libxine1, purge it first

sudo apt-get remove --purge libxine1-ffmpeg
sudo apt-get install libxine1-ffmpeg

---

### Post by kadrianus on 2008-02-01
I had the same problem with 2 machines after gutsy update
I also get the pop windows that invites to install mp3 support (didn't work)
I also run the script from console (didn't work)
I also installed amarok and every single related library again (didn't work)
Amarok was able to play mp3 if it were started as root (sudo amarok from console).
Other players were able to play mp3.

So...

- Close Amarok

-Open a console

- Go to your home

	**cd ~**

- Backup your .xine directory just in case you want to get it back.

	**tar -cvf xine.tar .xine**

- Remove .xine directory

	**rm -rf ~/.xine**

- Run Amarok

Now Amarok can play your mp3 tracks.

---

### Post by monkman on 2008-02-14
worked for me....

---

