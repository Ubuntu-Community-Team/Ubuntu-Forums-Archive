---
title: "locked out my administrator account"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Alpha Actual on 2007-08-18
I set up a user ( limited) account an then I set that account to load on boot. 

I checked the box allowing local admin login but when i select "switch user", only the user account shows up.

I am unfamiliar with recovery mode options.  OOPS

Help!:(

---

### Post by taurus on 2007-08-18
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by pbwalker on 2007-08-18
When you say "Admin" account, are you refering to the root account? Can you login at all?

Anyways, if you need to reset the root password, you can do so by getting into GRUB (hit the appropriate key when it tells you on boot) and add "single" (no quotes) to the end of your kernel arguments. This will boot you into single user mode. Once you get a command shell, type 'passwd' (again, no quotes) and give it a new password...

---

### Post by Alpha Actual on 2007-08-18
yes, 

I am currently logged in as user but have no admin privlidges

What I intended to do was have the limited account automatically log in on boot with the option 

to switch to root account using a password.

Setting up an account for a youngin to play games on but not do to much else. 

 LoL   :oops:I might have locked out the right person! Me :oops:

---

### Post by pbwalker on 2007-08-18
so you have no root access? That is the admin you are talking about?

I assume you can't su into root at all?

---

### Post by Alpha Actual on 2007-08-18
couldnt get  terminal command right

---

### Post by pbwalker on 2007-08-18
Go ahead, reboot into GRUB (hit the appropriate key when it tells you on boot...you have 3 seconds or so to do it). Once you are in, go to (usually) the 2nd line and add "single" (no quotes) to the end of your kernel arguments. This will boot you into single user mode. Once you get a command shell, type 'passwd' (again, no quotes) and give it a new password...

Let me know if that works for you!

---

### Post by Alpha Actual on 2007-08-18
Yea!!  Thanks so much!!

---

### Post by pbwalker on 2007-08-18
Glad it worked out for you!!

---

