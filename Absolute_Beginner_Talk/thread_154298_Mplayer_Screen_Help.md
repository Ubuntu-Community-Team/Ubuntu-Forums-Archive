---
title: "Mplayer Screen Help"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-02
is there a way to streach the videos in mplayer because when i make the screen bigger the video stays the same size

---

### Post by taurus on 2006-04-02
You can either change the option in ~/.mplayer/gui.conf to vo_driver = "xv" (should be the second line in it)...  Or try this one then,
```

echo "zoom=yes" >> ~/.mplayer/config

```
Then, fire up mplayer again and see if it works with fullscreen...

---

### Post by gabruo on 2006-04-02
Thanks, was just having the same problem the code worked great.:)

---

### Post by taurus on 2006-04-02
[QUOTE=gabruo]Thanks, was just having the same problem the code worked great.:)[/QUOTE]
Glad to hear it also worked for you too.

---

### Post by slipk487 on 2006-04-02
thx i couldnt use this
~/.mplayer/gui.conf to vo_driver = "xv"
but this worked 
echo "zoom=yes" >> ~/.mplayer/config

---

### Post by taurus on 2006-04-03
[QUOTE=slipk487]thx i couldnt use this
~/.mplayer/gui.conf to vo_driver = "xv"[/QUOTE]
It means that you edit your ~/.mplayer/gui.conf and change whatever driver you use to xv!!!
```

gedit ~/.mplayer/gui.conf

```

---

### Post by slipk487 on 2006-04-03
the first time i used 
```
gedit ~/.mplayer/gui.conf
```
it didnt work but after using 
```
echo "zoom=yes" >> ~/.mplayer/config
```
it worked

---

