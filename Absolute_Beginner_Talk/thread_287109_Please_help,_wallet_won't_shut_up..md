---
title: "Please help, wallet won't shut up."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-28
Ok so heres my problem, I just switch to Gnome from KDE in the terminal with "sudo aptitude install ubuntu-desktop" and its working fine and all, I've somehow managed to get a mix desktop between KDE and Gnome, I don't know how but I'm fine with it. Whenever I start up Kopete, I get this stupid KDE Wallet crap that I don't want, I want it to shut up, I've tried "sudo apt-get remove kde wallet" and "sudo apt-get remove kde daemon" and many other stuff like it but it keep stelling me that the package is not found. What do I do?

---

### Post by David_T on 2006-10-28
From doing an apt-cache search, it looks like it's called kwalletmanager.

---

### Post by Narcoleptic_Insomniac on 2006-10-28
Ok I'll try apt-get removing that then, I'll report back wether it works or not.

---

### Post by Narcoleptic_Insomniac on 2006-10-28
Well It removed kwalletmanager, but when I open kopete I still get the stupid message "The application 'Kopete' has requested to open the wallet 'kdewallet' please enter the password below." So I tried sudo apt-get remove kdewallet, but it says no package was found with that name. So what do I do now?

---

### Post by Swampfox on 2006-10-28
Go to the KDE control center 
(right click on dekstop and choose run and type in **kcontrol** )

then choose Security & Privacy. You'll find Kwallet there.
Just uncheck the box.

---

### Post by Narcoleptic_Insomniac on 2006-10-28
I'm on Edgy Eft you see and there is no Control center, if there is I don't know where to find it. So what now?

---

### Post by Narcoleptic_Insomniac on 2006-10-28
Actually NM I missed part of what you said and did it wrong, I'll try it the right way, sorry.

---

### Post by Narcoleptic_Insomniac on 2006-10-28
Ok I'm in Controler Center, and I went to Security and Privacy but I don't see kwallet. I went to all the things and in every tab in all the things and no kwallet anywhere. Please help.

---

### Post by Swampfox on 2006-10-28
> **Narcoleptic_Insomniac said:**
> Ok I'm in Controler Center, and I went to Security and Privacy but I don't see kwallet. I went to all the things and in every tab in all the things and no kwallet anywhere. Please help.

Hmm..Try going into KDE and reinstall kwalletmanager and then do the instructions.

Go to the KDE control center
(right click on dekstop and choose run and type in kcontrol )

then choose Security & Privacy. You'll find Kwallet there.
Just uncheck the box.

---

