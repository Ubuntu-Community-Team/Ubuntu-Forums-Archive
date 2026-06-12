---
title: "Overnet"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by majkmil on 2005-12-07
Hi, I downloaded Overnet2000 from there site and untared it. I now have a folder with some files in it. One is edonkey2000 and it is  executable and the other is rundonkey.sh. Does anyone know what I need to do to install this program? Thanks

---

### Post by majkmil on 2005-12-07
anyone

---

### Post by Joe_CoT on 2005-12-07
there's no installer, so you'll have to do it manually.

copy the directory to /usr/local/share
```
 sudo cp -r eDonkey2000 /usr/local/share
```

now to create the shortcut

```
sudo gedit /usr/local/bin/edonkey
```

in the text editor, paste this:

```
cd /usr/local/share/eDonkey2000
sh runDonkey.sh
```
save it and close

now, make it executable
```
sudo chmod +x /usr/local/bin/edonkey
```

and now the command edonkey will run the program

---

### Post by majkmil on 2005-12-07
Thank you so much!

---

