---
title: "vlc"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by moheganer2 on 2006-11-08
i am currently listening to  Wfmu on vlc.I cannot turn it off.I have turned vlc on and off,tried to play a different file and deleted the downloaded file  but it just keeps playing.

---

### Post by BatteryCell on 2006-11-08
Maybe kill the sound processes.  I'm not at home right now but I think that if you are using kde run
```
killall artsd
```
and for gnome
```
killall esd
```
I'm not sure this will fix the problem but its worth a try.  Also, make sure that vlc is actually gone with 
```
ps-A | grep vlc
```
Once again Im not at home so I'm not sure that vlc is the proccess name.  If this command outputs anything run
```
killall vlc
```

---

