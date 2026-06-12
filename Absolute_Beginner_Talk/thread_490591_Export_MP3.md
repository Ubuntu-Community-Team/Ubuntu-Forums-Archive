---
title: "Export MP3"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-07-02
Ok what should I do with this ?

Audacity does not export MP3 files directly, but instead uses the 
freely available LAME library to handle MP3 file encoding.  You must 
obtain libmp3lame.so separately, either by downloading it or building 
it from the sources, and then locate the file for Audacity.  You only 
need to do this once.

---

### Post by yagood on 2007-07-02
Install the "liblame0" package through Synaptic.

---

### Post by burt_57 on 2007-07-02
I have done so.
no matter what I do it keep asking
for libmp3lame.so, after I have done some editting of a file ( mp3 )
and try to export it to a different folder.

---

### Post by yagood on 2007-07-02
I installed audacity to try to reproduce your problem and while exporting it's asking "Do you want to locate liblame0.so?". Then I select liblame0.so and export goes fine.

EDIT:

Ooops, my bad, the library file is called libmp3lame.so.0 and lives in /usr/lib/ BTW.

---

### Post by burt_57 on 2007-07-02
How do you select libmp3lame.so.0 .
I did a seach for it and found it , 
But when I found it nothing happen.

---

### Post by yagood on 2007-07-02
When you select "Export as MP3" option in Audacity, does it ask you to locate lame library? If yes, choose yes and then browse to find the library, select it, click OK, then it probably will complain about different library file name than expected, but that doesn't matter, because export should work anyway.

If it doesn't ask you about lame library location, what version of Audacity do you use?

---

### Post by burt_57 on 2007-07-02
select it, click OK, 
It does not allow me to click OK because it is not there ( ok )<.....
All I see is where it is that is that is all, I open the location folder
but for the life of me so many folder that I do not know what to do.
Hey thank for helping.
Could be me , I am new to Linux and trying to get away fro Windows all together.

---

### Post by yagood on 2007-07-03
You need to find a file named "libmp3lame.so.0" in this dialog, I know there's a lot of files there, but if you installed "libmp3lame0" package, then libmp3lame.so.0 should be there too, just scroll thorugh the list and select it.

---

### Post by r3bol on 2007-07-14
I'm having a problem with this too. 
libmp3lame0.so is in usr/lib (i can see it via the ubuntu file browser), but the audacity browser is not picking it up. I have even tried show hidden files.

---

### Post by jonlemur on 2007-07-16
I just downloaded and installed Audacity today, and got exporting to mp3 via LAME to work.  First, you don't have to show hidden files, but (except for the extra files you'll have to look through) it couldn't hurt.  Second, I had to change the box that says "Only libmp3lame.so" to "Extended Libraries (*.so*)."  Note that the "lib" files don't exactly go in alphabetical order as it makes a distinction between upper and lower case, so you will have to navigate past quite a few lib files.  Now that I think about it though, you could probably just put in the name "libmp3lame.so.0" into the text box and click "OK."  (I actually just tried that, and it seems to work.)  And BTW, I am in /usr/lib, but that should be default.  And just to try to be thorough, I am running Gnome in Dapper Drake and have LAME, liblame0, and LAME-EXTRAS installed through Synaptic.

I hope all that helps

---

### Post by stchman on 2007-07-16
> **burt_57 said:**
> Ok what should I do with this ?

Audacity does not export MP3 files directly, but instead uses the 
freely available LAME library to handle MP3 file encoding.  You must 
obtain libmp3lame.so separately, either by downloading it or building 
it from the sources, and then locate the file for Audacity.  You only 
need to do this once.

I use Sound Juicer to rip CDs to MP3s.  Follow this procedure to do it.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Hope this helps.

---

