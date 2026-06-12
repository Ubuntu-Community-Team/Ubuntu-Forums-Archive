---
title: "http/https proxy problem with checkgmail"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kkellner on 2007-01-16
hey,
I've had ubuntu for about 6 months now, and nearly everything works as it should...
but there's one thing I can't get to work no matter how hard I work at it.  I am trying to get checkgmail to work behind my school's proxy.  I realize I have to set the HTTPS_PROXY environmental variable to do this, but it still doesn't work.
is this the correct command?

export HTTPS_PROXY="http://proxy.server.edu/:port"

or am I typing something wrong?  should I use the port I normally use for firefox, etc, or do I need to specify a different port?  

proxies are one of the most annoying things to set in ubuntu...

---

### Post by kkellner on 2007-01-16
that should be : port, not :p

---

### Post by kkellner on 2007-01-16
if I type this:

export HTTPS_PROXY="http://proxy.server.edu:(normal http proxy port)"
I get a 401 unauthorized error and the login window continually pops up.

if I type

export HTTPS_PROXY="https://proxy.server.edu:(normal http proxy port)"
I get this error : 

Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Unknown tag 'html' on line 9 char 8 at /usr/bin/checkgmail line 1189.

I looked at this line in the file but I don't know enough about the code to find the problem.

Other ports give a variety of "connection refused" messages.

---

### Post by T-MAN3000 on 2008-01-20
I'm guessing google changed something in the authentication process, this happened a few months ago too. Didn't bother to check if there's a bugreport already, but I'll do that right away.

---

### Post by bapoumba on 2008-01-20
My own university proxy blocks a lot of ports (including the ones gmail uses). So I have to use the webmail. I cannot use checkgmail from there.

---

