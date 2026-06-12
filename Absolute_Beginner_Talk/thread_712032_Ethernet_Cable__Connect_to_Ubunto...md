---
title: "Ethernet Cable  Connect to Ubunto.."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by EffeX on 2008-03-01
hello all.. I am new to Linux.. i normally use my windows xp on my laptop..

Normally i just plug the ethernet cable into the back of the p.c and baaam. internet on.

But with ubuntu.. I connect ethernet cable into back on computer.. and i load internet and it wont display..

how do i enable it?

thanx alot guys


EffeX

---

### Post by forrestcupp on 2008-03-01
Usually network cards are detected automatically.  Go to System->Administration->Restricted Drivers Manager and see if it lists your card for restricted drivers.  If so, install them and it should work.

---

### Post by EffeX on 2008-03-01
ehm.. what do you mean by network card.

my internet is virgin media.. i had it moved upstairs this moments and only now put OS onto my p.c

And when i click restricted drivers.. it says... It dont need too or something

Thanx for youre post anyway :/

---

### Post by EffeX on 2008-03-01
any other suggestions?

---

### Post by EffeX on 2008-03-01
Its a modem.. with a blue ethernet cable going straight from the modem into the back of the p.c

---

### Post by forrestcupp on 2008-03-01
The network card is the thing on the back of your pc that you connect the network cable into (also called an ethernet cable).  It is the part of your computer that is already inside your pc that takes the information from your modem into your computer.  You have to have proper drivers for it to work.  Usually Ubuntu automatically recognizes your network card and has the proper drivers built in.  Evidently, that didn't happen in your case.

So you checked the Restricted Drivers Manager and nothing showed up?

---

### Post by EffeX on 2008-03-01
oh i get it now..

And when i click restrricted it says.. Nothing needs to be restricted..

---

### Post by EffeX on 2008-03-01
something does not feel right here :( might my network card be disabled .. if it can?

---

### Post by forrestcupp on 2008-03-01
post the results of
```
lspci
```
from your terminal

also in the terminal, what does this say
```
uname -a
```
That tells what kernel you are using.  If you happen to be using the 386 kernel, you should switch to the Generic kernel.

---

### Post by EffeX on 2008-03-01
what are terminals or w.e

Im new to this stuff remember :D

---

