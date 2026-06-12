---
title: "Issue with Ubuntu samba shares in OS X (asking for user/pass when I don't want it to)"
date: 2012-03-26
forum: Apple Hardware Users
---

### Post by Stingray88 on 2012-03-26
First I'd like to note that I previously had this issue, and then after moving to a new desktop and a fresh copy of Ubuntu, the issues were gone. Now just last night Ubuntu completely went belly up from a software update, and I was left with nothing. So I reinstalled a fresh copy of Ubuntu 10.04, and my issue has come back.

So I have Samba setup using [the basic Samba GUI for Ubuntu.]("http://www.unixmen.com/how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui/") I have every share set to visible, writable, and to allow access to everyone. Then I have the authentication mode under security set to "share".

The problem is when I hit cmd+k on my Macbook to bring up my list of shares that I want to connect to, and then click connect on the shares... it prompts me for this:

[IMG]http://i.imgur.com/BH6UK.png[/IMG]

I don't want to see this window. Ever. Previously, I had it set using these same settings in Ubuntu to never pop up... but somehow that's not what's happening now. Every time I want to connect to a share, this window pops up... no registered user works, no matter if I add that for authentication under Ubuntu or not. The guest account works... however there is no box to check to use the guest every time. Thus no matter what I do... this box always pops up when I want to connect to a share.

So anyone got any ideas on how I can get rid of this?

---

### Post by chrik on 2012-03-27
Try creating a new samba username/password following these instructions:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu)

The next time you connect use this username/password and check the "Remember this password in my keychain" box.

---

