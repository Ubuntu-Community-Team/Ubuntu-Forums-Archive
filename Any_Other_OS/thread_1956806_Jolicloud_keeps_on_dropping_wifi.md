---
title: "Jolicloud keeps on dropping wifi"
date: 2012-04-11
forum: Any Other OS
---

### Post by webheadjunky on 2012-04-11
Hi there. Got the wee man an old Asus 701SD and dumped Windoze XP in favour of Jolicloud 1.2 which is a great OS...no menus to cause havoc and nice easy icon based interface

Just one problem though....it drops connection after a few minutes. I then have to right click on the sys tray icon and click on my network to let it go through the reconnection process...which it does...only to drop it again approx 5 minutes later?

Is this something anyone has come across before?

Grateful for your advice

Cheers

Raaj

---

### Post by leclerc65 on 2012-04-12
My router is located in the basement and I have similar problem with several of my computers on the second floor. I found that Puppy is most resistant to these signal fluctuations.
I recommend Puppeee 1.0 which is made specifically for the eee (I also have the 701 but it's a 4G). There are two versions, one for the Atom the other the Celeron. Try also the Puppy 5.28, which is Lucid based. On the Puppy forum there is a script named Stay-connected, have a look to see whether you can use that for your (Joli) case.

---

### Post by webheadjunky on 2012-04-14
Thanks Lecler65

Had a look but it is Puppy specific (incidentally I like how they call their utilities pets!)

Thing is, I really like Jolicloud and it is Ubuntu based so I was hoping I could get a solution here that will let me keep what I've got

Cheers

Raaj

---

### Post by webheadjunky on 2012-04-21
Hi all
just wondering if anybody had any thoughts as to how I can fix this within Jolicloud
Otherwise, will reluctantly have to wipe and start again with a different OS
I am assuming it is OS related as we had no connection issues whatsoever in Windoze XP
:confused:

---

### Post by leclerc65 on 2012-04-21
Create the script bellow, named something like stay_connected.sh, and run as a cron job, to see if that help.

#!/bin/sh 
while [ 1 ]; do 
ping -c 1 8.8.8.8 
sleep 30 
done

---

