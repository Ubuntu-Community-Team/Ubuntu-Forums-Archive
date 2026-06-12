---
title: "file type assosiantions"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by mybeat on 2005-12-23
im sorry if the simmilar thread was here .. 
can someone help me with one problem please,
i have isntalled vlc and when i dclick on  .avi or simillar icon it opens up totem 
how to do so that vlc will be launched instead of totem ? , and where is this information stored? 
and another thing from keyboard shortcuts "launch music player" launches rhitmbox  but i wanna just bmp instead
how to do so ? 
how to disable time synchronization during boot ? 

thanx

---

### Post by Perfect Storm on 2005-12-23
right click on the .avi file and click **properties**. choose **open with** tab nad click the **add** tab. 
Pick **Use a costum command** and write **wxvlc** Now you can choose it in **open with** tab. That's it :)  and now vlc will open .avi files instead of totem.

If you want VLC to automatically start up when inserting a DVD:
**System** ---> **Removalble Drives & Media**. Click **multimedia** tab. Under **Video DVD Discs** write in the command box: **wxvlc dvd:///dev/dvd**

---

