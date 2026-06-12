---
title: "Help With Mplayer"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-01
Is the a way to get better sterriming videos form Mplayer it sounds all choppy and video lags and i have high speed internet and it never sis this under windows

---

### Post by slipk487 on 2006-04-01
nvm video is fine now but it still sounds choppy

---

### Post by slipk487 on 2006-04-01
video lags again wat could be causeing it to happed

---

### Post by mstlyevil on 2006-04-10
Here is the solution. You will need to alter your /etc/mplayer/mplayer.conf file. Open a terminal window and type

```
sudo gedit /etc/mplayer/mplayer.conf
```

Now add this line to the end of the file

```
srate=48000
```

Save the file and now streaming videos should play normally.

---

