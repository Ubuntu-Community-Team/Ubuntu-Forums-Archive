---
title: "Suddenly can't write music to my phone"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by fionnseach on 2007-05-20
I've just bought a new memory card for my Sony Ericsson k750i.  For the first few days everything was fine and my world was again filled with joy as I happily transferred music, video and pictures to and fro with no problems.

Last night when I'd finished transferring some more music to the phone, it froze and had to be re-started.  I un-mounted the phone as usual, but the tracks didn't show up.  Trying to re-transfer them, the phone now tells me I don't have the permissions to write to the audio folder.  I'm pretty stuck on what to do now...

---

### Post by x64Jimbo on 2007-05-20
sudo chmod -R 777 /media/phonedir/

---

### Post by fionnseach on 2007-05-20
Thanks for that.  I'm not getting anything though.  It's saying "No such file or directory".  I've tried both sudo chmod -R 777 /media/phonedir/ and sudo chmod -R 777 /media/sdb1/

---

### Post by seshomaru samma on 2007-05-20
can you browse the card?
sometimes ubuntu creates a .trash file (hidden) and all the deleted files get stuck there and jam the card.
press ctrl+H to see if there are any hidden files
try it on another box to see if its not a hardware issue

---

### Post by fionnseach on 2007-05-21
Thanks, I'm not finding anything in the trash (although it does seem to have some tracks on it that don't show up on the phone).  Unfortunately, I can't try it on another box.

---

### Post by x64Jimbo on 2007-05-22
the phonedir part was to show you that you needed to put the directory of where the card is. It wasn't literal. It should be the address in the address bar when you are browsing the card.

---

