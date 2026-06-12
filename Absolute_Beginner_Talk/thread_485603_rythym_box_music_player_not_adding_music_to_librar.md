---
title: "rythym box music player not adding music to library"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by kerbantez on 2007-06-27
k im a noobie at ubuntu still. i created a dual boot for windows xp and ubuntu overwriting my old kde mandrake version of linux and putting ubunut in its place. im loving ubuntu. i just wanted to kno why the rythym box music player isnt adding any files to my library. 

p.s. the files are located on a windows partition. but i dont think it would make a difference.

---

### Post by Golyadkin on 2007-06-27
Try unfolding "Library> Import Errors" and see if there is an error message. I am having no problems with 30GB of music on a NTFS drive. I am using Feisty 64bit and Rhythmbox from the repository. Do you have read permissions on the Windows drive?

---

### Post by zanglang on 2007-06-27
If your files are Windows audio formats (.wma etc ) make sure you've installed the codecs for them, or Rhythmbox wouldn't be able to recognize them.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by sandeep108 on 2007-06-27
In my case, every time I need to access the windows partition, ubuntu asks for my password. Only then I can import the files into rhythmbox. I suspect that is the reason it is not able to on start-up.

---

### Post by kerbantez on 2007-06-27
thanks yes there is .wma format songs but only a few. most of them are .mp3 format and they wont be added to rythym box. ive noticed that it did add a few songs but they were in .wav format. 
and yes i have permissions to read the windows drive. 

so would i need to install the .mp3 codec or shouldn't that already be there?

i appreciate the feedback

---

### Post by LancerDragoon on 2007-06-27
Yes, you need to install the proper gstreamer codecs to enable MP3 playback support. To do this, go to Applications -> Add/Remove... and in the window that pops up, search for mp3. On the top-right corner, ensure that you choose to list All Available Applications.

---

### Post by kerbantez on 2007-06-27
hey thanks rythym box is working fine now

---

