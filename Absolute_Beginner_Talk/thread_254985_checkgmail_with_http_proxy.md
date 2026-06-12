---
title: "checkgmail with http proxy"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by kkellner on 2006-09-10
i have been using ubuntu for a few days and it has been wonderful except for when it interacts with the proxy network i have to use at college.
i have set up wget to use the proxy as well as firefox and amarok (even installed kcontrol just so amarok would find covers for me)
However, I cannot figure out how to set up checkgmail for a proxy.  the website for checkgmail says to set the environmental variable HTTP_PROXY but I'm not sure what that means.  thanks for your help!

---

### Post by larry wales on 2007-05-29
Damn, I wish someone would reply to this msg...  it'd be a useful thing to know.  I can't understand why the folks at checkgmail.sourceforge didn't include this option in the preferences panel.

-larry

---

### Post by inhumanbean on 2008-02-11
just do this:

export HTTPS_PROXY="http://proxyserveraddress:port"

eg..say your proxy server is "proxy.abc.com"

you would do
export HTTPS_PROXY="http://proxy.abc.com:8080"

(assuming 8080 is the port)

then just run checkgmail from the same window...
you can also set up a bash script and run it that way.

cheers.

---

