---
title: "Updating Ubuntu query"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-01-15
Hi

Just wondered if there was a simple explanation when sometimes checking for updates via the 'Update Manager' a warning window appears after checking online to say there were various duplicate entries in /var... lists if I remember correctly? To get by this I run 'Sudo Aptitude Update' in term window and then the update manager works ok without any duplicate entries?

TIA

:-k

---

### Post by scrooge_74 on 2007-01-15
I have seen people have trouble like that, but I prefer to do the updates the old fashion way

sudo apt-get update
sudo apt-get upgrade

I think is more fun,plus I can update remotely this way

---

### Post by golem3 on 2007-01-15
Did you edit the update lists and duplicate one by mistake? I think that might do it. You won't have to deal with the GUI if you go 

$ sudo apt-get update && sudo apt-get upgrade

Hope that helps.

---

### Post by geezerone on 2007-01-15
Thanks for the prompt replies people! :) 

I presume the upgrade will add or update entries in the /var/lib/apt/lists/ folder and remove duplicate ones?

I have created a couple of script shortcuts for carrying out this task in future but probably will be lazy and just go to 'update software' thus carrying out apt-get update. :KS  or am I wrong in thinking that is what the update software GUI does?

Thanks again! :)

---

