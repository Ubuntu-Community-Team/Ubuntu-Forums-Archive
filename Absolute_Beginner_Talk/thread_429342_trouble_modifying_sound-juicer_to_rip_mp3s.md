---
title: "trouble modifying sound-juicer to rip mp3s"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-05-01
Hi Ubuntuers:

I just upgraded to Feisty... looks good... and have trouble with getting SOUND-JUICER to rip mp3s.

There is a howto on this at: [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698) however, when I do:

edit > preferences  there is not an mp3 choice in the output format box.

So, I press on the edit profies button... there is an mp3 choice there, but when I choose it and then close the box, it does not show up in the output format box!

ALso, when I press on the edit profiles button, and follow the instructions at [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698) I cannot edit the profile of the newly created output type to give it the  audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux command.

Any suggestions?

Thanks!
Phil Smith
Duluth, GA

---

### Post by lluisanunez on 2007-05-01
Did you read this?
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by stchman on 2007-05-01
> **Phil Smith said:**
> Hi Ubuntuers:

I just upgraded to Feisty... looks good... and have trouble with getting SOUND-JUICER to rip mp3s.

There is a howto on this at: [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698) however, when I do:

edit > preferences  there is not an mp3 choice in the output format box.

So, I press on the edit profies button... there is an mp3 choice there, but when I choose it and then close the box, it does not show up in the output format box!

ALso, when I press on the edit profiles button, and follow the instructions at [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698) I cannot edit the profile of the newly created output type to give it the  audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux command.

Any suggestions?

Thanks!
Phil Smith
Duluth, GA

Follow my procedure if you want Juicer to rip your audio CDs to MP3 format:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Hope this helps.

---

### Post by Old Jimma on 2007-05-02
Hi GUys:

After following your directions, Sound-juicer still does not allow me to make any edits to a output type that I create named "mp3." For example, I cannot put my cursor in any of the boxes named "profile name," "description," or "pipeline."

Golly!
Phil Smith
Duluth, A

---

### Post by stchman on 2007-05-02
> **Phil Smith said:**
> Hi GUys:

After following your directions, Sound-juicer still does not allow me to make any edits to a output type that I create named "mp3." For example, I cannot put my cursor in any of the boxes named "profile name," "description," or "pipeline."

Golly!
Phil Smith
Duluth, A

Remove Sound Juicer and all of its dependies and the reinstall it.  This may cure the problem.  I believe that there is a ~/.juicer folder in your /home directory.  Delete that as well.

---

### Post by hoot on 2007-05-02
I am also having this same exact issue.  I am able to rip CD's using Goobox with no problem, just not Sound Juicer. I have followed all of the instructions on this thread as well as others and it still does not work.

In addition to the problem that the original poster had, once I have that window open, I am unable to even close the dialog boxes.  I have to right click the windows on the bottom task bar and select close.  

I will continue to work on this and post the solution if I am able to fix it.

---

### Post by ntetreau on 2007-05-02
Hi guys, this is done much better in Feisty, the mp3 profile is already prepared for you although not enabled by default.  To enable it, jus install gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-ugly-multiverse and lame.  Then, you can you the mp3 profile without further config.  Good luck!

Nic

---

### Post by Toddy on 2007-05-02
Hi Nic.  Can you post that default Feisty mp3 profile for Sound Juicer?  I ended up deleting mine before I realized I was just missing the appropriate plugins.  I would like to restore the default profile.  Thanks...

---

### Post by Old Jimma on 2007-05-02
Hi All:

ntetreau  provided the solution that works!!! Many thanks!

ntetreau, how did you know it would work?

Phil Smith
Duluth, GA

---

### Post by ntetreau on 2007-05-03
I knew about the solution because I posted a question about it a few months back int he Fesity forum, someone else answered exactly what I wrote up there!  

Here's the default mp3 profile in Fesity:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

---

