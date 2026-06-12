---
title: "How to uncript the passwords encrypted in /etc/shadow ?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-27
I lost one of my password in my linux box.
  
Maybe sthg like,  John the ripper ??

thank you very much !!
  
Pat'

---

### Post by ssam on 2005-11-27
do you still have the password of a user who can sudo? if so you could
```
sudo su lockedoutuser
```
to log in as this user, and then change the password with
```
passwd
```

getting passwords out of /etc/shadow is difficult, as it just stores the one way hash results. [http://en.wikipedia.org/wiki/Hash_function](http://en.wikipedia.org/wiki/Hash_function) . to break it you have to try input strings until the hash matches the stored hash (however this input string may not be the same as the original password)

---

### Post by patrick295767 on 2005-11-27
If I recall well, I could do it (in the past) with john the ripper 
to do brute force ... 
  
I'll let you know about my progress !
  
Thank you again & very much !!
  
pat'

---

### Post by ssam on 2005-11-27
if you can do it with brute force then maybe you passwords are to weak.

---

### Post by patrick295767 on 2005-11-28
[QUOTE=ssam]if you can do it with brute force then maybe you passwords are to weak.[/QUOTE]

Hi ssam from manchester, 
  
If I recall well, a brute force with a...z 1...0   (no A...Z)
is only one-30 hours of calculations ... if I recall well

Have a good day & best regards, 

pat'

---

### Post by rooster on 2005-11-28
[QUOTE=patrick295767]
  
If I recall well, a brute force with a...z 1...0   (no A...Z)
is only one-30 hours of calculations ... if I recall well

[/QUOTE]

And if I recall well, it depends massively from the lenght of your password.

If you only have one character, you can even try it manually, but I don't think you have a computer at hand which can crack your password with 10 characers in 30 hours (or I strongly want to have your computer for my home).

Rooster

---

### Post by patrick295767 on 2005-11-28
I calculated with a regular brute force (saminside for windows syskey on) that a 10chars with a z   A Z 1  0  + exotic chars like # @
it could l take 1, 2-3 months for the password ... 
rather long calculation, isnt it ?
  
For my home passwd in linux, I should be able to get it from the dictionary
i have some idea of the passwd (i am the author, lucky me !!)
  
In my windows session, I use a  pwd with a ...z   A... Z 1...  0  + exotic chars like # @
and with **[SIZE="4"]24 [/SIZE]**characters, is it strong, i guess there is no way to enter this windows xp !
no login with copy ...system32/cmd.exe ...system32/logon.exe
'cos thsi is not working under XP windows

---

