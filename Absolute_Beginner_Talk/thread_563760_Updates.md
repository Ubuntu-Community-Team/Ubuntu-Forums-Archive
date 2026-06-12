---
title: "Updates"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Lewis Lewis on 2007-09-30
Hi. I'm using FeistyFawn and the update manager keeps telling I have 4 updates available but when I proceed to update I get a warning saying these are unauthenticated updates and could allow a malicious person to take control of my system.  By their names and the description of them, they seem like they're valid and could be important but the warning worries me a little bit. Are they safe to download or could problems result if I download them?  
The 4 updates in question are,,,,, libssl0.9.8,,, openssl,,, update-manager,,, update-manager-core. I did a check to see if anyone posted this question and apologize if they did and this is a repeat question.

---

### Post by Nythain on 2007-09-30
that  usually  means you have an unvalidated repo... most repos have directions for adding the gpg key

---

### Post by Lewis Lewis on 2007-09-30
Rephrasing the question, I looked at the details listed with the updates and am still unsure if I should just ignore them or if they're important enough that I should  download them. My knowledge is truly limited. If anyone else has an answer and the time to explain so that new users to Ubuntu can decide what to do, please  reply. Are all the updates that the update manager offers safe to download? Should we accept and download them and be the guinea pigs? If not,  is there a way to remove those updates that aren't advisable to download from the update manager so they don't keep reappearing every time I boot up?  I already downloaded a couple unauthenticated updates because I thought that every update that the update manager offered was safe to download. If I was in error could someone please tell me.

---

### Post by rsambuca on 2007-09-30
If you post your sources.list for us, we will be able to tell you.  You can open a terminal and post the output of 

cat /etc/apt/sources.list

---

