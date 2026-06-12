---
title: "SCIM: how have SCIM sitting in the panel after Ubuntui starts up?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by flameproof on 2007-04-24
I installed SCIM, but now I have to start it manually via terminal. How can I make the keyboard swap sit in the panel after startup?

---

### Post by flameproof on 2007-04-24
To add some info:

No scim seems working when I startup. To get SCIM into the panel I do in Terminal:  SCIM -d

That locks SCIM to the panel, but it's gone after restart.

---

### Post by shirilover on 2007-04-25
try the following in a terminal:
Add SCIM to startup for X11
```

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup 

```

---

### Post by mskadu on 2007-04-28
And for the non-techies who have Ubuntu 7.04 installed, 
[LIST=1]
[*]System > Preferences > Sessions
[*]"Startup Programs" tab > Click New > and enter the following values
Name = SCIM
Command = /usr/bin/scim -f x11 --no-socket -d
[*]Click Ok and Done buttons.
[*]Logoff and Logon[/LIST]Hope this helps..

> **shirilover said:**
> try the following in a terminal:
Add SCIM to startup for X11
```

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup 

```

---

