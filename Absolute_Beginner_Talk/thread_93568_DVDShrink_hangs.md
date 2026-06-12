---
title: "DVDShrink hangs"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Luc1fer on 2005-11-22
Hi everyone,

I have just installed DVDShrink and it semmed to work just fine until I layed my hands on a DVD to test on. Everything works just fine until it gets to 37%. I have tried several different DVD's and several times with the same DVD.

However it allways hang at 37%. This made me thing about that it maybe is the emulated filesystem that dont suport so big files (am i wrong?).

So i guess that my question is if there is any way to change the emulated filesystem?

---

### Post by Paloseco on 2005-11-22
where is dvdshrink available for GNU/Linux? :confused:

---

### Post by Luc1fer on 2005-11-22
hmms... sorry... missed that part :p,

I use it together with Wine thats where my theory comes, so i just use the windows version.

---

### Post by Original Brownster on 2005-11-22
[QUOTE=Luc1fer]Hi everyone,

I have just installed DVDShrink and it semmed to work just fine until I layed my hands on a DVD to test on. Everything works just fine until it gets to 37%. I have tried several different DVD's and several times with the same DVD.

However it allways hang at 37%. This made me thing about that it maybe is the emulated filesystem that dont suport so big files (am i wrong?).

So i guess that my question is if there is any way to change the emulated filesystem?[/QUOTE]

I'ts working fine here, did you follow the howto posted on the ubuntu wiki? I followed this and it worked a charm. It says to use wine from the wine hq repository rather than from within the normal ubuntu repository.

There is no other reason I can think of why it would hang other than running out of space on the partition you are using but I guess you have checked that already.

:p

---

### Post by Luc1fer on 2005-11-23
Ok.

Yes I used the Wine version you could find on WineHQ. But i hadnt followed the HowTo on the Wiki. Did that now so I am currently testing.

It Worked! :)

---

