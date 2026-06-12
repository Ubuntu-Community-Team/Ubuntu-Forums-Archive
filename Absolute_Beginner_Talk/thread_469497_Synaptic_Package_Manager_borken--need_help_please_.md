---
title: "Synaptic Package Manager borken--need help please !!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-06-09
I have been out on the road for the past few weeks (truck driver) and just got back in today. Fired up the comp (Dapper) and started to get and install needed updates. Was advised by the notification icon there was a problem "Error: BrokenCount > 0". It said to run Package Manager and see what was wrong. When I ran it it said I had 2 broken packages. Samba and Samba dpg ( I think that was the second one). I decided to wait and fix them later so I exited the Package Manager, no problems. Came back about an hour later and tried to start Package Manager and all it will do is initiate for about three seconds and disappear from the screen. Tried apt-get install samba and it says "Segmentation faulty tree...50%". Kinda lost in space here ladies and gents -- any helping hand would be greatly appreciated !! Thanks in advance.

---

### Post by Pragmatist on 2007-06-10
Try this:
```
sudo apt-get -f install
```

---

