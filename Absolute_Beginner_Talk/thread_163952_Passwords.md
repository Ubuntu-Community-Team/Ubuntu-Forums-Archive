---
title: "Passwords"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by cssutto on 2006-04-21
I understand root password and I understand user password.

What I do not understand is how Ubuntu uses them.

I want to change the root password.

I also want to change my user password.

It is my understanding from what I have read that there is no way for me to change the root password, that the user password is the only one I can change.

If that is correct, then there is not really a root password in Ubuntu.

Will someone please clear this up for me?

Is sudo passwd root really a command that will change the root, or is this just the user password?

CSSJR

---

### Post by taurus on 2006-04-21
If you want to change or create root password, open a terminal and type
```

sudo passwd root
(Type in your password, the one that you use to log in...)
(Now, type in root password.)
(Retype root password...)

```
But if you want to change your password, then just do
```

passwd

```

---

### Post by aysiu on 2006-04-21
[QUOTE=cssutto]
It is my understanding from what I have read that there is no way for me to change the root password, that the user password is the only one I can change.[/QUOTE] Can you post a link to what you've read?

I would suggest reading this instead (please read the entire document): [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by cssutto on 2006-04-21
To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root 

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

I have read the above several times and apparently misunderstood it.

I understood it to mean that it was changing only the original password to the new password, not that it is creating a new password in the name of root.

So then, this paragraph means that you would end up with the two passwords, one for root (the one created at this time) and the one used in the sudo command still the user password.

Is that correct?

I don't mean to be tedious, but paswords are as serious as it gets.

CSSJR

---

### Post by catlett on 2006-04-21
You are absolutely correct. It can be confusing when commands and outputs, etc are run together without explanation. But you have it  figured out now. This is how you become part of the forum. You'll see someone post a question asking the same thing and you'll be the one posting a reply explaining it. You might leave the best response because you have more insight into why there is confusion. Regards.

---

### Post by cssutto on 2006-04-22
Catlett:

Thank you for the kind words.

This is my first day on this forum.

I visited the blue one, not to call any names, for a couple of days and it is dead so I mucked around and found this one.

The first few minutes, I learned more than I expected to about firewalls.

For a MS user since Gates was working out of his garage, and one who is totally fed up with MS and all of its problems, I found the series on clamav and firestarter a real eye opener.

I can see this is the place to be.

Thanks again.

CSSJR

---

