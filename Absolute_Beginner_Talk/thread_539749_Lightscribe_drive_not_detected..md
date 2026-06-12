---
title: "Lightscribe drive not detected."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by MrBeenz on 2007-08-31
Can anyone help me out i have LaCie installed but when i click burn it says No drives have been detected. Any ideas on whats wrong.

---

### Post by MrBeenz on 2007-08-31
So no one knows whats wrong

---

### Post by siralphred on 2007-08-31
try a reinstallation.....i think there is .deb file over at getdeb.net

---

### Post by MrBeenz on 2007-08-31
already tried to reinstall and it says the same thing.

---

### Post by siralphred on 2007-08-31
sorry then, but is possible your burning software might be having some issues since lacie works with the burning software, i dont know which one you use but on their website it say Tested with K3b  so if you dont mind try using it with k3b and see if you get same error, if you do i dont know how to solve, i will look around and if i find anything i will come back and post it

also you can look here i think they have lightscribe software there, i havent used it so cannot say anything further [http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

---

### Post by eladamri on 2008-02-25
I have been running into the same problem on my 64bit computer and found a solution on the thread [http://ubuntuforums.org/showthread.php?t=623251]("http://ubuntuforums.org/showthread.php?t=623251").

When run from the terminal you will see the error:
```
4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory
```

So to fix it I copied both:
liblightscribe.so
liblightscribe.so.1

from /usr/lib to /usr/lib32

---

### Post by c0mp13371331337 on 2008-06-26
I don't know if this is still a problem, but I ran '4L-gui' from the command line and noticed that every time I hit the Refresh Drive button, it printed the following error to the command line:

```
4L-cli: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```So I updated my file list (sudo updatedb) from the command line, and searched for that file from the command line (locate libstdc++.so.5).

I happened to have Doom3 installed, which also uses that library.  I copied that file from my Doom3 directory over to /usr/lib, restarted, and I now see my drive!  Hope the helps!

```
sudo cp /usr/local/games/doom3/libstdc++.so.5 /usr/lib/libstdc++.so.5
```

---

