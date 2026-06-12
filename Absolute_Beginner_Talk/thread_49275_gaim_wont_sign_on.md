---
title: "gaim wont sign on???"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-15
Help! I installed aMSN (what a joke) and now I can't sign in with GAIM...actualy it signs in ok but it gets stuck at "retrieving buddy list"...what the hell?

---

### Post by Skel on 2005-07-15
Why did ya install aMSN all i did was add a MSn account didnt need anything like aMSN :/ and check if ur passwords and info is correct.. mayeb thats it.

---

### Post by RastaMahata on 2005-07-15
have you quit aMSN before logging into gaim? I don't know, it might work :P

---

### Post by gammyhand on 2005-07-15
[QUOTE=Skel]Why did ya install aMSN all i did was add a MSn account didnt need anything like aMSN :/ and check if ur passwords and info is correct.. mayeb thats it.[/QUOTE]
Exactly how is that useful in any way, shape, or form, to my problem?

I installed aMSN because I wanted to see what it was like. I was already using GAIM for my msn account.

---

### Post by RastaMahata on 2005-07-15
[QUOTE=gammyhand]Exactly how is that useful in any way, shape, or form, to my problem?

I installed aMSN because I wanted to see what it was like. I was already using GAIM for my msn account.[/QUOTE]
 anyway, did you uninstall aMSN??

---

### Post by gammyhand on 2005-07-15
[QUOTE=RastaMahata]anyway, did you uninstall aMSN??[/QUOTE]
 yes. I uninstalled amsn..it connects fine (gaim) it just can't get the buddy list....??

---

### Post by RastaMahata on 2005-07-15
[QUOTE=gammyhand]yes. I uninstalled amsn..it connects fine (gaim) it just can't get the buddy list....??[/QUOTE]
 hrm, strange... try logging though [http://webmessenger.msn.com](http://webmessenger.msn.com)
If you can log in, its a gaim problem. If you cant, then some server is down or something. Please report back ;)

---

### Post by gammyhand on 2005-07-15
[QUOTE=RastaMahata]hrm, strange... try logging though [http://webmessenger.msn.com](http://webmessenger.msn.com)
If you can log in, its a gaim problem. If you cant, then some server is down or something. Please report back ;)[/QUOTE]
Well GAIM logs in fine and handshakes fine. It's when it tries to download my buddy list it sandboxes.

---

### Post by gammyhand on 2005-07-15
[QUOTE=gammyhand]Well GAIM logs in fine and handshakes fine. It's when it tries to download my buddy list it sandboxes.[/QUOTE]
 Oh and I just logged in fine on webmessenger :(

---

### Post by RastaMahata on 2005-07-15
[QUOTE=gammyhand]Oh and I just logged in fine on webmessenger :([/QUOTE]
 delete you account from gaim, close it. then start gaim again, create a msn account with your data and try to start again. might work.

---

### Post by gammyhand on 2005-07-15
[QUOTE=RastaMahata]delete you account from gaim, close it. then start gaim again, create a msn account with your data and try to start again. might work.[/QUOTE]
 will give that a go....

---

### Post by gammyhand on 2005-07-15
[QUOTE=gammyhand]will give that a go....[/QUOTE]
 nope. what the hell is going on :(

---

### Post by RastaMahata on 2005-07-15
[QUOTE=gammyhand]nope. what the hell is going on :([/QUOTE]
 damn weird. Reinstalling gaim didnt work out?

please type this in your console```
gaim --debug > log
```
This will output everything gaim does in a log file. After you reach the point where it doesnt connect, wait 10 seconds, then close gaim, and attach the log file in here (it should be in your home directory)

---

### Post by gammyhand on 2005-07-15
Thanks for your help :) Log is attached...I had to remove a few of the contact names from the log so it would fit as an attachment...who set the rather prehistoric 20kb limit anyway?

---

### Post by RastaMahata on 2005-07-16
[QUOTE=gammyhand]Thanks for your help :) Log is attached...I had to remove a few of the contact names from the log so it would fit as an attachment...who set the rather prehistoric 20kb limit anyway?[/QUOTE]
 sudo apt-get --purge remove docker imlib-base imlib1 libpng10-0 libungif4g tcltls

try to do that and see if it works... I think it might be only tcltls...

---

### Post by gammyhand on 2005-07-16
[QUOTE=RastaMahata]sudo apt-get --purge remove docker imlib-base imlib1 libpng10-0 libungif4g tcltls

try to do that and see if it works... I think it might be only tcltls...[/QUOTE]
 I removed all of them apart from libungif4g as it said it was going to remove mplayer plugins etc and still I cannot sign on :(

---

### Post by RastaMahata on 2005-07-16
[QUOTE=gammyhand]I removed all of them apart from libungif4g as it said it was going to remove mplayer plugins etc and still I cannot sign on :([/QUOTE]
 how about sudo apt-get --purge remove gaim ? then install it again.. :(

---

### Post by gammyhand on 2005-07-16
[QUOTE=RastaMahata]how about sudo apt-get --purge remove gaim ? then install it again.. :([/QUOTE]
 Nope :( what the hell? It was working fine until I put on bloody aMSN.

---

### Post by RastaMahata on 2005-07-16
[QUOTE=gammyhand]Nope :( what the hell? It was working fine until I put on bloody aMSN.[/QUOTE]
 I'm sorry I cant help you any more for today. It sure seems like a gaim problem.
I need to sleep now :(
I hope someone else can help you. Its really weird!

---

### Post by gammyhand on 2005-07-16
[QUOTE=gammyhand]Nope :( what the hell? It was working fine until I put on bloody aMSN.[/QUOTE]
 I just tried logging on with my icq account in gaim and that was fine. I am totally confused!

has aMSN left any config files behind or something?

---

### Post by gammyhand on 2005-07-16
[QUOTE=RastaMahata]I'm sorry I cant help you any more for today. It sure seems like a gaim problem.
I need to sleep now :(
I hope someone else can help you. Its really weird![/QUOTE]
No problem. Thanks for all your help :)

---

### Post by gammyhand on 2005-07-17
[QUOTE=gammyhand]No problem. Thanks for all your help :)[/QUOTE]
 no-one?

---

### Post by lothar_m on 2005-07-17
hi there

i'm having the same problem. Gaim doesn't connect to msn. It stops when downloading the buddy list from the server.

In my experience it's not related with amsn. As far as i can tell there is a bug with gaim. 

I googled around and it seem to me that when you add a buddy who's email as a  certain number of characters (or some type of characters) it prevents gaim from downloading the buddy list.

Unfortunately it seems that for now the only way to deal with this is to delete the buggy contact (if you know which one is it).

---

### Post by gammyhand on 2005-07-17
[QUOTE=lothar_m]hi there

i'm having the same problem. Gaim doesn't connect to msn. It stops when downloading the buddy list from the server.

In my experience it's not related with amsn. As far as i can tell there is a bug with gaim. 

I googled around and it seem to me that when you add a buddy who's email as a  certain number of characters (or some type of characters) it prevents gaim from downloading the buddy list.

Unfortunately it seems that for now the only way to deal with this is to delete the buggy contact (if you know which one is it).[/QUOTE]
 where would I delete the buggy contact? In my hotmail contacts list?

---

### Post by gammyhand on 2005-07-18
[QUOTE=gammyhand]where would I delete the buggy contact? In my hotmail contacts list?[/QUOTE]
 I tried deleting some contacts (and I added since I know it WAS working) and I still can't sign on.

---

### Post by gammyhand on 2005-07-20
[QUOTE=gammyhand]I tried deleting some contacts (and I added since I know it WAS working) and I still can't sign on.[/QUOTE]
 Sigh....do you think if I re-install hoary that GAIM will start working again? :(

---

### Post by gammyhand on 2005-07-20
Well, I just re-formatted and re-installed ubuntu and low and behold GAIM is working again. WTF does aMSN do to this system??

---

### Post by Kimm on 2005-07-20
usualy when a program f00kes up, deleting the config files gets it happy again.
if you get that problem again, just type:

```

rm -rf ~/.gaim

```

and if you dont trust amsn, type:

```

rm -rf ~/.amsn

```

If you installed gaim from source, that will probably remove all your smileys, but if you didnt they shouldnt be located there. **However** this remove all accounts set up in gaim, so you have to add them again! :)

---

### Post by gammyhand on 2005-07-21
[QUOTE=Kimm]usualy when a program f00kes up, deleting the config files gets it happy again.
if you get that problem again, just type:

```

rm -rf ~/.gaim

```

and if you dont trust amsn, type:

```

rm -rf ~/.amsn

```

If you installed gaim from source, that will probably remove all your smileys, but if you didnt they shouldnt be located there. **However** this remove all accounts set up in gaim, so you have to add them again! :)[/QUOTE]
 Adding new accounts is much preferable to reinstalling. I will be spending most of today getting ubuntu back to where it was.

Not a big deal though. I am off this week and going on holiday next week so I am stuck in the house doing all my washing etc anyway.

Thanks for that great tip :)

---

### Post by mdsmedia on 2005-11-10
Rather than start a new thread I thought I'd try here.

In GAIM ICQ and AIM are treated as one and the same. The port shown is an AIM port.

I want to sign into ICQ but it throws back bad password or screenname. In relation to ICQ, what are the 4 fields in GAIM? I understand password. What's the difference between screenname and alias. Which is the UIN?

What servers work for logging in to ICQ?

In relation to MSN (where's the skull and crossbones when u need them) it seems to have a problem with being unable to authenticate .NET?

Once again, apart from password, what are the 4 fields asking for?

---

### Post by mdsmedia on 2005-11-10
[QUOTE=mdsmedia]Rather than start a new thread I thought I'd try here.

In GAIM ICQ and AIM are treated as one and the same. The port shown is an AIM port.

I want to sign into ICQ but it throws back bad password or screenname. In relation to ICQ, what are the 4 fields in GAIM? I understand password. What's the difference between screenname and alias. Which is the UIN?

What servers work for logging in to ICQ?

In relation to MSN (where's the skull and crossbones when u need them) it seems to have a problem with being unable to authenticate .NET?

Once again, apart from password, what are the 4 fields asking for?[/QUOTE]

OK, Got ICQ up :)

Just so people know..put UIN in screenname field, and nickname in alias field

Still having a problem with MSN authentication :(

---

