---
title: "Auto Logon Configuration"
date: 2005-04-13
forum: Apple PPC Users
---

### Post by derdewey on 2005-04-13
I installed Ubuntu as test on a Apple G3 Tower (I don't know when it was made, it's got a bubbly design, reminiscent of the first iMacs, with the clear plastic handles).  I installed it on a computer lab computer to test out, see how things go, you know?

Well, I don't know how to get the system to automatically boot into a user account (what kind of account settings do you folks recommend for a computer to be used by lots of folks who just walk in and want to type up papers, browse, etc?).  Help would be greatly appreciated (seeing as I can't find any info on this that isn't platform specific).

---

### Post by bihe on 2005-04-13
just alter the gdm settings. it is possible to check the autologin option, in the dropdown beneath select the user for auto-login.

---

### Post by Rxke on 2005-04-13
if you already did the full setup, it's equally simple. no need for terminal stuff etc.

Using the Gnome desktop environment, go to System, select the Administration section (could be another name, I'm not using the English version, so i'm guessing, here, it's the section with the computer icon next to it.

You could either make another user (I'd say this is the preferred way) with restricted powers, so that only you can do the altering of systemsessions etc...
To do that, go to the subsection in Administration(or whatsitscalled ) and select users and groups.

there you can make another user. pick a name that's simple and maybe a password that's simple, too, because you won't be using it later on (autologin)
you can go to more settings there, if not sure, use the help button to figure things out.

next, go to the same subsectin (administration) and select Settings for Loginscreen, there you just check the box 'log in a user automatically,'
and select the new user you made right beneath there

Done. From now on the system boots in as that new usersettings without asking for uid or pswd.

---

### Post by packjamNL on 2007-05-26
so if you have 2 user-accounts, you can auto-login(on), 
I want my only user-account to startup without passwds;

---

