---
title: "Slow Cursor on ibook G4"
date: 2006-10-02
forum: Apple PPC Users
---

### Post by Jimerson on 2006-10-02
I just installed Ubuntu on my iBook G4, and so far everything seems to be working fine, except my cursor. I messed with the settings in System -> Preferences -> Mouse - but it helped very little. Is there another solution to this problem?

---

### Post by Jimerson on 2006-10-03
update: when using a USB mouse, the cursor works fine, but it is still slow with the touchpad (even after updating). That wouldn't be a missing driver issue, would it?

---

### Post by b5mC on 2006-10-03
I would have thought it was a settings issue.  Dont think I had the same problem with my usb mouse.  

With that said, it took me a little while to find a trackpad setting I was comfortable with.

As far as missing drivers...  Not really sure.  Havent been able to get all of the functionality our of my trackpad yet.

---

### Post by APU on 2006-10-03
You have to change the trackpad settings in the file /etc/X11/xorg.conf

There are many descriptions out there (including this very forum) where you can find information on how to do this. Unfortunately I don't have an example ready since i do not use Ubuntu on a Apple Laptop right now. But when I had it running on my PowerBook only two weeks ago, the trackpad worked just fine. 

I also found all necessary information about this isssue here in this forum.

---

### Post by Jimerson on 2006-10-03
Thanks a bunch! I'll start searching.

---

### Post by Leiki on 2006-10-05
Thanks for the help, APU. I am having the exact same problems. Jimerson, have you found what to do with xorg.conf file to fix this problem? If so, please let me know. :)

---

### Post by spinz8 on 2006-10-05
The threads you guys are looking for is here [http://www.ubuntuforums.org/showthread.php?t=242892&highlight=g4+slow+trackpad](http://www.ubuntuforums.org/showthread.php?t=242892&highlight=g4+slow+trackpad)
It works on my G4:D 
HTH

---

