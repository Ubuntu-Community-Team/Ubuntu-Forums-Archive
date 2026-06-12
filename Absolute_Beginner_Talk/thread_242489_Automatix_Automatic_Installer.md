---
title: "Automatix Automatic Installer"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by pink_taco on 2006-08-23
I'm running Dapper Drake....  I am trying to install Automatix, but am confused.  The instructions are as follows:

Open up terminal and paste the following lines one after the other (wait for each command to finish before you paste the next)

wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer
  
Do I simply paste those lines, one after another like the instructions say?  What is the purpose of the document that is shown when you click the link in the first line?  I had a previous thread about this, but I think there was a deeper prolem with my repositories....  I've simply reinstalled the OS, and installed all of the updates.  Before, on my previous installation, I had problems downloading the automatic updates and had a problems with my "sources.list" or something like that.  Everything is okay now.  Before, I think the errors with the automatix installer were stemming from the sources.list issue.   I'm rambling..  Anyway, back to the original question, do I just copy and paste those lines one after another, or is there more to it?  :confused:

---

### Post by reacocard on 2006-08-23
yep. just copy/paste. the commands download a script (the document), then make it executable, then execute the script.

---

### Post by pink_taco on 2006-08-23
Thanks a lot, Reacocard.  The install went perfectly.  I'm running Automatix as we speak!  I'm aware that I'm not supposed to install the AUD-DVD codecs because of legal issues.  I've noticed that there are lots of programs that are similar.  Like Bittorent clients, for example.  Do you recommend installing everything but the illegal codecs or are there programs in there that would have conflicts with each other?  I've got my windows partition mounted and I can read it from Linux.  When using Windows, I used media player to organize and play all of my music.  The music is ripped in .wma format.  What is the best option for listening to/organizing those files from  Ubuntu?  Do I need to convert them to .mp3 format?

---

### Post by reacocard on 2006-08-23
you don't need to convert them. any player using gstreamer or xine (my favorite is [exaile]("http://www.exaile.org")) should be able to play .wma files, given the right codecs. in fact, you can't convert them under linux without the codecs, since the converter relies on gstreamer. i'd reccomend just re-ripping to mp3 from the cds where possible, and otherwise leaving it in wma. note that linux players won't be able to handle DRM-protected wma files. if you want to convert sound files, soundconverter works well, and is in the repos. it can convert any format supported by gstreamer to mp3, ogg, flac or wav.

As for the other apps, just install what you want, and leave the rest. I beleive there's some beta (firefox & gaim, both 2.0) software in there you would want to leave. none of the software should have any conflicts though, so if you want to install them all, go ahead.

---

