---
title: "DAEMON Tools install?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-27
is there a way to  install DAEMON Tools  in ubuntu?

---

### Post by hopstah on 2006-08-27
why exactly do you need daemon tools in linux?

---

### Post by Fedcer on 2006-08-27
You don't need Daemon Tools nor any other program to mount cd images in linux.
First create a fodler where you want to mount the file (for example I use /media/iso), then just use this command:

```
sudo mount -o loop -t iso9660 filename.iso /media/iso
```

(changing the "/media/iso" to whathever your folder is)

---

### Post by diablofatt on 2007-06-19
What would the custom command be for opening this as a video? If i right click my ISO (wish is a video) and I go to properties and select "open with" and then go to "add" and add a custom command what could that be?:popcorn:

---

### Post by scapalexis888 on 2007-07-29
If your iso is a DVD movie, then you can just use VLC media play, click file>open disc and select your iso

---

