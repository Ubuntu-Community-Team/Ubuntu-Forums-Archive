---
title: "Root login for PPPOECONF?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-07-07
Ok, I want to make a pppoe connection for another user on the computer, the problem is that when I type :

sudo pppoeconf

it responds that I have to login as root. I know that its not good to login as root as it can cause many problems by mistake. So what can I do? I mean can I login as root, and how do I login as root?

---

### Post by Outrunner on 2007-07-07
Doesn't it ask you for a password?

---

### Post by ayed on 2007-07-07
sorry no, cuz when I use the sudo nothing shows up, it tells me to login as root when I only use the pppoeconf alone.

---

### Post by Outrunner on 2007-07-07
Ohh, well that seems strange. Of course, I've never tried to do this so I have no idea what I'm talking about, but maybe this will make a difference?

```
sudo -s
```

```
pppoeconf
```

---

### Post by opossumjack on 2007-07-07
I'm not so sure, but also this command should work...

> sudo -i

It would bring you up the root console. ;)

---

### Post by ayed on 2007-07-07
Nothin worked! Just to clear up, I made this user by going from my account to the system then to the administration then to Users and Groups. So in the terminal its like:
john@josef: $

Help please?

---

### Post by opossumjack on 2007-07-07
Hi, I've checked...

> sudo -i

it's the right command to get a root terminal. It will ask your user password to work.

Also.. Did you give Admnistrator privileges to your use, when you created it?

---

### Post by bme on 2007-07-07
"sudo passwd"
to make a root passwd

" su"
for root,when promted for password enter the passwrd created above

---

### Post by Outrunner on 2007-07-07
> **bme said:**
> (quote)sudo passwd(/quote)
to make a root passwd

(quote) su(/quote)
for root,when promted for password enter the passwrd created above

This is NOT good idea, you aren't supposed to login with root like that in Ubuntu

---

