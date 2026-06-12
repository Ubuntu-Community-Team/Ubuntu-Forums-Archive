---
title: "cupsd update problem"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by capozziatc on 2008-02-28
the other day i posted an issue i was having, and after allot of searching through forums and googleing i ended up solving the problem myself.  
[http://ubuntuforums.org/showthread.php?t=709901]("http://ubuntuforums.org/showthread.php?t=709901")

hopfully i can get this issue solved.

ok so after a clean install of Ubuntu gutsy i enable the "restricted drivers/ firmware" then restart.  everything is fine.  then i tell Ubuntu to download and install updates.  it downloads them all and starts to install them.  but it gets about 98% complete with the entire process and then just dies on me.  the system locks up i can still grap the window and move it around.  but i cant open programs and i cant hit "*ctrl + alt + f1*" to end the process.  i cant even tell it to restart.  this has happened twice, and last time i held the power button for 8 secs to shut it off (i know ur not supposed to do that with Linux but i couldn't think of anything else to try).  upon restart, ill be able to log in, which i do.  but then it just halts at its default pink screen.

this is all i can tell you it says "reloading apparmor progiles: done starting common unix printing system: cupsd"

i can easly reformat but i cant narrow down the update that kills the system because there are tons of updates that say "cupsd".

---

### Post by mikeyphi on 2008-03-01
A suggestion
If you go through the full OS install again - use a terminal to install updates, that way, if the error reoccurs, you will see what is happening. Use the following commands:

sudo aptitude update

and when updated

sudo aptitude safe-upgrade

---

