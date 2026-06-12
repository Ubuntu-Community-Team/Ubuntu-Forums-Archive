---
title: "Amarok clears library"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by holdie on 2008-01-27
I'm using a MyBook to store all of my music, and I'd like to be able to use Amarok to play them.  When I set my collection folders to the files in my MyBook, everything works fine, but when I restart Amarok the collection is blank and the boxes are unchecked under the configuration tab.

Any way to get around this?

thanks

---

### Post by emarkd on 2008-01-27
If by MyBook you're referring to an external hard drive, it sounds like Amarok is trying to update the collection while the drive is unplugged or powered off.  I think by default Amarok monitors your collection directories for changes.  You may want to turn that feature off.

---

### Post by holdie on 2008-01-28
I've tried switching off the "watch folders for changes" button, but it doesn't make any difference...It seems to me that the problem lies in the fact that I've got my harddrive mounting to a folder in the /media section, but the actual music files are in embedded folders within the main one (ie "Ipodmusic")...thus, when Amarok boots and the hard drive isn't connected, those folders actually do not exist on my computer...but i dunno

anyone else ran into this problem?

---

### Post by holdie on 2008-01-28
Been playing around with it and i found that simply restarting the program will erase the checked box in my collection tab (ie if I check music under /media/MyBook it shows up, if I then exit and restart Amarok it is no longer checked)...this does not happen with folders which are on my computer's hard drive...

---

### Post by holdie on 2008-01-30
any idea as to what I'm missing here?

---

