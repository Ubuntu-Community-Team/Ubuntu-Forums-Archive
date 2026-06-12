---
title: "Way too many users"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-19
Hello everyone

I am the only user on my machine, and /home/hari has all my required files. 

However, I find that there are a real lot of users and groups on my machine. Almost every software installation creates a new user. Apache built a www-data. MySQL created one. And what really gets me down is the user security. I can not use apache to Alias folders in my home directory (Permission Denied) because www-data doesn't have access.

Since I am the only user, how do I make my account "universal?" in other words, I want my user profile to have www-data properties, mysql data properties, proftpd user properties and everything?

---

### Post by Rackerz on 2005-12-19
Are you using Ubuntu for server purposes?

---

### Post by harisund on 2005-12-19
Yes. I am using it to run a server. Why? Security concerns? What do you suggest?

---

### Post by ertai on 2005-12-19
I would surely suggest to NOT make everything to one user. I would make the files apache need readable by everyone so www-data can also access them

---

### Post by harisund on 2005-12-19
Hmm... The problem is that I have different directories that I want accessible by Apache, all in my home folder. There is a photos folder, scanned comic pages folder so on and so forth. So you are suggesting that I just make the required folders readable (listable) for the www-data user?

---

### Post by ertai on 2005-12-19
yes.. I think that is the best solution.. but watch out.. only readable.. otherwise everyone can edit it..

---

### Post by harisund on 2005-12-19
> otherwise everyone can edit it...
Do I need to be worry about it? There is no account other than mine and root too is disabled. 

So how will I know which software creates which user, so that I can give that user permission?

---

