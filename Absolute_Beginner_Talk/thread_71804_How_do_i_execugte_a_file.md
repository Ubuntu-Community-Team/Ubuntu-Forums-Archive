---
title: "How do i execugte a file"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-04
I want to execute a .bin file for realplayer 10 but when i type the name exactly in term or click on it in gnome nothing happens

---

### Post by invalid on 2005-10-04
You typically execute a file by typing:
./filename
or in certain places
sh filename

If it will not execute with this, you probably need to 
chmod +x filename
as to give it execute permission

Try this,
Cheers
Cb

---

### Post by dgrafix on 2005-10-04
ive tried all those but i keep getting:

./Real.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

it definitely is the right filename because if i deliberately get it wrong i get the usual:

bash: ./Real.binm: No such file or directory

---

### Post by cayamara on 2005-10-04
[QUOTE=dgrafix]ive tried all those but i keep getting:
./Real.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
it definitely is the right filename because if i deliberately get it wrong i get the usual:
bash: ./Real.binm: No such file or directory[/QUOTE]
It looks like you are missing a library to execute the program.
```
sudo apt-get install libstdc++5
```
should do the trick. That package provides libstdc++.so.5.
Have fun! :D

---

