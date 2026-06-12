---
title: "Deluge"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-07-19
All right, so I rebooted my system and then when I tired opening Deluge it just crashed. Here's the output when starting it through terminal. 

no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)

I tried reinstalling it and I get the same message. Any ideas?

---

### Post by felicity on 2007-07-19
Did you try deleting the ~/.config/deluge/persistent.state file?

Also 0.5.3 RC1 is available [here]("http://deluge-torrent.org/") if you're interested.

---

### Post by Armman on 2007-07-19
Thanks for the reply, can you tell me what folder I need to look in to find that file?

---

### Post by felicity on 2007-07-19
Start in your home directory, then go to the .config folder, then the deluge folder.

---

### Post by deadlikeoscar on 2007-07-19
go to /home/YourName/.config/deluge/ 

.config is a hidden folder. Open your home folder and press Ctrl + H to show your hidden files.

---

### Post by Armman on 2007-07-19
Found the file, deleted it, and now Deluge works again! Thanks!

---

### Post by deadlikeoscar on 2007-07-19
Try not to install a new version without being aware that you may have to do this again. Not a big deal and I think it is something that will quickly be worked out but something to be aware of if you ever have this problem again.

---

### Post by machavillain on 2007-07-25
Just for the record, I had the same problem, found this thread, and solved it the same way. Deluge also wasn't showing up in the Add/Remove programs dialogue, so I couldn't even try to reinstall it...

---

