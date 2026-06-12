---
title: "fonts for tovid"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-01-21
hi,
i'm trying to extend the fonts available to tovid (in particular its frontend tovidgui).
I'm following instructions of page [http://tovid.wikia.com/wiki/Tovid_FAQ](http://tovid.wikia.com/wiki/Tovid_FAQ) so i've downloaded
 imagick_type_gen.pl and run by terminal

imagick_type_gen.pl > ~/.magick/type.xml

but i got only

bash: imagick_type_gen.pl: command not found

what's wrong?

please help me
thanks

---

### Post by zerhacke on 2007-01-21
Preface the command with a dot slash.

```
./imagick_type_gen.pl > ~/.magick/type.xml
```

---

### Post by ubunlilluz on 2007-01-21
```

lillux@lilluxoctavius:~$ sudo ./imagick_type_gen.pl > ~/.magick/type.xml
sudo: ./imagick_type_gen.pl: command not found

```

:frown: :(

---

### Post by ubunlilluz on 2007-01-22
:( :(

---

### Post by jaano on 2007-03-29
the script has to be exectuable, eg.
# chmod 770 your_script.pl

then you can execute it.

---

