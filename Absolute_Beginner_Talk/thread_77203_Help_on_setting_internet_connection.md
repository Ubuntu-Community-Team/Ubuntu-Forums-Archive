---
title: "Help on setting internet connection"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2005-10-16
I've just installed Linux and I'm working with a dual boot.  Of course, I'm posting this msg through my Window XP OS.  My internet is set-up with my Etheret card connected to router then to DSL modem.  This is a wire network.  I was on the internet lastnight and got my Ubuntu updated.  Today I jumped on the computer and dont have any connection now.  It was working after the update but only once I turned my computer on this problem arose.  I know when I go to Network Tools I see numbers jumping around at the Inter...(something) statistic.  Once I open up Foxfire no connection.  Any advice?
Thanks

---

### Post by Knome_fan on 2005-10-16
I'm just guessing here, but maybe you do have a problem with nameresolution. What did you set as your DNS?

P.S.:

If you open a terminal, can you ping something?
Could you try:
ping 62.111.62.111

and 

ping [www.google.org](www.google.org)

---

### Post by Leigh on 2005-10-16
Are you getting an IP address from your router?  Type **ifconfig | grep "inet "** in a terminal window to see what you get.
(Note, there is a SPACE between the last quotation mark and the letter "t" in **inet**)

---

### Post by Vanish00 on 2005-10-16
I got a msg to open terminal and type sudo ppoeconf.  Since I did that my internet seems to be working for now.  Thxs for info, i'll keep those cmds in mind

---

