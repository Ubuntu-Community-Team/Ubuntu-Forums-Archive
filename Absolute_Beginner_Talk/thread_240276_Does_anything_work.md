---
title: "Does anything work?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Mourneblade on 2006-08-20
I have just installed Ubuntu (3 hours ago).  Since then I have got absolutly nothing to work, except for the built in web browser.  This is very irritating.  I have attempted to look at quite a few 'HowTo' posts on these forums, but they all seem to assume that I have much more understanding about Ubuntu than I do.  Here are the 2 things I have been attempting to do:

1.  Change the screen resolution.  I only have the choice of using 600x800 which is not good.  I have Nvidia 6600 card.

2.  Install Java.  I have downloaded it, and have read I need to go to Terminal and type su and then enter a password.  None of the passwords I have entered have been accepted.  So now I cannot proceed any further with this installation.

This would seem to be a very nice OS to have and use and to replace my Windows XP Pro, but so far I have been so frustrated with it all.  There has to be an easier way to make this all work, or at least a 'HowTo' that acctually works.

---

### Post by jason.b.c on 2006-08-20
> **Mourneblade said:**
> I have just installed Ubuntu (3 hours ago).  Since then I have got absolutly nothing to work, except for the built in web browser.  This is very irritating.  I have attempted to look at quite a few 'HowTo' posts on these forums, but they all seem to assume that I have much more understanding about Ubuntu than I do.  Here are the 2 things I have been attempting to do:

1.  Change the screen resolution.  I only have the choice of using 600x800 which is not good.  I have Nvidia 6600 card.

Sounds like your ( maybe ) nvidia drivers aren't installed , There's a HOW-TO section here describing how to install them...

> 2.  Install Java.  I have downloaded it, and have read I need to go to Terminal and type su and then enter a password.  None of the passwords I have entered have been accepted.  So now I cannot proceed any further with this installation.

This would seem to be a very nice OS to have and use and to replace my Windows XP Pro, but so far I have been so frustrated with it all.  There has to be an easier way to make this all work, or at least a 'HowTo' that acctually works.

Is it a **.deb**...?  If so then:

```
sudo dpkg -i

``` then put a space after the **-i** and grab the package and drag it into the terminal , make sure the cursor is blinking and press enter...

---

### Post by DC@DR on 2006-08-20
Wow, it seems like you're completely new to Ubuntu. The best place to go is this: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper). Keep exploring this page, it should guide you thru many useful things, and then if there's smth that you don't understand, go here, **search first**, and then post questions. Good luck with your adventure to Linux/Ubuntu world...:)

---

