---
title: "Bin file?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-10
i downloaded this game for linux
PlaneShift_CBV0.3.017.bin
and im wondering how do i install it?

---

### Post by riven0 on 2006-12-10
I installed that game a while ago, and if I'm not mistaken I think you just double-click on it. Try it anyway.

---

### Post by Circus-Killer on 2006-12-10
first make sure its executable

 $ chmod +x filename.bin

then run it:

 $ ./filename.bin

or

 $ sudo sh filename.bin

(depending on whether or not you want root priviledges while running the file.)

---

### Post by taurus on 2006-12-10
Applications -> Accessories -> Terminal
```
cd ~/desktop
chmod 755 PlaneShift_CBV0.3.017.bin
./PlaneShift_CBV0.3.017.bin
-or-
sudo ./PlaneShift_CBV0.3.017.bin
(if the above command, ./PlaneShift_CBV0.3.017.bin, returns with an error message about root or write permission...)
```

---

### Post by pay on 2006-12-10
Try ```
./PlaneShift_CBV0.3.017.bin #or if that doesn't work
sudo chown 755 PlaneShift_CBV0.3.017.bin
./PlaneShift_CBV0.3.017.bin
```or```
sh PlaneShift_CBV0.3.017.bin
```you can also add sudo infront of the commands to install the game as root.

EDIT:taurus beat me to it:P

---

### Post by jordanmthomas on 2006-12-10
Note that in Taurus's example, instead of desktop, you'll need to type Desktop (with the capital d)

---

### Post by synt4xerr0r on 2006-12-10
Thanks all i will take what i learned and use it for other bin files too

---

### Post by igknighted on 2006-12-10
Usually when you get a .bin file there is a readme or install guide on the website it came from or inside the archive the bin was in.  This will have specific install instructions.  There will be differences from time to time, so you need to read the instructions carefully.

Also, making the file executable can be done via the GUI.  Right click the file, select properties then click the permissions tab.  There is a 'make executable' check box which you then check, then click OK and you are done.

---

### Post by asnd16 on 2007-01-12
I have a BIN file that is a movie, how do I watch or extract this? Or shall i just burn it?

---

### Post by taurus on 2007-01-12
I just answered your post in the other thread!

---

