---
title: "weird problem.. cant update, or install anything!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2007-03-13
this is the error i get when i run synaptic package manager

E: Dynamic MMap ran out of room
E: Error occurred while processing redland-utils (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

i have no clue how this has happened, but.. i dunno if this might help.. i was trying to get mp3's working.. n.. downloaded what seemed to be like a billion pacakges.. dunno if that made a difference.. but none the less.. things r screwed as of now.. :(

edit: just realised.. i cant seem to see my other pratitions!! all i see is filesystem!.. hmmm..

---

### Post by seshomaru samma on 2007-03-13
try this
```
sudo gedit /etc/apt/apt.conf 
```
add this line:
```

APT::Cache-Limit "20000000";
```
save  and start synaptic again

if it still doesn't work ,change the line to :
```
APT::Cache-Limit "42123456";
```
save and restart synaptic

*you should start a new thread for your other problem and supply more details.

---

### Post by nightwolf2k5 on 2007-03-13
thank u so much man!! u the best ;)

---

