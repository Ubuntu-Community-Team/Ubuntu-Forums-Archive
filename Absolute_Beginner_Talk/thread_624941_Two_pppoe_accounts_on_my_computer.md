---
title: "Two pppoe accounts on my computer"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Jeremy_Wlk on 2007-11-27
Hi guys!

Could you help me making two pppoe accounts on one computer? I mean I have one account by now and it works wellt,.. but my friend would like to connect to the Web with his own login and password. In the help file I didn't find any solution.

Is it possible to make two connections in order to choose one of them which needed then?

---

### Post by Jeremy_Wlk on 2007-11-28
To take a closer look into into the problem, I've read manual on *"pppoeconf"* and 've found out a bit about configuration files. Actually I don't realize properly how they work but something has become more clear for me.

PPP configuration files that are related to creating and editing the accounts are listed below:

**/etc/ppp/options**
**/etc/ppp/chap-secrets** - here I added string like
```
"name_of_2nd_connection" * "password"
```
**/etc/ppp/pap-secrets** - here I added the same string as above in OUTBOUND section
**/etc/ppp/peers/dsl-provider**
(and some others probably...)

Only I've managed to achieve is to change current account's name and password however I've failed to add the second account...Could anyone help, please?

---

### Post by Jeremy_Wlk on 2007-11-29
Ok, not pretty good but at least it works now. What I've done - just 've created some files in **"/etc/ppp/peers/"** like *"dsl-connection-1"* and *"dsl-connection-2"* and 've edited string
```
"some_name1" * "some_password1"
```
within them. Accordingly I've changed *"pap-secret"* and *"chap-secret"* by editing some strings like following:
```
"some_name1" * "some_password1"
"some_name2" * "some_password2"
```

Now I wonder, how to tell one current connection from another, i.e. to determine what connection is currently active.

---

