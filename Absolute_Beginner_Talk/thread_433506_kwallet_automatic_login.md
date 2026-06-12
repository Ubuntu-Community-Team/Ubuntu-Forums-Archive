---
title: "kwallet automatic login"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-05-05
Is there a way to automatically unlock the kwallet on login? In Gnome you can use libpam-keyring to do it. I just get tired of loging in, then putting my password in once more for knetworkmanager.

---

### Post by junior28862 on 2007-05-06
I hear ya!  I hate that stupid thing!

---

### Post by jetpeach on 2007-05-11
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/kde-pwmanager](https://launchpad.net/ubuntu/+source/kde-pwmanager) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				yeah, i've been wanting this forever. 
is there a bug filed in launchpad for this? i'll look

hmm, looking on launchpad (which i'm not particularly familiar with) i'm not even finding kwallet, but instead seeing "kde pwmanager". looking on the web, i find this description of pwmanager

"PwManager is a secure password manager.
With PwManager you can easily manage your passwords. PwManager saves your passwords blowfish-encrypted in one file, so you have to remember only one master-password instead of all. Instead of the master-password you can use a chipcard, so you don't have to remember a password at all."

this sounds like exactly what we want. i have a feeling they're replacing kwallet with pwmanager or something like that. hopefully it will be fixed in gutsy. there may be a way already by using pwmanager - anybody care to search for it?

---

### Post by HeinzGas on 2007-05-14
> **DSn0wMan said:**
> Is there a way to automatically unlock the kwallet on login? In Gnome you can use libpam-keyring to do it. I just get tired of loging in, then putting my password in once more for knetworkmanager.

Try removing the password - it does not automatically login, but the first program asking for data will open it without asking for a password.

Heinz

---

