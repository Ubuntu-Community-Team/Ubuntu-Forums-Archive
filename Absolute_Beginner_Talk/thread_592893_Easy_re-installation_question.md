---
title: "Easy re-installation question"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-10-26
I currently have a separate '/' for the system files, and a separate '/home'.  To fix a couple of problems with Ubuntu I think it might be easiest to re-install the '/'. 

Is that possible?  How can avoid creating another '/home' inside the '/' -- I only want the one, my current one with all my personal files.

---

### Post by Billy_McBong on 2007-10-26
[COLOR="Blue"]do you have /home on a separate partition?
if you do then you just reinstall but you tell it to format the / but not to format the /home that will leave your /home untouched 
also have it mount /home as /home

if you don't then you will have to move /home to a separate partition [/COLOR]

---

### Post by Incense on 2007-10-26
When you reinstall from the live disk, select manual partitioning, set your root part with the / and check the format box, then set your /home to, well /home and DO NOT check the format box. Once the install is done your data and settings will be in tact.

---

### Post by aberadam on 2007-10-26
Great thanks, is the 'tell it to mount /home as /home' bit fairly obvious?

---

### Post by aberadam on 2007-10-26
I'm trying to rid myself of my current X settings (particularly keyboard) and old drivers... which will only work if they're not in the /home section...

---

### Post by aberadam on 2007-10-26
Thanks incense.

---

### Post by Incense on 2007-10-26
> **aberadam said:**
> Thanks incense.

I hope it helps. I have installed many different distros over the years, and have used the same /home. It is so nice to have. 

Cheers!

---

