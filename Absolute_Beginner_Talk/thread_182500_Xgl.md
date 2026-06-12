---
title: "Xgl"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-26
I saw a demo film about xgl and I loved it ( who dont's hehehe ) and i want to ask what kind of hardware, and software too, i need to run xgl.

---

### Post by richbarna on 2006-05-26
Yep, I got it ALL, Lovely !!! :)
Follow this guide.
[http://www.ubuntuforums.org/showthread.php?t=148351]("http://www.ubuntuforums.org/showthread.php?t=148351")

---

### Post by Simian on 2006-05-26
But if I use XGL will my Nvidia drivers still work properly?
Ultimately, will I still be able to run Quake 4?

---

### Post by richbarna on 2006-05-26
I am not a gamer, but due to the resources that compiz uses, I don't think so.
However, instead of using the compiz desktop, why not create a new user, and use that desktop for games instead?
Just a suggestion.
When I don't want to use the compiz in the background, I just do a console login with "startx" and it takes me to my standard desktop without compiz enabled.

---

### Post by kart3r on 2006-05-26
I can't find the files depdebs.tar.gz, compiz and compiz-gnome :S Can you help me?

---

### Post by Rinzwind on 2006-05-26
[QUOTE=richbarna]I am not a gamer, but due to the resources that compiz uses, I don't think so.
However, instead of using the compiz desktop, why not create a new user, and use that desktop for games instead?
Just a suggestion.
When I don't want to use the compiz in the background, I just do a console login with "startx" and it takes me to my standard desktop without compiz enabled.[/QUOTE]
COMPIZ allows you to switch to metacity and to restart compiz server with 1 click.

---

### Post by bruce89 on 2006-05-26
[QUOTE=Simian]But if I use XGL will my Nvidia drivers still work properly?
Ultimately, will I still be able to run Quake 4?[/QUOTE]
If you have XGL going, no; as it disables direct rendering, which means 3D.

---

### Post by kart3r on 2006-05-26
On the tutorial at some time he said to execute kdesu kate but appears this errors and opens a blank text page

acunha@acunha-desktop:~/Desktop$ kdesu kate
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
ScimInputContextPlugin()

---

### Post by Simian on 2006-05-26
OK I followed the how to and managed to get XGL and Compiz working. I was really impressed.

I switched back to metacity with:

```
metacity --replace
```

but I still wasn't able to run 3D games.

---

### Post by Scunizi on 2006-05-26
I just cought something in the "One threat that rules them all" about Compiz & xgl.  For games like quake and ut that require full screen there is a way to boot 2 xservers at the same time and hot key between them without switching users.  Unfortunatly, I'm on a windows box and limited in time to look for the link.  Post back if you get it working as I'd like to play UT2004.

---

### Post by richbarna on 2006-05-26
[QUOTE=Rinzwind]COMPIZ allows you to switch to metacity and to restart compiz server with 1 click.[/QUOTE]
 Ok, for the benefit of the rest of us, would you like to share that "1 click" knowledge with us?
Or is that as far as your information goes?
Or maybe it's a game where we all just click loads of stuff until we find it, or shall we "google" xgl compiz, one click super commands.

I'm not being funny, but this is the absolute beginners forum, and if someone has to post a comment, it's nice to back it up with some info for us newbies.

I see your sig says that your posts come with no warranty, maybe some information instead then. :)

---

### Post by Scunizi on 2006-05-27
I don't know about 1 click, but here's a link to the right forum thread.  Take a look at message 1045 at the bottom there are a couple of links for different methods of attacking this problem....  [http://www.ubuntuforums.org/showthread.php?t=131267&page=105]("http://www.ubuntuforums.org/showthread.php?t=131267&page=105")

---

