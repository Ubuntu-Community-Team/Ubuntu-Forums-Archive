---
title: "Ripping CD via lame"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by ed_d on 2005-11-15
Where do I find the codec for ripping cds via lame within soundjuicer? Want to have the mp3 support. I am able to play mp3s within Rhythmbox, but want to rip the cds too.
Thanks,
Ed

edit: Got grip loaded, that should do fine. Would be nice to have lame incorporated within Rhythembox, if anyone can give me a hint, that would be great.

---

### Post by The Mekon on 2005-11-15
I am not sure if this is what you want but it is in the Sound Juicer Help files

"You can click the Edit Profiles button to edit the available audio formats. The profile editor dialog provides direct access to the audio conversion. Profiles are defined with GStreamer pipelines. GStreamer is the underlying multimedia library used by Sound Juicer and other multimedia applications. A full explanation of audio profiles is outside the scope of this document.

If you need to store tracks in the MP3 format (for example, if your portable music player only supports MP3 and not Ogg Vorbis), you will need to create a new profile. To do this, click on Edit Profiles, click New, and name the profile MP3.

Select the MP3 profile and click the Edit button. Set GStreamer Pipeline to
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

Set the File Extension to mp3, and select the Active check box. You will have to restart Sound Juicer to see the new audio profile.

This profile uses the LAME MP3 encoder, so you will need to have the GStreamer LAME plugin installed."

---

### Post by ed_d on 2005-11-15
Well, did just that, so now just have to get a cd to try......

Thanks for the help, will let you know.

---

### Post by Gaming_Junkie on 2005-11-20
I found that goobox is MUCH faster in ripping cds than Sound Juicer ever was.  Sound  Juicer took at least 15 minutes longer per cd (approx. 25 minutes per cd, ridiculous).  Goobox takes 5 minutes maximum regardless of which format you save in.

---

### Post by ed_d on 2005-11-20
Due tell where to get....
Will give it a try.

---

### Post by SighKick on 2005-11-28
> "This profile uses the LAME MP3 encoder, so you will need to have the GStreamer LAME plugin installed."

This is the crunch....how to install a plugin?  I am a complete newbie when it comes to linux but have extensive background in Micro$haft so can follow instructions!

I have downloaded to my desktop lame_3.91-2_i386.deb (I hoped that this was the correct file since Ubuntu is based on Debian?).

Will some kind soul either give me instructions or paste a link to some previously published instructions to install the plugin to Sound Juicer CD Ripper.

Alternatively, where to find Goobox and how to install a new application complete with the lame encoder.

I will keep looking since I have very recently 'found' where the 'SEARCH' function is hiding on this forum.

**You can find the lame MP3 encoder here:-**
[http://users.rsise.anu.edu.au/~conrad/not_lame/]("http://users.rsise.anu.edu.au/~conrad/not_lame/")

---

### Post by ssam on 2005-11-28
have a read through this [http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html) for installing new software.

i recommend grip as a front end to the codecs. it offers lots of control

---

