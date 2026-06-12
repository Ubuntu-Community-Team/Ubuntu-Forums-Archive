---
title: "NVIDIA drivers in breezy"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2005-11-16
Ok so I got my wireless to work...actually I just went to a place where I could use it and found myself very pleased that it worked out of the box!

Anyway, I was wondering what NVIDIA drivers I should download for breezy...

I went to [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

to get drivers and don't know which one to download for a NVIDIA 6600 GO...

I'm so new to all of this, haha

thanks for the help!

---

### Post by Kyral on 2005-11-16
There is an NVidia driver package for Ubuntu already, though they aren't the bleeding edge drivers (Version 7667 vs. Version 7676). But it shouldn't matter.

Anyway this is how to do it.

```
sudo apt-get install nvidia-glx
```
```
sudo nvidia-glx-config enable
```

Then restart X with CTRL+ALT+Backspace. You know it works when the NVidia Logo appears

---

### Post by inovermyheadd on 2005-11-16
well that was easy...much appreciated Kyral

---

