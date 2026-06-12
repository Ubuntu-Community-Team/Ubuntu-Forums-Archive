---
title: "youtube / google video stalls"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-01-10
hello,

whenever i try and play a youtube or google video, i get the first second or two and then everything stalls (video continues to buffer).

i'm using edgy with flash 9.

any ideas?

thanks,
-steve

---

### Post by raul_ on 2007-01-10
Do you have the latest update installed?

---

### Post by moeFinley on 2007-01-10
This happens to me too, but I can normally watch plenty of videos before it fails.  As I understand it Flash 9 is still beta (?) so I guess this is to be expected.

---

### Post by stevieb on 2007-01-10
latest update of what- flash or edgy?
-steve

---

### Post by flossgeek on 2007-01-10
Flash works fine for me, with flash 9 beta, easily the best version yet by macromedia for Linux as prev versions were just terrible.

Use debs provided here, remove your prev flash FIRST! I haven't used the newer version as mention in the link below, but had no major issues either with the 9.0.21.55 release.
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

To remove flash simply remove the libflashplayer.so libary, do a locate command to find it location

locate libflashplayer.so

and then

sudo rm /your/location/here

---

### Post by raul_ on 2007-01-10
Flash 9 update 2. If you don't know, reinstall just in case, and then try again. 
[Go here]("http://labs.adobe.com/downloads/flashplayer9.html") and then copy the files to your firefox/plugins folder. 

To find that folder do
```

locate firefox/plugins

```

then ```

sudo nautilus
```

navigate to that folder, and copy the files you downloaded.

finally, restart firefox

---

### Post by hal10000 on 2007-01-10
With the latest flash9 (beta) I have no problems at all. It works fine.
If you have the multiverse section enabled in you /etc/apt/sources.list, you can install it via your package manager.
(Or use automatix).

---

