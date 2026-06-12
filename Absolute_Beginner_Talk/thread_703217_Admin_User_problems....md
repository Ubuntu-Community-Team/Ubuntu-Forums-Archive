---
title: "Admin User problems..."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ndrwdnhm on 2008-02-21
Hi' I'm a first time user of Ubuntu but seem to have got myself into a bit of a pickle....

Once installed and after having a play i decided to create a new admin user, this worked just fine. I then decided to log off the existing admin user and onto the new. At this point i decided to see if i could delete the initial admin user profile, this worked. However when i restarted and logged back into the newly created admin user profile i had lost my admin rights. I logged off and attempted to logon as the deleted user - oddly this worked however i had lost the admin rights on this too...???

I appreciate that i possibly shouldn't have attempted to delete the initial user however i am now in a loop that i cannot get out of.

Any sugestions, i am thinking that a fresh install may be the simplest.

thanks

---

### Post by tangibleorange on 2008-02-21
OK. Try booting into the recover mode of Ubuntu (second option in the GRUB menu, you may need to press ESC to see it) when you first boot your PC. This should take you to a command prompt. From here, enter:

```
visudo
```

And try adding this line to the bottom of the file:

```
bob ALL=(ALL) ALL
```

Replace 'bob' with the username to whom you wish to grant admin user rights.

If you can't open the file for any reason, you could try this command:

```
echo 'bob ALL=(ALL) ALL' | tee -a /etc/sudoers
```

---

