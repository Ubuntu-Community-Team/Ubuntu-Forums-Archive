---
title: "How to compile a binary file?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-10-13
I know this has been asked many times before but I couldn't find anything about it with search so I'll ask.

I started out trying to find liblamemp3.so for my Audacity program. I found the /usr/lib/liblamemp3.so.O file but was not sure if that was what was needed. So I went online and downloaded the lame file from fluendo.

I'm not sure, but it seems this is a binary file as it will not open with any apps. So if someone knows for sure what this file is and what I need to do with it, I would certainly appreciate some help. 

The name of the file is:
 download.php?
 order=14138&id=14
 667&osCsidjd9rkdk
ibihtcgeaeb1h0lold5

---

### Post by avik on 2007-10-13
The liblamemp3.so.O file should be the same.  Try a symlink:

```

cd /usr/lib/
sudo ln -s liblamemp3.so.0 liblamemp3.so

```

EDIT: Actually, the filename might be liblamemp3.so.0 (zero at the end).  I changed it above.  Thanks por100pre1.

---

### Post by por100pre1 on 2007-10-13
Not sure about this, but I think it's liblamemp3.so.**0**    :-k

---

### Post by avik on 2007-10-14
Thanks.  I think so as well.  I changed the post to reflect that.

---

### Post by rsnow on 2007-10-14
O.K., I tried the symlink only to realize that I had the file name wrong. It is supposed to be libmp3lame.so not liblamemp3.so. After doing some more research I decided to try the easy way.

I went to synaptic package manager and did a search for lame. I marked lame for install and clicked 'apply'. After spm did its thing, I went to /usr/lib and found libmp3lame.so.0. When Audacity asked if I was sure I wanted to use libmp3lame.so.0 instead of libmp3lame.so I said yes. Audacity went ahead and exported the file as mp3. I checked the file on Rhythmbox and it played fine. So I guess libmp3lame.so.0 works.

Now I need to figure out why Audacity doesn't sound right when it plays audio files. It sounds like it is playing in slow motion. The cursor moves slowly and the sound is like a low pitched twang.

I may just uninstall and reinstall.

---

### Post by rsnow on 2007-10-14
Well, uninstall and reinstall didn't work. Everything seems to work OK except the speed of playback. Has anyone else had this experience?

---

### Post by rsnow on 2007-10-19
To update and close this thread...I just checked Audacity again and now it is working. I'm happy but still puzzled as to why it didn't want to play nice at first. As they say, "All's well that ends well".

---

