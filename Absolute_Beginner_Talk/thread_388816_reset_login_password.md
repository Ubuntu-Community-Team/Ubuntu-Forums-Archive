---
title: "reset login password"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2007-03-19
I gave my brother in law a computer preinstalled with ubuntu. (it seemed like a good idea at the time), I thought what could go wrong?

I know that every thing was working when I gave it to him, including the user name and password. 

On the first day he logged of and now he says that he cannot login. 

The original password was simply “password” so i can only assume that he decided to to some how change the user password to another super secret user password, then forgot the password. 

Well anyway, I know what is the root password. 

I there a way that I can go in and reset his maybe via command line?

---

### Post by Jason Weiss on 2007-03-20
It sounds like I should just reinstall?

---

### Post by Efwis on 2007-03-20
you don't have to reinstall, log in and create  new user account, after the account is created, you should be able to delete the original account and use the new one as the primary.

---

### Post by dreadlord_chris on 2007-03-20
> **Jason Weiss said:**
> I gave my brother in law a computer preinstalled with ubuntu. (it seemed like a good idea at the time), I thought what could go wrong?

I know that every thing was working when I gave it to him, including the user name and password. 

On the first day he logged of and now he says that he cannot login. 

The original password was simply &#8220;password&#8221; so i can only assume that he decided to to some how change the user password to another super secret user password, then forgot the password. 

Well anyway, I know what is the root password. 

I there a way that I can go in and reset his maybe via command line?

Log in to root:

```

passwd <username>

```

then just follow the prompts

---

### Post by Jason Weiss on 2007-03-20
> **Efwis said:**
> you don't have to reinstall, log in and create  new user account, after the account is created, you should be able to delete the original account and use the new one as the primary.


GREAT almost there, can I create a new account with out being able to log in?

maybe through recovery mode?

---

### Post by Efwis on 2007-03-20
since you know the root password, I assume you also know the username to log in as root, therefore you should be able to login as root with recovery mode.

if I recall correctly, and I could be wrong, never tried this myself, the  username should be the original one you set up, then you just enter the root password.

I could be wrong, since I don't change the root password, or go into root except to install programs that require root access.
Another thing you can do if you are successful in logging in as root, is do as dreadlord_chris suggested.

---

### Post by Jason Weiss on 2007-03-20
oh ok and to log on as root I just need to go into recovery mode need to log in with my user name and root password in recovery mode, is that right?

Can I just hit ctrl-f2 from the logging screen ?  will this take me to recovery mode or am i thinking of something different?

---

### Post by scxtt on 2007-03-20
rebooting into recovery mode doesn't require a password, just physical access to the box ...

---

### Post by Jason Weiss on 2007-03-20
Man I love linux more and more every day.  If I had this problem with windows i would have a real problem. 

As i keep telling people I meet, Nothing is impossible with linux, 

Thank you all again for you help.

Jason

---

### Post by Efwis on 2007-03-20
> **Jason Weiss said:**
> oh ok and to log on as root I just need to go into recovery mode need to log in with my user name and root password in recovery mode, is that right?

Can I just hit ctrl-f2 from the logging screen ?  will this take me to recovery mode or am i thinking of something different?

This won't take you to recovery mode, however you can still log in as root from there using your username and password combo.

doing that gives you access to either make the new user account, which I'm not sure how to do that in terminal mode, or you can change the password for the username you need to change it for.

so once your are in the terminal, do the following
```

sudo passwd username

```
It will ask you for the current password for that username
then it will ask you to type in the new password and then re-type it.

it could be as simple as a case that your brother forgot how to properly put in the password. i.e. case sensitivity.

---

### Post by sean_gilmore on 2007-03-20
I just installed using Wubi, and i have no idea what to do

i installed using Wubi-7.04-herd4-v6 first, but that didnt work at all on the boot

so then i tried with Wubi-7.04-herd4-v4 (after uninstalling the first one)

and then it worked but won't let me log in

first i did Sean Gilmore and my password

and it didnt work

i figured maybe it was cuz i had a space in the name and it was an alphanumeric pass

so i uninstalled and reinstalled again, and used Sean and password

and again, it did not work


im a noob, so i really need installer advice

if anyone could talk person to person please IM: Sean Then Said

---

