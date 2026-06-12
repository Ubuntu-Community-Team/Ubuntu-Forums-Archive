---
title: "Wireless adapter not working with Ubuntu"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Rexer on 2007-03-28
I kind of expected this. Today i switched from Windows XP to Ubuntu Linux. However my USB, Wireless Internet, Linksys Adapter is not seen by Ubuntu Linux. What, if anything, can i install. I am completely new to any form of linux, so im sorry if there is something that is in plain view about this that i have not seen. Any help at all is appreciated.

---

### Post by su_penguin on 2007-03-28
Google: ndiswrapper

---

### Post by crispy_420 on 2007-03-28
How about telling us what adaptor you have. There may be a native linux driver you could try before using a Windows driver (ndiswrapper). If you know the chipset that may help too.

---

### Post by halitech on 2007-03-28
open a terminal and type

```
lsusb
```

and paste it here

---

### Post by NeoGreen on 2007-03-28
What version of ubuntu are you using?

---

### Post by surfjdh on 2007-03-28
easy solution, you have the driver cd right?, good, if not find the apprt. drivers for your model linksys adapter, they are .inf, apps>assc.>terminal>type  ndiswrapper -i FileNameHere.inf, if you have multiple .inf files...install em all. then get KwifiManager and check it out...it worked!!, in dapper a graphic gui is present to accomplish this called windows wireles drivers under systen>admin>w.w.d..   have fun

---

### Post by Rexer on 2007-03-28
im trying to use a wusb54g v4. i downloaded ndiswrapper and got that untar'd and ungzipped, those are probably the wrong terms, im following the instructions step by step now. however, when i did ./make uninstall it gave me an error: bash: ./make: no such file or directory.
I am using 6.10 ubuntu.

Also, when i installed linux, it told me to make a username so i called it admin. now its asking me to run something as root and i dont know the password. i tried to make an account with root as the name but it said it was taken. is there a default password?




*update* I did sudo ndiswrapper -i inffile.inf and it had a problem at line 135. i did this with two inf files and the same line didnt work. whats going on?

---

### Post by Rexer on 2007-03-29
sorry but, bump.

I did sudo ndiswrapper -i inffile.inf and it had a problem at line 135. i did this with two inf files and the same line didnt work. whats going on?

---

### Post by Durito on 2007-03-29
[INDENT]What does the error message say?
[/INDENT]

---

### Post by surfjdh on 2007-03-30
2 things, post the error msg, and two as far as passwords are concerned...wait why did you call your account admin?, thats sort of weird, why not your name, or a game tag, ftw?, n-e ways, your "root" account's password is the same (in 6.06d.d.) as the account you created.  i.e.: name=admin password=34fellati ;then name=root password=34fellati...

---

