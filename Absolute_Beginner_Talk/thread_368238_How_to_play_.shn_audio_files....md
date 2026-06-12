---
title: "How to play *.shn audio files...?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by funkadelic on 2007-02-23
What is the easiest way to play Shorten (*.shn) audio files in Ubuntu?

---

### Post by deadgobby on 2007-02-23
Not to sound mean or any thing. But Google can be a powerful tool.
[http://www.google.com/search?q=%28*.shn%29+audio+files+in+Ubuntu%3F&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=%28*.shn%29+audio+files+in+Ubuntu%3F&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)
Gobby

---

### Post by funkadelic on 2007-02-23
I tried google -- all I found was a compile-it-yourself plugin for XMMS.

Click that link and see for yourself. I resent the implication that I would ask without even doing a google search.

---

### Post by dmber on 2007-10-31
same thing for me.  and i can't get the xmms plugin to compile.  "no make file" error.

i really need to play shn files.  i have almost 100 gigs of live music in .shn format.

thanks.

---

### Post by cozmic charlie on 2007-10-31
You might want to give this a try [http://ubuntuforums.org/showthread.php?t=501509&highlight=shn](http://ubuntuforums.org/showthread.php?t=501509&highlight=shn).  It works for Fiesty or Gutsy.  Linux is not very shn friendly.  The only player app I have found to play shn is xmms.  In Fiesty there is an xxms plug-in in the repos but not in Gutsy.  However, I did get it to work using the above how to.  You need to download and install both the xmms plug in and the shn codec from their site and install them.  Try it and post back if you are having problems

---

### Post by n3tfury on 2007-10-31
i believe vlc plays .shn files.

---

### Post by swoskow on 2007-10-31
> **n3tfury said:**
> i believe vlc plays .shn files.

If it does that would be new to me.  Maybe I missed a plug in somewhere.  I'll check it out.

---

### Post by swoskow on 2007-10-31
> **dmber said:**
> same thing for me.  and i can't get the xmms plugin to compile.  "no make file" error.

i really need to play shn files.  i have almost 100 gigs of live music in .shn format.

thanks.

This might help [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) - scroll down and find the section on installing from source package.  It will walk you through the entire process, even has a video.  Post back if you still have a problem.

---

### Post by thelawoffives on 2008-06-09
You can get the shorten app here: [http://etree.org/shnutils/shorten/](http://etree.org/shnutils/shorten/) , build it and from the command line: $ shorten -x file.shn file.wav Now you will have wav files that you can play or compress to mp3/ogg or whatever.

This worked well for me.

---

