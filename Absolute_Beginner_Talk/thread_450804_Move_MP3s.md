---
title: "Move MP3s"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-21
How would I move a bunch of mp3s from one folder ~/Desktop/Music to ~/My\ Music. Preferably command line. Heres the catch, theres other files not mp3s, im only interested in the mp3s.

---

### Post by taurus on 2007-05-21
```
mv ~/Desktop/Music/*.mp3 ~/"My Music"
```

---

### Post by Inxsible on 2007-05-21
> **Nekiruhs said:**
> How would I move a bunch of mp3s from one folder ~/Desktop/Music to ~/My\ Music. Preferably command line. Heres the catch, theres other files not mp3s, im only interested in the mp3s.

```

sudo mv /Desktop/Music/*.mp3  /"My Music"

```

I think that should do it although I am not sure if you would need to do a sudo

---

### Post by Nekiruhs on 2007-05-21
I dunno whats going on but im getting an error on both:
```
administrator@KBUNTU:~$ mv ~/Desktop/Music/*.mp3 ~/"My Music"
mv: cannot stat `/home/administrator/Desktop/Music/*.mp3': No such file or directory
```

---

### Post by taurus on 2007-05-21
What's the output of this command?

```
ls -la ~/Desktop/Music/*.mp3
```
Are those files you want to move end with mp3 extension, filename.mp3?

---

### Post by Nekiruhs on 2007-05-21
```
administrator@KBUNTU:~$ ls -la ~/Desktop/Music/*.mp3
ls: /home/administrator/Desktop/Music/*.mp3: No such file or directory
```

Maybe im doing something wrong.

---

### Post by taurus on 2007-05-21
```
ls -la ~/Desktop/Music
```

---

