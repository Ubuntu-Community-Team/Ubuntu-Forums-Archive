---
title: "How to set Google account in Pidgin 2.0.0 (previous Gaim)"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-06
Hi,
I have installed Pidgin 2.0.0 and I just don't know how to configure Google account. In previous version of Pidgin (Gaim) there was Jabber protocol, but in new one there is no Jabber protocol available.

Available protocols in Pidgin 2.0.0 are:
- AIM,
- Gadu-Gadu,
- GroupWise,
- ICQ,
- IRC,
- MSN,
- QQ,
- SILC,
- SIMPLE,
- Sametime,
- XMPP and
- Yahoo.

Has someone configure Pidgin to use Google?
Thanks,
Abcuser

---

### Post by felicity on 2007-05-06
You want XMPP! :) 

I'm not sure why they didn't use XMPP/Jabber..

---

### Post by abcuser on 2007-05-06
Hi,
thanks for help.

Now I have done the following:
Screen name: my e-mail adress without @gmail.com
Server: googlemail.com (default is jabber.org and is not working)
Password: Google mail password

Thanks,
Abcuser

---

### Post by abcuser on 2007-05-07
Hi,
one more question. At home my notebook works fine with Pidgin to MSN, Yahoo and Google, but at my work non of them work. There is probably somekind of proxy or firewall blocking. For proxy I have set: "Use Global Proxy Settings" (default settings).

Error messages:
MSN: myaccount disconected: Connection error from Notification server: Unable to connect
Google: myaccount/Home disconnected: Couldn't connect to host
Yahoo: myaccount disconnected: Unable to connect.

Any idea how to make this programs work?
Thanks,
Abcuser

---

### Post by felicity on 2007-05-07
Have you been able to connect to those services at your work previously?

Does your work have any information available about a firewall they may be using?

---

### Post by kerry_s on 2007-05-07
Here are my settings.

---

### Post by MoxJet on 2007-05-07
This might give you some ideas:
[http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

---

### Post by abcuser on 2007-05-08
kerry_s, MoxJet, both suggestions are for old version of Gaim not for Pidgin.

---

### Post by abcuser on 2007-05-08
> **felicity said:**
> Have you been able to connect to those services at your work previously?

Does your work have any information available about a firewall they may be using?
Previously I have used MSN Messenger on Windows XP. I have been using Google Talk from Google web page. I haven't used Yahoo from my job, didn't need this IM. 

As I see some ports have been disabled on company firewall. Is there any settings I could use IM to use any other standard port, just like [http://www.meebo.com](http://www.meebo.com) uses port 80 (default web port), to avoid firewall blockade?

Thanks,
Abcuser

---

### Post by kerry_s on 2007-05-08
> **abcuser said:**
> kerry_s, MoxJet, both suggestions are for old version of Gaim not for Pidgin.

I thought only the name was changed, not the program?

---

### Post by kerry_s on 2007-05-08
Okay i got pidgin, it's uses the XMPP.

---

### Post by MoxJet on 2007-05-10
Whoa Gmail with Pidgin is sweet, I get new mail notifications :D

---

### Post by HydroDiOxide on 2007-05-16
I get an error when I want to connect to googletalk saying I need tsl/ssl support. How do I enable this?

---

### Post by lsutiger on 2007-06-13
A little off topic, but will get this thread bumped...
When I use Gaim and use my gtalk account, it lists all of my contacts in my address book, not just my 'friends'....is there a way to prevent this?

---

### Post by ncappel1 on 2007-06-13
I just want to add that I installed Pidgin today (2.0.0 Beta7) and it has jabber support.

---

### Post by icaughtfire818 on 2007-06-21
Has anyone had problems with getting Pidgin to connect?

I have...I've tried changing the port, and nothing has worked yet.

Any ideas?

---

### Post by phr0ze on 2007-06-21
@ OP, Your work could have started blocking all of that traffic. There is not much you can do which would be 'safe'. There are ways around this but you risk trouble at your company because they disabled this for a reason.

@ icaughtfire818, You should start a new thread for a new issue. There are lots of people using Gtalk with PIDGIN, even the OP got it working. Start a new thread and give us some details about error messages, etc.

---

### Post by joseph_chapman on 2007-06-28
If you are getting 'not authorized' after trying any of the many configuration combinations referenced in this and other posts, it may be something as simple as you are pressing the 'REGISTER' button and not the 'SAVE' button.

[http://developer.pidgin.im/ticket/1341](http://developer.pidgin.im/ticket/1341)

This simple mistake wasted several of my hours and had I known this was a 'convenience' feature for Pidgin/GAIM that allowed you to register/create a new account on the target server when you didn't have one I would never had clicked it.

So, if you already have an account on Google Talk or some other jabber/XMPP server, DO NOT CLICK REGISTER, click SAVE and then tick the 'enable' check box and you are done.

Whew!

---

