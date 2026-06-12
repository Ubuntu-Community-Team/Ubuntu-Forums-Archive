---
title: "Wireless Problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Clewless on 2007-04-09
Okay. I have downloaded & using Live CD, the newest BETA (Feisty) to try and use my wireless card. (Edimax EW-7128g) Based on a RaLink chipset.

Now, out of the box, I can view all of the nearby routers using the utility at the top of the desktop screen. But it will not connect with the routers. Any ideas?

:popcorn:

---

### Post by theboomboomcars on 2007-04-09
What does iwconfig show?

I had this same problem, and it was because it would truncate the last letter off the essid.  So if it showed essid, it would try to connect to essi.  I just had to add a letter to the end and it worked.

---

### Post by mand0 on 2007-04-09
> **theboomboomcars said:**
> I had this same problem, and it was because it would truncate the last letter off the essid.  So if it showed essid, it would try to connect to essi.  I just had to add a letter to the end and it worked.

I am also having a similar problem.  Did you add the essid via the Terminal or did you use the Networking GUI ?

---

### Post by RKCole on 2007-04-09
Hello.

I'm not sure if this will be of much help as far as a Live CD is concerned, but [this]("http://ubuntuforums.org/showpost.php?p=2325524&postcount=20") is how I was able to get my USB wireless device (using a RaLink RT73 chipset) working with both Edgy and Feisty.  I'm still trying to figure out how to get WPA2-PSK+AES working, though.  Once I do, I'm going to redo the guide I wrote.

Hope this helps some...

Take care.

---

