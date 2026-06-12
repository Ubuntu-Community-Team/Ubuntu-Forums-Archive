---
title: "Whats the benefits of having your .home directory on a different partition?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-11-17
Hi. I was wondering what are the benefits of having your .home directory on a different partition?

---

### Post by petit.padavoine on 2006-11-17
If you mess up one partition while re-partitioning, your data is safe.
Other than that, no idea... :)

---

### Post by localuser on 2006-11-17
> **jincast90 said:**
> Hi. I was wondering what are the benefits of having your .home directory on a different partition?

You can reinstall the OS without losing your data.

---

### Post by Metacarpal on 2006-11-17
> **localuser said:**
> You can reinstall the OS without losing your data.

Bingo.  You can reinstall, upgrade, etc without losing any of your personal data.  I recently did a fresh install on my system with a separate /home partition.  Once the install was done, I just added the same users I had previously - it recognized their existing folders from the previous install automagically.  When I logged in under the different accounts, all the original personal settings had been applied, so the desktop look was preserved, in addition to the files and folders.

---

### Post by justin whitaker on 2006-11-17
Nice trick. I assume that also means that I could install multiple Linux or BSD versions, and have them pick up the /home drive? 

Say, for example, Dapper and Feisty, or Dapper and Edgy?

---

### Post by klerfayt on 2006-11-17
> **justin whitaker said:**
> Nice trick. I assume that also means that I could install multiple Linux or BSD versions, and have them pick up the /home drive? 

Say, for example, Dapper and Feisty, or Dapper and Edgy?
Only if you use different user names for every os.
Example: you are "bob" in dapper & "dave" in edgy

---

### Post by petit.padavoine on 2006-11-18
> **localuser said:**
> You can reinstall the OS without losing your data.
Not only data, but also configuration for your apps!

---

### Post by jaboua on 2006-11-18
> **klerfayt said:**
> Only if you use different user names for every os.
Example: you are "bob" in dapper & "dave" in edgy

It is possible with the same usernames as well, but that isn't reccomended as the distros might have different versions of apps and it can result in conflicting settings.

I would rather do as mentioned, make different user accounts, and then symlink the folders containing personal files around. Make sure that the users have the same UID though, so you won't get permission problems.

---

