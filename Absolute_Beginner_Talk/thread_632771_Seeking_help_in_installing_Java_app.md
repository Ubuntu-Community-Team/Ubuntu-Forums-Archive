---
title: "Seeking help in installing Java app"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-12-05
I am trying to install a Java app called MusicMagicMixer in my Fiesty box. 

After downloading it, it's sitting on my Desktop.  I believe I've  already uncompressed the tarball.  Already searched this and the MusicMagic forums, but didn't see anything that looked like and answer to this question.

Here is what I did so far:
1. Downloaded MusicMixer_x86_1.8.tgz from [http://www.musicip.com/mixer/index.jsp](http://www.musicip.com/mixer/index.jsp) to my desktop.
2. Used gzip to uncompress it.
3. I now have an icon that looks like a box called MusicMixer_x86_1.8.tgz on my desktop
4. It contains folder called MusicIP.  That folder (MusicIP) contains another folder called MusicMagicMixer
5. The MusicMagicMixer folder contains several other directories and files, none of which appear to be compressed.

My immediate goal is to install the app in my system.  I know that once that is done I will need to do some more tweaks probably involving JAVA_HOME.  

But for now, my goal is to get this installed.  Any help would be greatly appreciated.

---

### Post by vikram on 2007-12-06
not familiar with this app but search for jar files and run them as 

java -jar jar-file-name

---

### Post by m9ke on 2007-12-06
Thanks, vikram!

Actually, last night I looked at this again.  I right-clicked on MusicMixer_x86_1.8.tgz and chose a decompressing option (can't remember exact wording-at work now).

The folder MusicIP then appeared on my desktop.

I was able to get the executable in that directory to *try* to run via the command line.

I got the expected JAVA_HOME error.

My next step will be to choose a location other than the desktop for the directory MusicIP, move it there, and then sort out the JAVA_HOME issue.

Thanks,

m9ke

---

