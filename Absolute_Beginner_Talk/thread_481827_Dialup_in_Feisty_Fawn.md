---
title: "Dialup in Feisty Fawn"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by catfish88 on 2007-06-22
Hi, I have made a dialup connection in Feisty Fawn by going to System, Administration, Network, and then putting in all the information like username and phone number. So now how do I actually connect using that connection? Or is there more I have to do?

---

### Post by niteshifter on 2007-06-22
Get "wvdial" from the repository. To answer your question, yes there's more to do: editing ppp and chat scripts. Which is why I recommend wvdial - just one configuration file to set up, it will deal with the ppp and chat programs for you.

---

