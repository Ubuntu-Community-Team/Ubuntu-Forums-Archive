---
title: "Turning back to the darkside"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-29
The computer I am currently using isn't my own machine, and the owner wants to have Windows reinstalled in order to have a network reestablished between his office computer and this one (both are on the same router). When I installed Dapper, I converted all the important files (music, text, etc.) to ext3 .  .  .if I go ahead with reinstalling Windows, will I be able to backwards-format everything, as well as re-partition the drives as easily as GParted allowed?

---

### Post by crash0 on 2006-11-29
what do you mean, you converted the files to ext3? you can convert a partition to a certian filesystem but not a file.

---

### Post by Ocxic on 2006-11-29
I don;t know if you know this, but ubuntu can network with windows computers, simply share a folder on a windows machien, then do "sudo apt-get install samba" to get windows networking support on the linux computer, then go to places->connect to server. select windows share from the menu, type in the required info(not everything is required to be filled out). and click connect. I do this myself it's relly that easy. to share a folder in linux, rightclick and select share folder. and slect windows share from the list, then map the drive form the windows box.

---

### Post by CheshireMac on 2006-11-29
> **Ocxic said:**
> I don;t know if you know this, but ubuntu can network with windows computers, simply share a folder on a windows machien, then do "sudo apt-get install samba" to get windows networking support on the linux computer, then go to places->connect to server. select windows share from the menu, type in the required info(not everything is required to be filled out). and click connect. I do this myself it's relly that easy. to share a folder in linux, rightclick and select share folder. and slect windows share from the list, then map the drive form the windows box.

That actually sounds like it's worth trying out . . .now if only I could figure out a way to fool my father into thinking I switched back. ~LOL~ Thanks . . .I may be able to attempt this.

---

### Post by PilotJLR on 2006-11-29
You could even backup to a big enough flash drive or USB hard disk.

The files themselves are not converted, they are just sitting on an ext3 filesystem.
Backup elsewhere, and you're all set... no biggie.

---

### Post by bodhi.zazen on 2006-11-29
> **CheshireMac said:**
> That actually sounds like it's worth trying out . . .now if only I could figure out a way to fool my father into thinking I switched back. ~LOL~ Thanks . . .I may be able to attempt this.

Just install KDE (Looks like windows), download a backdrop from Microsoft, and tell him it is windows vista.....

---

### Post by That_Geek on 2006-11-29
lol, im sure he would never know

and yes samba is very easy to use, i just started using it myself, and it was really easy to set up

---

### Post by groggyboy on 2006-11-29
if you do end up reinstalling windows on your box, you can install the ext2ifs driver from [fs-driver.org]("http://www.fs-driver.org") in windows.  it lets windows read and write natively to ext2/ext3.  my shared partition is ext3.  i can even install games onto it from windows and they play fine.  but i think you should try samba first ;)!

---

### Post by Rodneyck on 2006-11-29
I can't imagine going back to Windows. Leaving Linux would be like loosing your favorite pet, I would think. 

I hope your dad finds another use for his wallet after Bill empties it. Ohhh....maybe he could fasten an optical device to it and slide it around as a mouse.  [-(

---

### Post by wpshooter on 2006-11-29
> **That_Geek said:**
> lol, im sure he would never know

and yes samba is very easy to use, i just started using it myself, and it was really easy to set up

Yes, this does work but IMO it works on a somewhat sporadic basis and is not yet to the level that you can completely depend upon it !!!

---

### Post by Josh1 on 2006-11-29
Well if someone wants to use Windows, or any other O/S, let them. They will never want to use ubuntu or anything else if you force them.
Slowly build them up then install ubuntu on their computers.... thats how I got everyone here using ubuntu 6.10! :mrgreen:

---

