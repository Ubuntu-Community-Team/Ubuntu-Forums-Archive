---
title: "su password problems"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by acheezit on 2007-10-20
hey ubuntu users...im very new to ububntu i currently am running 7.10 and i am having some problems intalling some ati video drivers...ive figured out the terminal...which is a good thing..ive tried to instal the new drivers by typing  sh ./ati-driver-installer-8.40.4.run into the terminal box...it wont run them...it cant find it...so i then research a little more...i find out i need to log in as super user...i type su into terminal it asks for a password...and i just cant type anything in the blank...i just cant type...what is the deal?

---

### Post by Celegorm on 2007-10-20
By default the root account is disabled in Ubuntu, hence, switching to root with su will not work. Instead, try putting 'sudo' in front of each command that needs to be executed as root (separated by a space from the rest of the command). This will work on any account that is an administrator, which the account you made during installation is by default. Also, note that when you type in your password in the terminal it will not echo to the screen. It's still being typed, you just won't be able to see it.

---

### Post by kerry_s on 2007-10-20
use> sudo su

---

### Post by Maestro23 on 2007-10-20
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ravisharma1987 on 2007-10-20
just type the first user password when u  r prompted to enter password.
its linux style of asking password but not echoing it in the terminal ...
u won't see any astrisk(i.e. *) in the password feild.
bye bye 
bol

---

### Post by acheezit on 2007-10-20
thanks guys!

---

