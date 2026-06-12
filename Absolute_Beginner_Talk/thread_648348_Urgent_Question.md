---
title: "Urgent Question"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-23
Icons are not showing up on my desktop and my menu when i click on some stuff it is not working what could be wrong please help this is urgent
Edit:Shows up with a black screen and gnome is not starting correctly

---

### Post by fedex1993 on 2007-12-23
Here is a screen shot of what i am talking about
Edit: Once i got to apperances it sets the theme correctly i dont know whats going on with it at all

---

### Post by dward526 on 2007-12-23
You might want to try reinstalling gnome desktop

```
 sudo apt-get reinstall ubuntu-desktop 
```

After this, you may be booted into your command line.  If so, do this

```
 sudo gdm
``` or ```
 sudo apt-get reinstall gdm 
```

Cheers

---

### Post by fedex1993 on 2007-12-23
yeah i dont what is going but after i boot into gdm i got to system monitor and it shows me running like 15 nautlis processes which i dont know how is possible

---

### Post by fedex1993 on 2007-12-23
> **dward526 said:**
> You might want to try reinstalling gnome desktop

```
 sudo apt-get reinstall ubuntu-desktop 
```

After this, you may be booted into your command line.  If so, do this

```
 sudo gdm
``` or ```
 sudo apt-get reinstall gdm 
```

Cheers

there is not such command as reinstall if you didnt know that

---

### Post by finferflu on 2007-12-23
It looks like a Nautilus problem to me. What happens when you open Nautils?

---

### Post by fedex1993 on 2007-12-23
nautils doesnt open the only way that i can browse fiels is thunar and termanil

---

### Post by forestpixie on 2007-12-23
> **fedex1993 said:**
> there is not such command as reinstall if you didnt know that

it's ```
sudo apt-get install --reinstall *packagename
```*

---

### Post by finferflu on 2007-12-23
Type
```
nautilus
```
in a terminal and paste the output here.

---

### Post by fedex1993 on 2007-12-23
nothing happens the output just shows another command that i can type

---

### Post by finferflu on 2007-12-23
Hmm, that's very odd, it should show at least some information...
Not sure how this can help, but you can try:

```
nautilus -c
```

---

### Post by fedex1993 on 2007-12-23
i reinstalled ubuntu let see if i have any problems

---

### Post by bapoumba on 2007-12-23
@ fedex1993: I read Hardy user in your profile, are you using Hardy?

---

### Post by fedex1993 on 2007-12-23
not on my laptop i am using gutsy i am using hardy on my desktop works fine on my desktop

---

### Post by bapoumba on 2007-12-23
Okay, is it the same with another user (you can create one for testing with **sudo adduser <login_here>**)

---

### Post by fedex1993 on 2007-12-23
i reinstalled on my laptop its seems to be working fine now. 
Thanks bapoumba and fin for helping

---

### Post by dward526 on 2007-12-23
> **fedex1993 said:**
> there is not such command as reinstall if you didnt know that

Sorry, the reinstall function works with aptitude, not apt-get as I said.

---

