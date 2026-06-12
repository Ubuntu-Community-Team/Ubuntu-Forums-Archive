---
title: "Linux Newbie : Ubuntu Gutsy, Wine and Dreamweaver"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by desk2web on 2007-11-14
Hi there,

OK, I've got Ubuntu Gusty installed on my PC now, and I have to admit I love it!  I've managed to get VirtualBox sorted out, but for one small problem when trying to save files in Dreamweaver onto a network drive - so, I installed Wine and have installed Dreamweaver 8 successfully - now my question I guess is not actually related to either Dreamweaver or Wine, but more generally "newbie" based!

So, the question is this, how can I mount (if thats the correct term!) a network drive (I have a network storage device with its own IP etc) so that I can access it successfully through Dreamweaver in Wine? I am assuming I need to edit some file or other, but what and how I have no idea, which is frustrating me at the moment.

I'm keen to get away completely from Windows, but Dreamweaver in particular is essential to me, although I have tonight installed Nvu and Quantas Plus to see how they compare - but the bottom line is that all my development sites are stored on a 500gb NAS drive and I need to be able to access them and save to them successfully whatever application I am in, be it under Wine or not.

Any advice would be very greatly appreciated.

Allan

---

### Post by desk2web on 2007-11-14
Got it sussed out :)

mkdir /mnt/mountname

then edit fstab (I used pico /etc/fstab)

//FND/sharename /mnt/mountname smb defaults 0 0

Worked perfectly - its a steep learning curve and I'm only now beginning to appreciate the very basics, but Windows for me could be a thing of the past!

---

