---
title: "PrintScreen in JPG?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Lolicon on 2007-07-06
I would like to save my printscreens in an averagely lossy filesize instead of the normal PNG that the PrintScreen does. How can I do that?

---

### Post by p_quarles on 2007-07-06
Open the .png in GIMP, and then save it as a jpeg.

---

### Post by Lolicon on 2007-07-06
I know how to do that, but can it do it automaticly?

---

### Post by moredhel on 2007-07-06
seems not, what is wrong with pngs?

---

### Post by Lolicon on 2007-07-06
Lossless pictures are huge. My internet doesn't like to upload a 2MB file when it can upload a 100kb jpg file.

---

### Post by 3rdalbum on 2007-07-06
```
sudo apt-get install imagemagick
```

Installs the commands you need for command-line screenshotting and image conversion.

```
import -window root screenshot.jpg
```

Captures the whole screen and saves it as "screenshot.jpg" in your home directory. If you want, you can put that command as a launcher on your panel or in your menu.

---

### Post by Lolicon on 2007-07-06
Thank you. Is there a way to wrap the command to the printscreen key?

---

### Post by moredhel on 2007-07-07
.png?! lossless?! .png are tiny, hench their use as website images. I dunno about size compared to jpegs, but i'm sure there is little different. Now .bmp is the one you want to avoid.

---

### Post by xc3RnbFO8P on 2007-07-07
Install "ksnapshot" and save it as jpeg. That is the easy way.

---

