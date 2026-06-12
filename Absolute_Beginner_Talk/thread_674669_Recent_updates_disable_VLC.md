---
title: "Recent updates disable VLC"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by ElliottMarlow on 2008-01-21
Recently I downloaded and installed the newest Ubuntu updates, this past Friday to be exact. Ever since I installed these updates VLC seems to be disabled and any video I try to play in Totem or Xine appears only in black and white. I know experienced users frown upon blindly downloading and installing updates without looking at them, but what's done is done. 

Any ideas? Anyone else have this problem? I removed and reinstalled VLC, but to no avail. Could it be a driver or hardware issue? Is there a way to find the list of updates I installed last week and remove them?

---

### Post by DMK62 on 2008-01-21
There was an xorg update last week that caused vlc not to launch and other programs either would not run or encountered problems. From a terminal do 

sudo apt-get update 

and

sudo apt-get upgrade

there will probably be an updated version of xorg listed , the one that caused problems last week was pulled and the new one should have been updated on most servers by now.

hth

Dale

---

### Post by DMK62 on 2008-01-22
Also make sure you restart x after you upgrade the version of xorg-server. You can do that by logging out and back in or restarting the computer.

Dale

---

### Post by ElliottMarlow on 2008-01-22
Thanks! Worked like a charm.

---

### Post by ronmarley1 on 2008-01-22
Hey, it's an avatar copy-cat...  Just kidding!  Actually, yours is nicer than mine.  I guess I have steal your face envy...  LOL!
Another way to restart X is <Ctrl><Alt><Shift><Backspace>

---

