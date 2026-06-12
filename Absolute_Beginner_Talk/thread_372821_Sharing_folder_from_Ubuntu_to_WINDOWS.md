---
title: "Sharing folder from Ubuntu to WINDOWS"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2007-02-28
I'm having real difficulty doing this, would appreciate if anyone can help me out.

I've shared a folder on my ubuntu box and.

I've gone to a windows machine on the local network and typed:

\\192.168.0.109\sharedfolder

and it just keeps giving me a login box. I've entered my root account details, tried adding another account and logging in with that and it's just not working.

Has anyone done this successfully? :(

---

### Post by noob919 on 2007-02-28
How do you get to the point you're at?  What's the first step to sharing files between Windows and Ubuntu?

---

### Post by linuxbun on 2007-02-28
> **noob919 said:**
> How do you get to the point you're at?  What's the first step to sharing files between Windows and Ubuntu?

I right clicked a folder in ubuntu and shared with samba :confused:

---

### Post by crossedout on 2007-02-28
Are you using Samba?  Its the simplest way I can think of for what you are trying to accomplish.
System->Administration->Shared Folders

If not, please elaborate on how you are accessing the sharedfolder.

-Xout

[EDIT] - Beat me to it.  Try this:
```
smbpasswd -a YOURUSERNAME
```

It prompts you for a password, enter anything you want.  The username should be a valid unix user not a windows username.  The changes affect only the Samba login info, not the normal ubuntu login information.

---

### Post by linuxbun on 2007-03-02
That did the trick, thanks for your help :KS

---

