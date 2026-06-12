---
title: "Does printer sharing work in Samba in Feisty?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Blond_Knight on 2007-04-25
I share a printer through Samba in Edgy, no editing necessary just:
```
sudo lpadmin -p LJ2100 -E -v parallel:/dev/lp0 -P LJ2100.ppd
sudo lpadmin -d LJ2100
```

Restart Samba and the printer appears as a shared resource on the server.
In Feisty it doesnt seem to work.  I worked on it for four hours and couldnt get the printer to share.
I tried editing the Cupsys.conf file to allow the network to 'see' it, tried uncommenting things in the smb.conf file.  Finally I had to wipe it and reinstall Edgy.
Anyone have a clue why samba wouldnt share the printer?

---

### Post by bloodniece on 2007-04-25
I usually just edit smb.conf

Find the following lines
 ...
 # printing = cups
 # printcap name = cups
 ...
and uncomment them.
 printing = cups
 printcap name = cups

---

### Post by Blond_Knight on 2007-04-25
Thats interesting, those lines are commented out in my Edgy server...which has samba sharing the printer!
Thanks for the suggestion I'll test it tomorrow.

---

### Post by Blond_Knight on 2007-04-26
I install Fiesty on another box tonight, ran through the same setup, and the darn printer showed up as a shared resource.  I didnt have to make the edit you suggested. I have no clue why it didnt work yesterday and works today.  But I appreciate the suggestion and will add it to the knowledgebase for the next time :)

---

### Post by st33med on 2007-04-26
You don''t have to do that with Samba. You can just go to System->Administration->Printing and click New Printer and enter the info there.

---

### Post by fable on 2007-04-30
I do have this same printer sharing problem.  My printer used to work with Dapper (6.06).  Yesterday I installed Fiesty (7/04) and the printer stop sharing.  However, Samba seems to work fine for folder sharing over the network.

I am new to Linux.  Where is smb.conf located?  I looked at the Samba folder in /var but there is no smb.conf file.

Any advice to fix this printer sharing problem is appreciated.

---

### Post by fable on 2007-04-30
I found the smb.conf file in /etc/samba.
I uncommented the two lines:
```
  printing = cups 
  printcap name = cups
```
Now my XP machines can see the HP printer on the Ubuntu machine.

---

### Post by nir78 on 2007-05-01
> **fable said:**
> I found the smb.conf file in /etc/samba.
I uncommented the two lines:
  printing = cups 
  printcap name = cups
Now my XP machines can see the HP printer on the Ubuntu machine.

Same here...
Worked only after uncomment the lines.
There was no problem in 6.10 but in 7.04 even with webmin I had to uncomment :confused:

---

### Post by theemrsweets on 2007-05-14
> **bloodniece said:**
> I usually just edit smb.conf

Find the following lines
 ...
 # printing = cups
 # printcap name = cups
 ...
and uncomment them.
 printing = cups
 printcap name = cups

I had the same problem and did this.  Now it works! Thanks

---

