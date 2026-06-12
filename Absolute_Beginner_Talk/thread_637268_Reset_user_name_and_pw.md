---
title: "Reset user name and p/w"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by bill814 on 2007-12-10
I have installed 7.04 several times and always use the same user and p/w.Suddenly, it does not recognize my user name and/or p/w. I tried CTRL ALT F1, but it does notr respond since it does not recognize my user name which is "bill". Anyways, I guess That is why it is noit responding.
Thanks, Bill

---

### Post by nikoPSK on 2007-12-10
boot into recovery mode then type this:

passwd <user>

---

### Post by LookTJ on 2007-12-10
> **nikoPSK said:**
> boot into recovery mode then type this:

passwd <user>
doesn't recovery mode make you root? If so, you would have to do passwd [username]?

---

### Post by Dr Small on 2007-12-10
Doing passwd <user> is to change the user's password.

---

### Post by nikoPSK on 2007-12-10
I know, he wants to change it so....

---

### Post by Teknyk on 2007-12-13
Sorry to revive a days old thread but I have a question along similar lines.
I bring my laptop to work with me and I can't always carry it when I leave my desk. I do lock it when I leave and yes I am aware that anyone using the recovery method will alert me once I realize my password is not working but that's a day late and a dollar short. Kind of like coming home and finding your door has been kicked in, you know you have been broken into but that doesn't bring back your TV.

How can I make it so you **do not** automatically get root access when booting into recovery mode?
Ideally I would like to (if need be) boot to recovery mode and be prompted for the root password and **then** be able to change user passwords.

Does this require enabling the root account even though I have read this is a no-no?
If I do enable to root account will I have to use the root password for sudo when logged in as a user?

I guess in a nutshell my question is, what is best practice when complete and total  physical security is not an option?

---

### Post by Dr Small on 2007-12-13
Teknyk, please read this:
[http://php.8ez.com/drsmall/blog/?p=176](http://php.8ez.com/drsmall/blog/?p=176)

Skip down to Grub Password, and read from there.
That will set a password on the Recovery Mode entry, keeping people from booting into recovery mode and logging in as root.

Dr Small

---

