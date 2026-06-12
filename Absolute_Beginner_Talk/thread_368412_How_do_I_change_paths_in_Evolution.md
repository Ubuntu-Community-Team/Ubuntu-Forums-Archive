---
title: "How do I change paths in Evolution?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-23
Can I configure Novell / Ximian Evolution so that it stores its data (sent and received e-mails, addresses, etc.) elsewhere?  Thanks!

---

### Post by Blofeld on 2007-02-28
OK, I've found the answer out myself and thereby transformed myself from chrysalis (noob) to butterfly (Linux wizard).  Hear me out.
Essentially, it's not necessary to reconfigure Evolution itself.  Instead, one moves the respective ./evolution directory whereever one wants and then simply creates a symbolic link there.  It's that simple.  Here's how.
1.  terminate all Evolution services and instances by commandlining "evolution --force-shutdown"
2.  move the /home/Blofeld/.evolution folder to a better place, say /data/.evolution
3.  go to where the folder once used to be by commandlining "cd /home/Blofeld"
4.  ln -s /data/.evolution
5.  Blo's your uncle.:guitar: 
6.  if you're one of those no-fun overcautious belt-and-braces types you might also want to backup the .evolution folder before shifting it

---

