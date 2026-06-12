---
title: "is there a way to make my pc beep when compiling is done.. or any command line task?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-12
I know I can do 

  command1; command2;

Is there a system beep command?  just so I will be alerted?

---

### Post by emarkd on 2008-02-12
Not sure about the beep, but you could find an appropriate wav or mp3 and play it using mplayer:

```

command1 && mplayer beep.wav

```

---

### Post by joesmith1234 on 2008-02-12
i got it with 
  sudo apt-get install beep

make; beep;

;)

---

### Post by apetresc on 2008-02-12
For extra nerd points, just pipe stuff into your sound card ;)
```
make ; cat Makefile > /dev/dsp
```
Not quite a beep but it'll get your attention!

---

### Post by Dr Small on 2008-02-12
Or:
```
command1; echo -e "\a"
```

---

### Post by Christmas on 2008-02-12
Instead of beep you can also try a CLI player, like ogg123 or mpg123.

---

