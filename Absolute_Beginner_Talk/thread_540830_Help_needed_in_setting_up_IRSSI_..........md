---
title: "Help needed in setting up IRSSI ........."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by @vijay@ on 2007-09-02
im using xchat till now ; now im looking into terminal programs  :lolflag:

so i installed irssi

Im behind a proxy server in localhost:10014

i added the proxy server by 
------------------------------------------------------
/SET use_proxy ON
/SET proxy_address localhost
/SET proxy_port 10014

/SET -clear proxy_password
/EVAL SET proxy_string CONNECT %s:%d HTTP/1.0\n\n
-----------------------------------------------------------------
seeing here [http://www.irssi.org/documentation/startup#c10](http://www.irssi.org/documentation/startup#c10)

Now when i tried to connect to irc.ubuntu.com by
-----------------
/connect irc.ubuntu.com
-------------------------

i get this error:mad:
--------------------------------------                                                                           
11:31 -!- Irssi: Looking up irc.ubuntu.com
11:31 -!- Irssi: Connecting to irc.ubuntu.com [127.0.0.1] port 6667
11:31 -!- Irssi: Connection to irc.ubuntu.com established
11:31 -!- HTTP/1.0 200 Connection established
11:31 !irc.ubuntu.com *** Looking up your hostname...
11:31 !irc.ubuntu.com *** Checking ident
11:31 !irc.ubuntu.com *** Your forward and reverse DNS don't match
11:31 !irc.ubuntu.com *** No identd (auth) response
11:31 -!- ERROR Closing Link: 127.0.0.1 (Connection Timed Out)
11:31 -!- Irssi: Connection lost to irc.ubuntu.com
----------------------------------------------------------

Whats the prob ???? xchat was able to connect perfectly without probs:confused::confused:

---

### Post by PriceChild on 2007-09-02
*moves and bumps*

---

### Post by @vijay@ on 2007-09-02
sorry to post it there, i was confuse where to post the thread ; and thanx for moving

---

### Post by @vijay@ on 2007-09-02
here are screenshots displaying the setting of xchat and irssi 

xchat settings
[http://img408.imageshack.us/img408/3720/screenshot1wy2.png](http://img408.imageshack.us/img408/3720/screenshot1wy2.png)

irssi settings
[http://img251.imageshack.us/img251/606/screenshot2iq2.png](http://img251.imageshack.us/img251/606/screenshot2iq2.png)

xchat works but not irssi , why???

---

### Post by @vijay@ on 2007-09-03
anyone?????????:(:(

---

### Post by ladynikon on 2007-09-08
you may wanna try posting config.  So that people can see what you have going on.

LadyNikon:guitar:

---

