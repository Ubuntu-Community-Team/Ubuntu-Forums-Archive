---
title: "Enemy Territory Fortress installation issue"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Coinz on 2006-11-11
hi, i'm new to linux and i'm trying to install etf ( an Enemy Territory mod ) but i get this error: ( note that i've got et installed and running fine allready )

coinz@coinz:~$ sudo chmod a+x etf_1.6-english.run 
coinz@coinz:~$ sudo sh etf_1.6-english.run 
Verifying archive integrity... All good.
Uncompressing ETF: 1.6-english Installer...............................................................
./search.sh: 20: Syntax error: Bad substitution

---

### Post by funkyade on 2006-11-11
Are you running Edgy?

If so then try editing the .sh file and changing the line /bin/sh at the top to /bin/bash

Just a thought.

hth

---

### Post by Coinz on 2006-11-11
I'm running ubuntu 6.10 but what do you mean by editing .sh file ?

---

