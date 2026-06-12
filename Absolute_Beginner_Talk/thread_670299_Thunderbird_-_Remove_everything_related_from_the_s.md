---
title: "Thunderbird - Remove everything related from the system"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2008-01-17
My Thunderbird install got really really messy so I uninstalled using:

```
sudo apt-get remove --purge mozilla thunderbird
```

As far as I know this removes the applications only - Im guessing that the mails and extensions are still somewhere on my hard drive.

I would like to remove these so that the next time I install (If I do) Thunderbird I get a completely clean installation.


Anyone able to help me on this one?

---

### Post by Malta paul on 2008-01-17
Hi, You can check System>Administration>Synaptic Package Manager, then search for Thunderbird. Check all reference boxes are not ticked. if so the dependencies will also have be deleted.
Unfortunately if you have not saved your email address list by exporting it, you will have lost it.
Now just reinstall Thunderbird using Applications>add/remove>search Thunderbird and you will have a clean install.
Hope this is of help, Have fun:)

---

### Post by aysiu on 2008-01-17
Are you sure it's not your profile that's messed up instead of the installation?

Try these commands to get a fresh profile: ```
mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird.old
mv ~/.thunderbird ~/.thunderbird.old
``` If one of those commands errors out and says the folder doesn't exist, that's okay.

Then restart Thunderbird.

---

### Post by stchman on 2008-01-17
> **tigerplug said:**
> My Thunderbird install got really really messy so I uninstalled using:

```
sudo apt-get remove --purge mozilla thunderbird
```

As far as I know this removes the applications only - Im guessing that the mails and extensions are still somewhere on my hard drive.

I would like to remove these so that the next time I install (If I do) Thunderbird I get a completely clean installation.


Anyone able to help me on this one?

Use autoremove instead if remove.  Autoremove get rids of unused dependencies.

```
sudo apt-get autoremove thunderbird
```

After that remove the residual config in synaptic.

The mail and other settings are in the ~/.thunderbird folder.

---

### Post by tigerplug on 2008-01-18
> **aysiu said:**
> Are you sure it's not your profile that's messed up instead of the installation?

Try these commands to get a fresh profile: ```
mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird.old
mv ~/.thunderbird ~/.thunderbird.old
``` If one of those commands errors out and says the folder doesn't exist, that's okay.

Then restart Thunderbird.


Thanks :D

It kinda makes sense when you think about it!

---

### Post by aysiu on 2008-01-18
> **tigerplug said:**
> Thanks :D

It kinda makes sense when you think about it!
So it worked?

---

