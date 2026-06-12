---
title: "*VERY Newbie* Running a couple of windows progs"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by kwyjibo on 2006-04-14
Hello all!  Got ubuntu installed on my machine after playing about til 5am last night sorting out big enough partitions for it. took forever!  It's a move i'm wanting to make as well as being forced to (work reason).  So I warn you well in advance I'm a complete newbie at this, and some of what i say may be dull.

so setting it up, bit of a headache innit? I got it installed, but took ages to get it to mount ntfs partitions, play mp3s, divx, xvid and all that stuff, and i don't even wanna go in to how long it took me to get my lexmark printer configured.

I've just installed Wine too (again another long process), it's got IE working and WMP, and the likes but really I only want it to work for a couple of little programs, in particular something called Voipstunt, it allows me to make free calls to the UK and I use it lots.  With wine i have managed to get passed the DLL errors but now just a checksum error, and it prompting me to reinstall, which I have no idea how to do.  So my question is, is Wine the best program to do this for me (i cant see how i can do a fresh install of it from the setup.exe) or is this better alternative? or shall i pester voipstunt to make a linux install?  :p




oh i got another newbie question actually, what sort of structure is good, currently got a /home partition of 50gb, / partition of 20 (both logical), and then 2 x 1gb primary partitions for boot and swap. I thought /home woulda been just for private data but the more i do the messier it seems to become. maybe i need to start saving my downloaded installs to / somewhere and then unpacking them there. is that the 'best practice', or what is?

---

### Post by Monster_user on 2006-04-14
[QUOTE=kwyjibo]I thought /home woulda been just for private data but the more i do the messier it seems to become.[/QUOTE]
The '/home' partition is for your private date. Private also including your desktop configuration settings, and music playlists, etc..

Saving them to '/' is going to be more trouble than it is worth. Dealing with permissions, and all. Besides, you have a large home partition. Just save it to a sub-folder. Such as "Downloads/Installers".

Voipstunt...

Linux has VOIP software. You may be able to use your account in Ekiga, Kphone, or another VOIP client for Linux.

---

### Post by ykyang on 2006-08-23
hi,Monster_user
could you give some ideas for set up an account for Voipstunt in Ekiga? I find that there is only for setting up an ekiga account in *Tools >> PC-to-Phone Account*. Thank you.

---

