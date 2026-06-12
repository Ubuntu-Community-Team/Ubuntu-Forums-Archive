---
title: "No ItunesDB Error Message in Amarok"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by AdamMPkins on 2007-11-08
When attempting to connect my IPod in Amarok, i get a message that reads:


> Media Device: could not find iTunesDB on device mounted at /media/ADAMMPKINS'. Should I try to initialize your iPod?

I click initialize and get these two erros:

> Media device: failed to write iPod database

> 
Media Device: Failed to initialize iPod mounted at /media/ADAMMPKINS' 

Any help? Please  bear with me, im new to ubuntu.
Thanks

---

### Post by AdamMPkins on 2007-11-08
any help?

---

### Post by AdamMPkins on 2007-11-08
I could sure use some help.

---

### Post by rfurman24 on 2007-11-08
Is that where the ipod is mounted? Has the ipod been used before as in with other linux or with windows? Does it actually have a .db on it?

---

### Post by AdamMPkins on 2007-11-08
Yes, the Db file IS on the ipod, i have used it before for about a year with windows. This was my first time using it with linux and it worked fine the first sync but i accidently disconnected it before it was done transferring and now i get the message that i previously stated.

---

### Post by mangurt on 2007-11-08
Doh!!!  There's probably an error disconnecting it without unmounting the ipod.  You might have to go back to the windows machine and correct the database on itunes.  Hopefully you still have access to itunes and the database.

---

### Post by AdamMPkins on 2007-11-08
> **mangurt said:**
> Doh!!!  There's probably an error disconnecting it without unmounting the ipod.  You might have to go back to the windows machine and correct the database on itunes.  Hopefully you still have access to itunes and the database.

Tried that, it loaded fine on windows. I mean, there's  no music to be synced in itunes, but it loaded and attached fine to itunes but it still wont connect to Amarok. It also wont connect with GTKPod or Rythmbox

---

### Post by AdamMPkins on 2007-11-08
any other suggestions?

---

### Post by AdamMPkins on 2007-11-09
any more help?

---

### Post by rfurman24 on 2007-11-11
Ya. The problem is from not umounting it. That has happened to me before but I do not remember how I fixed it. I usaully keep a backup of my ipod on my computer.

---

