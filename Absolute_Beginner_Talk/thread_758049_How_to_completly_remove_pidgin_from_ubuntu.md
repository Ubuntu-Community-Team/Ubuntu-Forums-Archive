---
title: "How to completly remove pidgin from ubuntu"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-17
Hey im new to ubuntu ... and i wanted to remove pidgin because iv got another program for my msn and shyt

and im really really newbie and i hate it cuz i can solve anyproblem in windows ... but im a sitting duck when it comes to ubuntu 

can someone tell me how to remove it .. 
when i go into the synaptic pack mngr  and serach pidgin .. i see 2 things 

pidgin 
pidgin-data

can i completely remove them  ? // or just one 

 also i have absolutly no use for some program like " evolution mail " "sound juicer cd extractor " and a couple of other thingss 

but when i go to remove/add programs and try to remove it .. it says i cant and i needa remove the WHOLE package ... but i donno how ... 


im soo soory that im soo newbie ... but im REALLY new to ubuntu .. and i know youv been throgh this when you first installed ubuntu ... please bare with me >.<

---

### Post by northern lights on 2008-04-17
From a terminal, run ```
sudo apt-get remove pidgin
```

---

### Post by moehabibi on 2008-04-17
yess thank you .. its gone now =] 

but what about the other things ... 
it tells me i need to remove the whole package ... 
but which packagE?

---

### Post by northern lights on 2008-04-17
apt-get told you to remove "the whole package"?! Or what did?

---

### Post by Oldsoldier2003 on 2008-04-17
```
sudo aptitude purge pidgin pidgin-data libpurple0
cd ~
rm -r .purple

```
will remove pidgin, all its packages and will also remove the settings.
Aptitude will tell you its removing ubuntu-desktop, but don't worry... its a meta package and wont actually unistall your desktop.

---

### Post by jbruwer on 2008-04-17
Just for interest sake why would you want to remove the wonder that is pidgin

---

### Post by Triggerhapp on 2008-04-17
> **jbruwer said:**
> Just for interest sake why would you want to remove the wonder that is pidgin

If you only use the EvilNetwork, aMsn is better ;)

---

### Post by Oldsoldier2003 on 2008-04-17
> **Triggerhapp said:**
> If you only use the EvilNetwork, aMsn is better ;)

True, but Pidgin is the best integrated messenger in my opinion. It beats trillian hands down. Well if I were a KDE fan I'd use Kopete, but thats a different story ;)

---

### Post by stchman on 2008-04-17
> **moehabibi said:**
> yess thank you .. its gone now =] 

but what about the other things ... 
it tells me i need to remove the whole package ... 
but which packagE?

Yes the program is gone but Pidgin's dependencies are still there.  You need to use autoremove instead of remove.

```
sudo apt-get autoremove pidgin
```

The autoremove command removes all unused dependencies.

---

