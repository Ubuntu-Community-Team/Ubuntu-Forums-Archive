---
title: "Pidgin problem MSN account (aMSN works fine)"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by sergiodlc on 2007-10-25
Hi:

I can't login into my MSN account with Pidgin. It happens mainly at work. It works perfectly in some other places. They don't have a blocking policy here since MSN Messenger and aMSN work fine.

I really want to use Pidgin as my only IM application. It works OK with Google Talk accounts.

By the way, the same thing happens with Yahoo accounts. Pidgin doesn't work but Yahoo Messenger works OK.

What should I do? :confused:

Thanks in advance,

Sergio

---

### Post by Foxphyre on 2007-10-25
what are the settings under the advanced tab for msn within pidgin
server should be: messenger.hotmail.com
port: 1863
http method server: gateway.messenger.hotmail.com
and tell it to use whatever proxy settings your web browser is using

---

### Post by sergiodlc on 2007-10-25
I have checked the option to enable http method and this solved my problem. Yahoo accounts are still unusable.

---

### Post by gabizu on 2007-10-27
I have (near)same problem! i have  a http proxy(works fine in firefox) and if i try to connect to my yahoo(gtalk) accounts it doesn't work! if i put port 80 instead of 5222 is trying to connect and gives this error:Read Error! if a let the 5222 port :"proxy forbids port 5222 tunneling"

---

### Post by russianbandit on 2007-10-27
I alsoo have a problem with pidgin where my msn account can never connect.
Some times it connects at work, but never at home. And I have no firewalls at home.

---

### Post by ~cyrus~ on 2007-10-27
I can confirm that MSN and Yahoo don't initially connect on launching Pidgin.

For Yahoo, I have to ping scs.msg.yahoo.com only after which it connects to Yahoo messenger

For MSN, I try to do the same thing by trying to ping messenger.hotmail.com but am unable to ping this address. I switch to HTTP method and try to ping gateway.messenger.hotmail.com and cannot ping that address either.

The only other solution for me is to use aMSN that works, and the new Yahoo mail page that incorporates Yahoo messenger as well.

---

### Post by ~cyrus~ on 2007-10-29
If it's of any help to anyone else, my connectivity issues were sorted out as indicated in [this thread]("http://ubuntuforums.org/showthread.php?t=586395").

---

