---
title: "Crazy Tovid"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-14
i converted an avi video with tovid, and then made an iso of the new file.  the weird thing was that the iso became like 8.5 GB large, even though the original avi was only like 1.3 GB large...........how am i supposed to be able to burn an 8.5 GB file onto a dvd???](*,) (sarcastic)

---

### Post by nalmeth on 2006-05-14
with a dual-layer DVD 

you might have missed something, though I wouldn't know what. I've never used tovid.

If it helps, you might want to try [devede]("http://www.rastersoft.com/programas/devede.html")

---

### Post by user1397 on 2006-05-16
i figured out that when you make an iso image of a video file, it creates a "dvd" folder in /home.  that folder kept on building up all of the video files combined, so it kept getting bigger. now i know that after every video i make an image out of, i have to delete that "dvd" folder. as simple as that.
here is a link on my troubles and solutions with tovid:
[How to Correctly burn movie DVD's using K3B]("http://www.ubuntuforums.org/showthread.php?t=169825")
(Follow openmind's advice especially)
Oh and by the way I can't even install devede! it won't let me ./configure, make, make install, checkinstall, etc.!

---

### Post by ash211 on 2006-05-17
[QUOTE=erik1397]Oh and by the way I can't even install devede! it won't let me ./configure, make, make install, checkinstall, etc.![/QUOTE]

Try installing the build-essential package before running those commands:
```
sudo apt-get install build-essential
```

If that doesn't work, it may be a GCC version problem, which I'm not too familiar with.

---

### Post by user1397 on 2006-05-17
[quote=ash211]Try installing the build-essential package before running those commands:
```
sudo apt-get install build-essential
``` 
If that doesn't work, it may be a GCC version problem, which I'm not too familiar with.[/quote]
i do have the build-essential package, and the checkinstall package, but both didn't work.  it must be a GCC version problem like you said.
no matter though, i don't need devede, cause ive got tovid, and it works perfectly for me.

---

### Post by ash211 on 2006-05-18
I think I may have found the reason it wasn't working, for those who see this later:

```
andrew@Dell8400Kubuntu:~/Downloads/devede$ ls
devede.desktop  devede.glade  devede.gladep  devede.png  devede.py  docs  install.sh  pixmaps  po
andrew@Dell8400Kubuntu:~/Downloads/devede$
```
Configure, and make scripts aren't in the directory, so those commands don't apply here.  I ended up installing the package with a simple
```
sudo ./install.sh
```

---

### Post by joshrobinson on 2006-05-19
just for the record, devede gave me horrible audio sync problems. so i stick with tovid, real nice program once you figure it out

---

### Post by user1397 on 2006-05-19
[quote=joshrobinson]just for the record, devede gave me horrible audio sync problems. so i stick with tovid, real nice program once you figure it out[/quote]
I agree 100% with your statement:D

---

### Post by joshrobinson on 2006-05-19
[QUOTE=erik1397]I agree 100% with your statement:D[/QUOTE]

doesnt take too long either :-P

---

### Post by az on 2006-05-19
[QUOTE=joshrobinson]just for the record, devede gave me horrible audio sync problems. so i stick with tovid, real nice program once you figure it out[/QUOTE]
I read that you could actually play around with the audio sync using devede (to adjust it if misaligned), something you cannot do with Tovid.  As you can see, I have yet to run devede....

---

### Post by user1397 on 2006-05-19
[quote=joshrobinson]doesnt take too long either :-P[/quote]
actually, what is there to figure out if you use the tovid gui? (like me:D)

---

