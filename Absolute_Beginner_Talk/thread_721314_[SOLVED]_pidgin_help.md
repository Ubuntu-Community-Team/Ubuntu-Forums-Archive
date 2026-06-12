---
title: "[SOLVED] pidgin help"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by medic8ted on 2008-03-11
I'm trying to set up pidgin, but can't send any messages.  I know usernames are correct and I'm logged in to Yahoo! but buddies don't get messages.  I am receiving messages, but they are not getting the ones I send.

---

### Post by Het Irv on 2008-03-11
Do you have a firewall set up that is blocking outgoing packets?

---

### Post by medic8ted on 2008-03-11
Firestarter installed, policy tab says Outbound permissive by default.  Router should allow all oubound as well.  Is there a command I can use to check outbound?

---

### Post by Oldsoldier2003 on 2008-03-11
> **medic8ted said:**
> Firestarter installed, policy tab says Outbound permissive by default.  Router should allow all oubound as well.  Is there a command I can use to check outbound?
```

netstat -p | grep 'pidgin'
``` will tell you if you have established any connections

---

### Post by medic8ted on 2008-03-11
```
netstat -p | grep 'pidgin'
```
tcp        0      0 computername.local:54157    cs15.msg.dcn.yahoo:mmcc ESTABLISHED6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     76668    6894/pidgin         /tmp/orbit-matt/linc-1aee-0-2d5dc4eca990d
unix  3      [ ]         STREAM     CONNECTED     76663    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43023    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43014    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43006    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43003    6894/pidgin


Looks connected to me

---

### Post by Oldsoldier2003 on 2008-03-11
> **medic8ted said:**
> ```
netstat -p | grep 'pidgin'
```
tcp        0      0 computername.local:54157    cs15.msg.dcn.yahoo:mmcc ESTABLISHED6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     76668    6894/pidgin         /tmp/orbit-matt/linc-1aee-0-2d5dc4eca990d
unix  3      [ ]         STREAM     CONNECTED     76663    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43023    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43014    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43006    6894/pidgin         
unix  3      [ ]         STREAM     CONNECTED     43003    6894/pidgin


Looks connected to me

yep you're connected as far as pidgin is concerned. check and see the status of pidgin... ie do you have more than one instance open, is it zombied?   also try disabling your accounts then re-enabling them once you are sure you only have one instance of pidgin.

---

### Post by medic8ted on 2008-03-11
> yep you're connected as far as pidgin is concerned. check and see the status of pidgin... ie do you have more than one instance open, is it zombied? also try disabling your accounts then re-enabling them once you are sure you only have one instance of pidgin.
```
 top 
``` 
shows no zombies, already tried disabling account and deleting account too.  Re-enabled it and still no luck.  Also tried removing pidgin and re-compiling also to no avail.  Kopete doesn't work either.

---

### Post by Het Irv on 2008-03-11
Are you having problems with just one person or everyone?  The problem may not be on your end.

---

### Post by medic8ted on 2008-03-11
everyone, they all say "offline" in the buddy list window, even though I know they're online

---

### Post by medic8ted on 2008-03-16
Nevermind...the problem was theirs...computer illiterate people trying to explain things resulting in mass confusion for all.

---

