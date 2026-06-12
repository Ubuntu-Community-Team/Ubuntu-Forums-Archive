---
title: "Hd usage? How come there's no space left?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-25
Well I have this doubt. Xubuntu fits into one Cd wich has 700 mega capacity. So I installed it to 4.6 giga HD. Very small, but could be worse, I guess. Now the disk read 3.8 Gig. I suppose the linux formatation stole the other 800 mega. It's acceptable so far.

After I installed xubuntu, I had more than 2 giga free in the HD. I have around 500 mega of data in my home folder (pictures, videoclips, etc..) But I only have 406 mb free in the disk. Where did the other gigabyte go??? Even if i delte all personal files, the free disk space will be under 1 giga, and in the beggining it had 2 giga. Off-couse, I downloaded opera and vlc player, but somehow I doubt they are 1 Giga in size.

Am I missing something here??

---

### Post by taurus on 2007-05-25
Try

```
sudo aptitude clean
df -h
```

---

### Post by Ganda_Melga on 2007-05-25
> **taurus said:**
> Try

```
sudo aptitude clean
df -h
```


Wow! :shock::shock::shock:

Now that's what a call a powerfull command! :confused:It freed around 400 mega in the HD. The problem is is also "cleaned" my internet connection! :shock::shock::shock: Instantly lost connection. And to restore connection wasn't easy. :-k Re-started the computer, the modem, and the router several times, and in different sequences until I finaly got my net back.

Is this common???

---

