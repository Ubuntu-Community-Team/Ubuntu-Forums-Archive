---
title: "Synaptic Pkg manager says there's a problem"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-14
It says something is broke...I think it meant RealAudio. But it won't let me fix the broken stuff.  Should I find a way to solve this problem or just let it be? My Real Player works fine.

---

### Post by aysiu on 2006-04-14
Try going to Applications > Accessories > Terminal and typing ```
sudo apt-get -f install
```

---

### Post by esteban2x on 2006-04-14
Here is the mesage I get:

building dependency tree....done
correcting dependencies.....done
The following packages will be REMOVED:
RealPlayer
Need to get OB of archives
After unpacking 15.4 mb disk space will be freed.
Do you want to continue  (Y/N)?

I chose no because I don't want to remove RealPlayer.
What gives with this stuff?

---

