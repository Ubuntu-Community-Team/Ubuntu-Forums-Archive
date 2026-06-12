---
title: "Can a Script Kiddie Steal My Files?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Troubled on 2007-08-15
I've asked something similar in the servers and security forums but I didn't receive a very specific answer. I've gone to a particular coder's website and telnet port 23'd his server, as well as chatted with him via IRC. What is the chance (if there is a chance) that he could have gained access to my system and files?

Please reply! Thanks!

---

### Post by eentonig on 2007-08-15
depends on what you talked about. If he found enough information from you to social engineer his way in to your system or not.

---

### Post by Troubled on 2007-08-15
I did not talk to him about anything relevant.
Is it possible that he has installed software on my ubuntu box through HTML, telnet port 23, or IRC? Assume that I've already succesfully done sudo-as-admin.

---

### Post by Frak on 2007-08-15
Not really, Linux does not support remote code execution without PHP or something of the sorts active. So you really don't need to be worried much.

---

### Post by milosz.galazka on 2007-08-15
You can see open ports and active connections using command **netstat -ta**

---

