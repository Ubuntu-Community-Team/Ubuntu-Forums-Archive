---
title: "Muliple accounts in Checkgmail"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by backflip on 2007-12-07
I've several gmail accounts but I only have the ability to check one at the moment, although checkgmail has the capacity to check multiple accounts.
Can someone please give  very  simple instructions regarding the following taken  from the  sourceforge site?

Can be run in multiple instances to check different mail accounts
Use the -profile=[profile name] command-line switch to set up a new account

Thanks

---

### Post by OrangeCrate on 2007-12-07
No experience here with Checkgmail, but there's a Firefox add-on called Gmail Manager that allows you to check multiple accounts, and it's easy as pie to set up. See here:

[https://addons.mozilla.org/en-US/firefox/addon/1320](https://addons.mozilla.org/en-US/firefox/addon/1320)

---

### Post by backflip on 2007-12-07
Thanks, I already use that, but it is only really useful if you have firefox running.
I thought someone would understand** Use the -profile=[profile name] command-line switch to set up a new account** I didn't think that command would be unique to checkgmail, butwould be  fairly easily understood, just not by me :(

---

### Post by Adam590 on 2008-01-31
Just figured this out today:


1. to set up a second profile (let's name it ***work***), enter this in a terminal:

```
checkgmail -profile=work
```

2. As this instance of checkgmail opens, it will take you straight to the preferences page. Enter your account info here. Done!

3. Access this second account by running that above bit of code in a terminal, or by creating a desktop or panel launcher with the code: /usr/bin/checkgmail -profile=work

---

### Post by backflip on 2008-01-31
Thank you, excellent, I appreciate the launcher code too. All  that would have been well outwith my ability.:)

---

