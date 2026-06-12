---
title: "Is my password to complicated for Gutsy? :S"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-11-10
Hi.
My password is 17 characters long and has Capital and small letters, numbers and special characters. Is this a too complicated password for Gutsy? It worked in fiesty...
When I changed to that passwd I wasn't able to log in on ctrl+alt+f7 but I was able to log in on ctrl+alt+f1 and when I change the passwd to something easier like just 1 character in ctrl+alt+f1 I can login again on ctrl+alt+f7 with the new password... This is really weird, does anyone know what to do?

---

### Post by chlorinekid on 2007-11-10
> **spydon said:**
> Hi.
My password is 17 characters long and has Capital and small letters, numbers and special characters. Is this a too complicated password for Gutsy?

i'm not sure whether or not there is some sort of restriction on password length but is a password that long and complicated really necessary? :/

---

### Post by matthewcraig on 2007-11-10
[http://ubuntuforums.org/archive/index.php/t-2444.html](http://ubuntuforums.org/archive/index.php/t-2444.html)

This forum post seems to indicate the limit is 15 characters.

---

### Post by spydon on 2007-11-10
WTF is the point of having a character limit? :confused:
I don't want to be brute forced...

---

### Post by Dripbagulhos on 2007-11-10
> **matthewcraig said:**
> [http://ubuntuforums.org/archive/index.php/t-2444.html](http://ubuntuforums.org/archive/index.php/t-2444.html)

This forum post seems to indicate the limit is 15 characters.

Well... I may be loosing something on the conversation, but my password has 22 charactteres and I have had any trouble with it... I used to login with GDM, text mode and KDM with Feisty and Gutsy. I suspect that the problem is not the lenght of the password, but the "special" characters... Why don't you try, just for experimentation purposes, to put a 30 char passwsord, using only letters (upper case and lower case) and numbers. See if this work. If it does work, try to insert, one by one, the special chars that you have on your password. 

Just an idea! :-)

---

### Post by Harpoon on 2007-11-10
This makes me wonder...

Back in the days of linux 1.+, you could input a password of almost any length, but only the first 8 characters were actually used. 

Haven't thought about this in a long while, but I wonder if the setup we have today is working on the same basic principle.  If so, a troublesome special character at position 15 **might** be the cause of the problem.

---

### Post by mivo on 2007-11-10
Unless I am mistaken, it's still true that only the first eight characters are considered by the DES algorithm.

---

### Post by spydon on 2007-11-10
But it worked in fiesty... If it still uses the same algorithm and doesn't have any limit it should be working but it doesn't](*,)
Does anyone know if they have changed anything?

---

