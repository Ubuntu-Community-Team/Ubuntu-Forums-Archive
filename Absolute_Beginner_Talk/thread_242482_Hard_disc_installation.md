---
title: "Hard disc installation"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by mozgreen on 2006-08-23
This may sound daft to an experienced user - which I am not.
I recently fitted an 80gb Maxtor hard disc for use as a backup depot for music and video.  This was formatted ex3 using Qtparted, chown'd to myself and the Discs Manager used to enable a path to a folder on the desktop and then 'Enable.'
After reboot the access path disappears, ownership back to root and status is 'Inaccessable.':confused: 
What am I doing wrong and how can I mount this thing so that it is easily accessable?
Any help or advice gratefully recieved!

Moz

---

### Post by Turgon on 2006-08-23
Hm, thats a little strange.

You could problaby make a path in fstab:

sudo gedit /etc/fstab

For changing ownership, you can actualy do it in a gui:

sudo gksu nautilus

Then change waht you need and close the window.

---

### Post by mozgreen on 2006-08-24
Thanks Turgon! :D  

Editing the fstab and/or changing owner via "sudo gksu nautilus" worked and I now have a depot hd the whole family can access (God help me).
Thanks again! :mrgreen: 

Moz

---

