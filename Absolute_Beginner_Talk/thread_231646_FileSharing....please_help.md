---
title: "FileSharing....please help"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-08-07
hi all, 

me and my housemates share an internet connection...i.e.

Internet->Router->our machines...

now, i can get into their shared folders and steal files from them but unfortunately they cant see mine. I can see my machine on the network in 'My Network Places' in XP on their machines but then i try to access it it asks me for a password. ive tried all manner of things from my username and password to shouting at it and nothing appears to work....although the shouting did make me feel better. Is it possible for them to gain access to my shared folders, and if so how do i go about making this possible??

Thanks

DK

P.s. for some reason my machine appears as an ubuntu/samba server or something...i did install samba and something else that said something oir other about sharing with windows but i`ve had no luck!! i`m a little out of practise recently so speak slowly...:D

---

### Post by bscbrit on 2006-08-07
Have you set some of your files/folders as 'shared' yet?

---

### Post by DiscoKiller on 2006-08-07
yeah man. i figured i might have a bit of a 'mare getting windows to see into my ext3 filesystem however, although i was kinda hoping samba might help out in some way, but then seeing as how i dont really know what samba is then i cant really make that judgement.

---

### Post by bscbrit on 2006-08-08
Can anyone else make any useful suggestions?

---

### Post by Arisna on 2006-08-08
Edit the file /etc/samba/smb.conf using this command:

```
gksu gedit /etc/samba/smb.conf
```

Find the "Authentication" section.  Change the line that says "security=user" and change it to "security=share".  Save file, exit.

Using whatever tool you were using to share the file originally, setup the share as public.  This is easy to do through Nautilus.  Anyone on your network will now be able to view the share, just like with Windows.  Note that this isn't the most secure choice, but it is the most Windows-like.

EDIT:  The below linked thread has a lot of good information about setting up Samba, especially if you want more advanced security:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

