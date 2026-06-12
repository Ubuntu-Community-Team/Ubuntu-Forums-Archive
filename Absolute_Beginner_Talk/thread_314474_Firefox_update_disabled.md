---
title: "Firefox update disabled"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-12-07
I installed firefox using the methods outlined in this link
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
But, my check for update button seems to still be disabled? What gives? Anyone know how to update firefox or if I should do it that way?

Thanks!

---

### Post by ButteBlues on 2006-12-07
You don't need the update button in Firefox. ;)


It is automatically updated by the apt system when updates are available.

---

### Post by cjnkns on 2006-12-07
I was under the impression that since I downloaded firefox and since the firefox directory exists in my /opt directory that it would work that way.

---

### Post by yabbadabbadont on 2006-12-07
Since you didn't install it through the apt system, you are most likely correct in that the option should be enabled...  Try looking through your about:config settings for things that mention update and make sure that they are enabled (true).

---

### Post by mcduck on 2006-12-07
since you are not using FF from ubuntu's repositories, it wont be automatically updated like rest of your system. You need to update it yourself, but normal users don't have rights to do that( you don't have write access outside your home directory). So only way to do it is to start FF as root (gksudo firefox) and then you should be able to use FF's own updater. But whatever happens don't use the root FF to browse the net, just get the update and close FF.

---

### Post by cjnkns on 2006-12-07
Ahhhhh... that makes sense thank you!

---

### Post by davidgarcin on 2007-03-09
I had the same problem after using that script (which is great, for anyone wondering).  If you start firefox with su privileges, then enable the automatic Firefox update (ie. go to Preferences -> Advanced -> Update and check the "Firefox" box under "Automatically check for updates to"), that preference change is still in effect when you run Firefox as a normal user again.

I'm not sure, but I'm hoping Firefox will now update itself even when I'm running it as a normal user.  This will save me having to remember to run it as su to update every once in a while.  Can anyone confirm that?

---

### Post by nanotube on 2007-03-09
> **davidgarcin said:**
> I had the same problem after using that script (which is great, for anyone wondering).  If you start firefox with su privileges, then enable the automatic Firefox update (ie. go to Preferences -> Advanced -> Update and check the "Firefox" box under "Automatically check for updates to"), that preference change is still in effect when you run Firefox as a normal user again.

I'm not sure, but I'm hoping Firefox will now update itself even when I'm running it as a normal user.  This will save me having to remember to run it as su to update every once in a while.  Can anyone confirm that?

sorry, no confirmation for you. :) the update will still need to overwrite some files in /opt/firefox, which are owned by root, so you will need to "gksudo firefox" to run the update. it won't work otherwise. 

your other option is to chown all of /opt/firefox to your username, but that kinda removes a layer of "protection" when you do that...

---

