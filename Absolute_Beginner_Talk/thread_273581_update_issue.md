---
title: "update issue"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-10-08
Had some synaptic and update probs a week or so ago but its all been fine
until i installed the kubunto desktop onto it......not sure if thats been the cause somewhere but i get the below errors when trying to update.
Synaptic still seems to work though this time

[ATTACH]17111[/ATTACH]

Any clue as to what to do anyone?:-k 
tia

---

### Post by Dinerty on 2006-10-08
Not 100% sure, but you tried using a default sources.list?.

---

### Post by Frak on 2006-10-08
I think you had on an off-chance day something was wrong with the servers.

---

### Post by Frak on 2006-10-08
And if it was more than a day,
I'm clueless.

---

### Post by xpod on 2006-10-08
Never even considered it mate:rolleyes: 
There really aint much more im going to use automatix for anyway.
Watch this space....

---

### Post by Kateikyoushi on 2006-10-08
Try

```
sudo apt-get update
```

Maybe the sources.list went wrong try to use the backup of it or redownload a new.

---

### Post by pistcivet on 2006-10-08
```
cat /etc/apt/sources.list
```Please post the output.

---

