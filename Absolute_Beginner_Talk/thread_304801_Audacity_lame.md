---
title: "Audacity lame"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by deadgobby on 2006-11-22
OK for the life of me I do not recall how to get libmp3lame.so to work. I know it is looking for it, but how to invoke it I draw a blank. I am trying to take some old recordings and convert them to MP3 for mat. Lame is installed. So I am Ugg. ](*,) 
Gobby

---

### Post by paul6 on 2006-11-22
> **deadgobby said:**
> OK for the life of me I do not recall how to get libmp3lame.so to work. I know it is looking for it, but how to invoke it I draw a blank. I am trying to take some old recordings and convert them to MP3 for mat. Lame is installed. So I am Ugg. ](*,) 
Gobby

```
sudo aptitude install liblame-dev
```

Than, the libmp3lame.so you need should be in /usr/lib

Paul

---

### Post by deadgobby on 2006-11-22
> **paul6 said:**
> ```
sudo aptitude install liblame-dev
```

Than, the libmp3lame.so you need should be in /usr/lib

Paul
Oh yes that was the ticket. BIG THANKS
Gobby

---

### Post by mtyoung on 2006-12-02
Thankyou, Paul6.
It worked fine for me on Ubuntu 6.04.

Mark

---

### Post by rockprincess on 2006-12-10
hello all,

i just figured out how to import the lame codec without having to install the liblame-dev package (which actually is just for developers).

you have to install the package liblame0, and then you start Audacity.

You go into the properties...(I only have the german version of it but it must be something like this...) 

Edit --> Properties/Options --> File Format --> and then at the Bottom it says "MP3 Exportoptions" or something like that..then you go SEARCH LIBRARY and search for libmp3lame.so.0.0.0 (that's the exact name)
note: Make sure you activate "Extended Libraries *.so" otherwise you have to go through every single file in /usr/lib ;)

that should work!

---

### Post by gboursiquot on 2006-12-11
I don't have the file(libmp3lame.so) in my usr/lib directory how do I get it there?

---

### Post by Mortuis on 2006-12-14
> **rockprincess said:**
> hello all,

i just figured out how to import the lame codec without having to install the liblame-dev package (which actually is just for developers).

you have to install the package liblame0, and then you start Audacity.

You go into the properties...(I only have the german version of it but it must be something like this...) 

Edit --> Properties/Options --> File Format --> and then at the Bottom it says "MP3 Exportoptions" or something like that..then you go SEARCH LIBRARY and search for libmp3lame.so.0.0.0 (that's the exact name)
note: Make sure you activate "Extended Libraries *.so" otherwise you have to go through every single file in /usr/lib ;)

that should work!

Thanks rockprincess, that worked perfectly for me.

---

