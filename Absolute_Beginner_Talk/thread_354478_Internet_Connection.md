---
title: "Internet Connection"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Grateful_Justin on 2007-02-06
Well I used the same command I do every time to get the internet up and running. PPPoE config.  It used to make the internet run fine and now ... well it doesn't.  So am I typing something wrong or what?  I am kinda frustrated and tired so I am sure that doesn't help any whatsoever, but at any rate I need this to work by tomorrow because tomorrow I am deleting Windows completely.  Any help would be appreciated.   












Grateful_Justin 	](*,)

---

### Post by shareMenaPeace on 2007-02-06
Check the readme

Select the "?" icon on top of the Desktop panel, to start the Ubuntu Help Centre.
Select Working with your desktop.
Select Internet.
Select Connecting to the Internet.
Select ADSL Connections.

Follow this page i think basicly you just need to run this command from a terminal 
Application -> Asseccoires -> Terminal

```
sudo pppoeconf
```
than type in your password and follow the install - i didnt had to enter ra password and used default settings.

But read the page first maybe i forgott something :)

---

### Post by Grateful_Justin on 2007-02-06
Now I know I am WAY WAY WAY to tired to be on the computer this is what I typed 


sudo pppoe conf

I put a space in between the pppoe and conf.  WOW..

Thank you.

now to bed with me.

---

### Post by kvonb on 2007-02-06
Use synaptic and search for "gpppon" and install it, it's a simple GUI frontend for connecting/disconnecting, I use it on my server :).

---

