---
title: "No MP3 Library for Audacity"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by dipetersen on 2006-07-05
I am very new to Ubuntu and Linux in general. I am specifically setting up a computer to record audio. I found out about Ubuntu and thought I would give it a try. So far so good!  I figured out how to install audacity but when I try to save the recording as an MP3, it says that there isn't an MP3 library installed.  I am familiar with the LAME DLL in windows and have my windows machine configured to use that.  What library is used on a Linux machine and where would I find it? 

Thank you.

Dave Petersen

---

### Post by ed_d on 2006-07-05
You may have to install the codecs:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by christhemonkey on 2006-07-05
```
sudo apt-get install liblame0
```

Then you will need to select the right library with audacity, under the settings thing somewhere. (i forget where!).

Then you will need to select find library, and in the open dialog, change it to look for all files instead of just the 1 it wants.

Then choose the file with a name pretty much exactly the same.
And voila!


(Sorry about the vagueness of those instructions! Not done that for a very long time, and dont currently have it installed so cant do it myself)

---

### Post by ajgreeny on 2006-07-05
Although the info above is helpfull, I think you need to go to this page and follow the instructions there because the file you are looking for is not quite how it's done now.  Good luck - it all worked for me once I got past this problem.

[http://ubuntuforums.org/showthread.php?t=86948&highlight=audacity+mp3](http://ubuntuforums.org/showthread.php?t=86948&highlight=audacity+mp3)

For more info justdo a forum search on "audacity mp3" and lots of stuff will surface.

---

### Post by dipetersen on 2006-07-05
Thank you. 

Both reply's helped my understanding on what to do.

I will try it this evening.

Regards

Dave Petersen

---

