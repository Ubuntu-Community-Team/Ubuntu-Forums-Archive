---
title: "spamassassin + evolution"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by terry_gardener on 2007-08-22
please can someone explain how to setup spamassassin with evolution mail 2.10.1 i have read a couple of howto's on this but each one says to type the location thenh - p-e for example but it doesn't let you type when clicked it opens the select file dialogue box. 

i am getting about 15-20 spam emails a day and would to stop them. 

i have spamassassin installed and spamc. 

please can someone tell me how to do this it would be brilliant. 

is there any gui based spam filters that work just as well and easy to install and use. i use to use ca anti-spam for windows xp and vista has one built in. 

thanks

---

### Post by ddrichardson on 2007-08-22
If it helps I recently wrote an addition to the user documentation for spam filtering in evolution, it isn't upstream until october but can mail you a copy if you like.

---

### Post by gary0 on 2007-08-22
Install spamassassin first, then set up evolution. I had exactly this problem, and that this worked. I get over 100 spams a day, but see only 2 or 3 of them in my inbox.

HTH
Gary.

---

### Post by ddrichardson on 2007-08-22
Its pretty straightforward in anycase - the spamassin plugin is already in Evolution, just install spamassassin from the repos and enable from plugins in evolution.

Be aware that it takes time to learn what's spam and what isn't but gets very accurate the more you use it.

Lastly configure one system, you can get noth spamassassin and bogofilter working together but it's not too straight forward.

---

### Post by terry_gardener on 2007-08-22
how does spam assassin learn what is spam and what isn't. 

is it the emails i mark a junk or is it some other way.

---

### Post by ddrichardson on 2007-08-22
By enabling the plugin and marking as junk.

---

