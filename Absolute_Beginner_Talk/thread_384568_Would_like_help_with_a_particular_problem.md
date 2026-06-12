---
title: "Would like help with a particular problem"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by raidlost on 2007-03-14
MAN cos when one needs help the last resort is to chip in and say

[FONT="Arial Black"]***[COLOR="DarkRed"][SIZE="3"]HELP![/SIZE][/COLOR]***[/FONT]

Thanx  (sorry to have got your attention in this way)

I know that the posts were drastic but as you can see from my threads ----
My work has asked me to setup the following and I suggested Ubuntu now I have to either sort it out or use something else...\

We need 
A base installation of an OS that is on RAID 1 ( I think I have it, as I did it during the installation but I have not successfully booted into it)
we must remotely administer ( I have ssh and remote desktop all setup and working)
network connectivity and name resolution is up and working
time server needs to synchronize with our PDC ( can't get it working, time is the same)
kerberos authentication to the PDC (works - getent and wbinfo tests work)
text based mail client to send sarg reports automatically at 00:10 to admin@domain (can't get mailx to send successfully - it worked and when I added samba I no longer receive mail and nothing in the queue) 
samba for file shares for admin ( had it working but since kerberos was set up I no longer connect - insufficient permission error)
apache (working like a charm)
and most importantly SQUID (no matter what I try I can't get it to work - I keep getting authentication errors in Mozilla)
lastly - sarg for squid reporting. (have not got squid to work yet)

**I have hunted high and low** been through numerous docs and am at my wits end 

if you could help I would make a wookiee life pact

---

### Post by ComplexNumber on 2007-03-14
right, if you want help, then state what your problem is by editing your first post. i've split your post off from the other thread because it doesn't concern that thread (although i'm not sure what it does concern). please don't hijack other peoples threads. its not nice.

---

### Post by darrenm on 2007-03-14
Raidlost, if you are for real then I'm ready to help. As said edit the first post in this thread and state what your problem is. There are better ways to get attention though.

---

### Post by gus sett on 2007-03-15
**return visit** please let know if searching on mailx *didn't*
spawn new :idea:

now there is the coherent voice with the reputation--welcome back.
you are natural at sorting this stuff.  There's the mailx thread elsewhere
perhaps samba/PDC could be this one, SQUID and two more others
would be juggleable.

:?: What boxes are available to you for Ubuntu. This is a
lot to try on one chassis concurrently, so what's composition(s)


> **raidlost said:**
> MAN cos when one needs help the last resort is to chip in and say

[FONT="Arial Black"]***[COLOR="DarkRed"][SIZE="3"]HELP![/SIZE][/COLOR]***[/FONT]

Thanx  (sorry to have got your attention in this way)

I know that the posts were drastic but as you can see from my threads ----
My work has asked me to setup the following and I suggested Ubuntu now I have to either sort it out or use something else...\

We need 
A base installation of an OS that is on RAID 1 ( I think I have it, as I did it during the installation but I have not successfully booted into it)
we must remotely administer ( I have ssh and remote desktop all setup and working)
network connectivity and name resolution is up and working
time server needs to synchronize with our PDC ( can't get it working, time is the same)
kerberos authentication to the PDC (works - getent and wbinfo tests work)
text based mail client to send sarg reports automatically at 00:10 to admin@domain (can't get mailx to send successfully - it worked and when I added samba I no longer receive mail and nothing in the queue) 
samba for file shares for admin ( had it working but since kerberos was set up I no longer connect - insufficient permission error)
apache (working like a charm)
and most importantly SQUID (no matter what I try I can't get it to work - I keep getting authentication errors in Mozilla)
lastly - sarg for squid reporting. (have not got squid to work yet)

**I have hunted high and low** been through numerous docs and am at my wits end 

if you could help I would make a wookiee life pact

---

