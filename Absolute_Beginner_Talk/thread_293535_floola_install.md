---
title: "floola install"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-05
I would like to install this ipod manager called Floola and have tried many times to get the .tar.gz file installed. I can upack it to my home folder, but have trouble after that.  This is not in the repositories and I would like to try it out.  Does anyone know of a good walk-through for a newbie.

Thanks for any help provided.
P.S. I followed the how to install anything guide and still am too fresh at the terminal to pick all this up.

---

### Post by catlett on 2006-11-05
Just download the floola for linux file. Once you download it right click to bring up the option menu. Select "extraxt here". This will create a folder "Floola-linux". Open the folder and double click the floola executable. It is the only file that is labeled floola or if you have the standard icons it is the file that is shaped like a blue square. That will launch floola,
If you want a "shortcut" on your desktop, you will need to create a 'launcher'. Right click on the desktop and select "create launcher". Just browse to the folder you just created and select the floola file. You can put any comment you want. Click on the 'no icon' box to select an icon for your launcher.

P.S. I just read the read me. You need to copy the 2 files in the folder that are labeled libfmodex to /usr/lib
If you know the terminal, just cp the 2 files to /usr/lib. If not you can drag and drop them with nautilus. Go to Places>Home folder and browse to the Floola-linux folder. Then go to the terminal and enter ```
gksudo nautilus
``` This launches nautilus as root so you will not have a permissions error. Browse the gksudo nautilus to /usr/lib. Drag and drop the 2 files from the Floola-linux folder in the regular nautilus to the /usr/lib folder in the gksudo nautilus.

---

### Post by gentlemanmasher on 2006-11-05
thanks a million.  I appreciate your help.

---

### Post by philidox on 2007-11-15
I'll try install it the way you laid out if it does not work, I'll post back

---

### Post by blubyu1914 on 2008-03-12
I'm having the same issue with getting Floola to work on my system. I'm running Gutsy 7.10 x64 version. According to Floola's website, the instructions are as follows: [ You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1). If you don't know how to do this simply copy as root files contained in this package to /usr/lib32 (Thanks Adam Thayer)]

I have tried this several times copying these files to lib, lib/32, and lib/64. Still no luck in getting this to work.. Anybody out there have any luck in getting Floola to work.. I've used this many times on a Windows system and like how it operates a lot.. I would love to use this on my Linix system now...

---

### Post by Doc Holyday on 2008-05-04
I had the same problem on Ubuntu Hardy. A simple:
sudo apt-get install libstdc++5
fixed it. Floola seems to rely on libstdc++ 5, where Hardy [... and maybe older Ubuntus?!?] on default prefers to install libstdc++6 instead.

---

### Post by big_iain on 2008-05-26
Many thanks Doc, I spent ages finding software to make my iPod work with Ubuntu ( Gutsy ) only to loose it when i upgraded to Hardy Heron.After many attempts to re-install it i found your posting and installed libstdc++5 and hey presto!! worked first time:guitar:

---

### Post by DarinB on 2008-05-26
out of curiosity what ipod are you using???
i have a gen 3 40 Gb would love a new classic or nano but not sure if i can got it running on ubuntu

---

### Post by jbaerbock on 2008-05-26
What I did is added the floola.exe (windows version of floola) to my Ipod HD and just run it using Wine. Works perfectly if not better than natively in windows. Then when you happen to be on windows machines there is no problem using it there either :D.

---

### Post by DarinB on 2008-05-26
yeah! thats right out of the man pages for floola i want to know if it works with the new ipods ie classic and the new gen nano????

---

### Post by jbaerbock on 2008-05-26
Well it works with my IPod 5th Generation (So rather new). I would think it should work. I know rythmbox in ubuntu 8.04 is supposed to work with nano and whatknot else. Music management is easy, podcasts are more problematic on rythmbox. Good luck.

---

