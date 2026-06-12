---
title: "Everything fine, except no internet connection"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by gummyfungus on 2008-02-28
Hi guys, I'm totally new to Linux. The installation on my P3 1GHz machine was a breeze and everything worked fine, except I can't connect to the internet using Firefox. Using a wired connection, and my other 2 Mac machines connected fine via wireless. Tested using the same wired connection too on  my mac and it worked fine. The weird thing is when I ping some addresses in the Terminal and there's a response. Any suggestions? Thanks in advance!

---

### Post by laidback on 2008-02-28
In Network>settings>properties look to see if you have Roaming Enabled (check box), I found I needed it unchecked. Just a thought.

---

### Post by gummyfungus on 2008-02-28
> **laidback said:**
> In Network>settings>properties look to see if you have Roaming Enabled (check box), I found I needed it unchecked. Just a thought.

Tried it, no luck either. Ping doesn't work with Roaming Enabled unchecked. :(

---

### Post by gummyfungus on 2008-02-29
Whoopee! Problem solved. Apparently all I have to do is disabled IPV6 via terminal as described in the help file. :)

---

