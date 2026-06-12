---
title: "Root help and new user help"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Lucid535 on 2008-01-12
I have just installed this OS and my sound card dose not work. I found a forum post that explains my problem and how to fix it. [HTML]http://ubuntuforums.org/showthread.php?t=546931[/HTML]

But i cant Write in the file i need to because it is READ ONLY.... I have tried to find help on how i can fix this. But my head hurts and its getting late.

How can i Change the folder i need? How do i log into ROOT? 

And if anyone could fill in directions to make it easy please do, everything is new to me so the more detailed the better sorry... and thanks

---

### Post by RomeReactor on 2008-01-12
Hi. To open the file with administrator privileges (root), open a terminal (Applications->Accessories->Terminal) and write or paste:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then enter your password when prompted to. **Gedit** is the text editor, and **gksudo** tells Gedit to open the file with administrator privileges so you can edit it..

---

### Post by mcduck on 2008-01-12
You should probably read this:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

