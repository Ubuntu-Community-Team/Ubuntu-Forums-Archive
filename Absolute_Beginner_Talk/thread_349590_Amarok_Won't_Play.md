---
title: "Amarok Won't Play"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by jpoRS on 2007-01-30
Hey,

I am running Edgy on my hp laptop, and I am having a difficulty with amarok.  It starts up fine, but a few seconds after it opens, I get an error message telling me that amarok doesn't have mp3 support.  I click the install support button, and nothing happens.  Amarok will not play any file, mp3, .ogg, or any other format.

I have searched the forums several times and have found several people with the same problem.  Most of them seem to have solved their problem, but no one gives a clear explanation of what they did.  Does anyone know what is causing this problem?

jim

---

### Post by mrbungle on 2007-01-30
im a new user but had the same problem.  i believe you have to install the restricted formats?  something like that.  search the synaptic for it and you should find it.


after i installed that.  it would play the mp3:D

---

### Post by orb9220 on 2007-01-30
Or try automatix in your menu system tools>

There you can install all the video and audio codecs your system needs.

---

### Post by jpoRS on 2007-01-30
I have all of my codecs installed.  And reinstalled since the problem started.  It isn't a restricted format issue, because it used to play mp3, and now it won't play mp3 OR ogg.

jim

---

### Post by Cobikegeek on 2007-01-30
Go to this site for info on installing restricted formats.  

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Then use synaptic to install what you need for the specific app you're using.

---

### Post by jpoRS on 2007-01-30
I have tried that.  It isn't a restricted format issue.  mp3s did work in amarok, but now they don't.  Ogg files, which aren't restricted (right?) don't work either.



jim

---

### Post by nbayiha on 2007-02-01
Did you install you mutimedia codecs pack ? if not go this page

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

or try this in the terminal, i guess it should solve your problem.

```

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

---

### Post by dorcssa on 2007-02-01
Try to reinstall amarok, maybe it helps.

---

### Post by jpoRS on 2007-02-01
Tried reinstalling amarok already, and that terminal thing didn't help, everything is up to date.

See why I am frustrated?

jim

---

### Post by Cobikegeek on 2007-02-01
Have you checked your amarok configuration?

Under settings->configure amarok->engine

Sound system should be: xine engine
output plugin should be: autodetect

and libxine-extracodecs must be installed.

If all that is good, then have you tried to play mp3 files with Banshee or Rhythmbox just to verify?  That's all I can offer. Good luck.

---

### Post by jpoRS on 2007-02-01
amarok is configured correctly, and rhythmbox works fine.

jim

---

### Post by theoldgit on 2007-02-01
I had a similar problem.
Try removing the ~/.kde folder (To wastebasket so you can restore it).
If that wont work try removing ~/.xine (again to the wastebasket so you can restore it).

You will then have to tell Amorak where the music is, so be patient while that goes on. I hope this works as it did for me.

If these dont work, then put the two folders back and you will be back where you were.

---

### Post by jpoRS on 2007-02-01
YES! Ditching .xine did it!  I cannot tell you how grateful I am!

jim

---

### Post by theoldgit on 2007-02-02
I can understand how greatful you are, the same thing happened to me. Its worth changing to Linux just for Amarok. Anyway glad it worked and thanks for letting us know.

---

### Post by SunRa on 2007-02-12
Hello,

Where can I find the .xine folder? I guess i don't have a .kde file since using xubuntu...?

I have the same problem with amarok, and nothing help...

---

### Post by jpoRS on 2007-02-14
Go to Places> Home Folder.

Press CTRL+H or go to View and select "Show Hidden Folders".

Find the .xine folder, and move it to your desktop.

Restart Amarok, and you are fixed!

Let me know if this doesn't work out.

And you would have a .kde folder, Amarok creates it when you install Amarok.  I had it and I am running regular Ubuntu.  However you might not need to do anything about .kde, I didn't.

Hope this helps.

jim

---

### Post by i_am_root on 2007-04-01
I was having a similar problem with amarok, but when i looked in my .xine folder there was a file with no extension called win32registry. That file had no extension on it though and amarok started working just fine again once I deleted that file.

---

### Post by InuyashaDuelist on 2007-04-01
Oh, so that's what the problem was. Around the same time the topic starter had this problem, I had the very problem. Except, I couldn't fix it. I just left Kubuntu for a month and came back, and it was fixed somehow. Maybe it was in the updates.

Good thing we've all got it fixed, though. >_>

---

### Post by VeVhLoS on 2007-06-03
had the same problem suddently one morning.
i installed libxine1-ffmpeg which replaces libxine-extracodecs as Cobikegeek suggested and everything works now.
thanks!
ps.i run debian unstable

---

