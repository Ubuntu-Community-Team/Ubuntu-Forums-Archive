---
title: "su dos not work but root terminal does"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-08-14
Oke open Terminal say "su" give passw:
paul@Paul:~$ su
Password:
su: Authentication failure
Sorry.
paul@Paul:~$

Open root terminal, he askes:
"Please enter your password to run /usr/bin/x.terminal-emulator

Then I give the same password and then I get a rot terminal !

Why not with "su" ??

---

### Post by sophtpaw on 2005-08-14
[QUOTE=Dutch]Oke open Terminal say "su" give passw:
paul@Paul:~$ su
Password:
su: Authentication failure
Sorry.
paul@Paul:~$

Open root terminal, he askes:
"Please enter your password to run /usr/bin/x.terminal-emulator

Then I give the same password and then I get a rot terminal !

Why not with "su" ??[/QUOTE]


Ubuntu works with sudo, not su. Slightly different system than you might be used to with other GNU/Linux flavours, but just as effective, and one less password to remember, so arguably easier?

See: [https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

Enjoy,

--
sophtpaw

---

### Post by Dutch on 2005-08-14
[QUOTE=sophtpaw]Ubuntu works with sudo, not su. Slightly different system than you might be used to with other GNU/Linux flavours, but just as effective, and one less password to remember, so arguably easier?

See: [https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

Enjoy,

--
sophtpaw[/QUOTE]


Oke Thanks !

---

### Post by transactionlogfiller on 2005-08-14
The important thing to notice is it says give _your_ password for the root terminal. You have to give root's password for su, and after a fresh ubuntu install root doesn't have a password so you can't use the account.

Personally, the first thing I do is "sudo passwd root", set a root password and then use su. Perhaps I'm old fashioned.

Can someone explain the pros/cons of sudo? Other than less passwords to remember.

---

