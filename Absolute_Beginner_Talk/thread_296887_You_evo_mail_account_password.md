---
title: "You evo mail account password"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Camellia on 2006-11-10
Hi all

I've just found a file called evolution under my ~/.gnome2_private which contains my email account and an extremely poorly encrypted password to it.

I suppose that is the config file for the evolution mail, but does it suppose to be way to store user information? i.e. if someone gains access to my system, or just someone knows how to open that particular folder, then he/she can easily read my password, which is no good:( 

any ideas?

---

### Post by angryfirelord on 2006-11-10
I haven't used evolution, but just don't let it store the password. Sure that isn't the lazy way of doing things, but I always do that using Thunderbird.

---

### Post by Camellia on 2006-11-10
So that means I'll have to input the password every time I want to check my email. Grrrrr.

---

### Post by JayTee on 2006-11-10
It's always a tradeoff with operating systems. You can have it good, easy and secure just pick any two! Linux will give you good and secure, the other guy will give you good and easy.

---

### Post by taurus on 2006-11-10
Or change the permissions so nobody can view anything in your home directory, $HOME!!!

```
chmod 700 /home/john
```

---

### Post by adam.tropics on 2006-11-10
> **taurus said:**
> Or change the permissions so nobody can view anything in your home directory, $HOME!!!

```
chmod 700 /home/john
```

..which is fine, so long as you don't have any other accounts with 'sudo', else they can get in there anyway!

---

### Post by Camellia on 2006-11-11
Yes I know
<code>
sudo chmod 700 ~
</code>

is a way to prevent some other accounts from viewing  your home folder, but my question is what if someone acctually uses your account somehow to do things, like your friend or your partner. Is there a way to generate more secure encrypted password for evolution to use?

---

