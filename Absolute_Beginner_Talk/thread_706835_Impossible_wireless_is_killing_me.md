---
title: "Impossible wireless is killing me"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-02-24
I've been looking and looking for guides to solving this but they either don't work or I don't understand them so I thought posting this here would be the best idea, since i could get beginner language answers :\

i have a broadcom 43xx card.. i installed the restricted driver, i can see conections, but when i try to connect it asks for the password, i enter it, it'll just say trying to enter password then a minute later the window will pop up again asking me to enter in the password..

what can i do?
at this point, i've spent about 5 hours trying to get this to work, and it seems pretty impossible..  i really don't want to go back to windows but if I can't get wifi working i don't really have much of a choice

sorry if i sound irritated or something of that nature, but it's really just such a frustrating problem..

---

### Post by coggins on 2008-02-24
Is the key WEP or WPA?  And have you chosen the right one of those in the connection box?
Failing that, try install wicd ([http://wicd.sourceforge.net]("http://wicd.sourceforge.net")).
It oftens works easily when no amount of fiddling seems to.

---

### Post by northern lights on 2008-02-24
This [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm%29%7C%2843xx%29") should solve your problem.

---

### Post by richaoj on 2008-02-24
I think the password it is prompting you for is the keyring password - it is a password separate from your login password that "unlocks" your ability to use stored passwords and stored WEP keys.  at some point you probably set one up without realizing it (maybe?).  you could try your login password - you may have incedentally set it up to be the same.  Does it say "Password to unlock default keyring" ?  

on a side note, i've had problems with the network-manager daemon as well and have also switched to wicd.  on the site you will see simple instructions for installing wicd on ubuntu.

---

### Post by richaoj on 2008-02-24
I think the password it is prompting you for is the keyring password - it is a password separate from your login password that "unlocks" your ability to use stored passwords and stored WEP keys.  at some point you probably set one up without realizing it (maybe?).  you could try your login password - you may have inadvertantly set it up to be the same.  Does it say "Password to unlock default keyring" ?  

on a side note, i've had problems with the network-manager daemon as well and have also switched to wicd.  on the site you will see simple instructions for installing wicd on ubuntu.

---

### Post by richaoj on 2008-02-24
d'oh double posts - i tried to correct a word and it seems i posted twice! d'oh

---

