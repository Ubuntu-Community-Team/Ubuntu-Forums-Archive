---
title: "apt-proxy not work with reposity dapper"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by rikymn on 2006-05-30
i config one server debian and one server ubuntu with apt-proxy (!!good program!!)

this is apt-proxy-v2.conf in any apt-proxy server (ubuntu and debian)

[ubuntu]
;; Ubuntu archive
backends = [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu)

[ubuntu-security]
;; Ubuntu security updates
backends = [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

[ubuntu-src]
backends = [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

[ubuntu-universe]
backends = [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

this is one client breezy (this work it)
deb [http://10.0.119.91:9999/ubuntu/](http://10.0.119.91:9999/ubuntu/) breezy main restricted
deb [http://10.0.119.91:9999/ubuntu-security](http://10.0.119.91:9999/ubuntu-security) breezy-updates main restricted
deb [http://10.0.119.91:9999/ubuntu](http://10.0.119.91:9999/ubuntu) breezy universe

this is one client dapper (this not work it)
deb [http://10.0.119.91:9999/ubuntu/](http://10.0.119.91:9999/ubuntu/) dapper main restricted
deb [http://10.0.119.91:9999/ubuntu-security](http://10.0.119.91:9999/ubuntu-security) dapper-security main restricted
deb [http://10.0.119.91:9999/ubuntu](http://10.0.119.91:9999/ubuntu) dapper universe

the apt-get update stop with this prompt

root@ubuntu:/etc# apt-get update
0% [In attesa degli header]

in apt-proxy server the /var/log/apt-log is
i apt-proxy
2006/05/29 11:05 CEST [Channel,3,10.0.119.39] [debug] Adding ttp: backend dynamicaly
2006/05/29 11:05 CEST [Channel,3,10.0.119.39] [debug] Created new BackendServer: [http://ttp:](http://ttp:)
2006/05/29 11:05 CEST [Channel,3,10.0.119.39] Unhandled error in Deferred:
2006/05/29 11:05 CEST [Channel,3,10.0.119.39] Traceback (most recent call last):
          File "/usr/lib/python2.3/site-packages/twisted/protocols/http.py", line 557, in requestReceiv
ed
            self.process()
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 1375, in process
            self.fetch()
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 1454, in fetch
            (dummyFetcher, 0, running,), None)
          File "/usr/lib/python2.3/site-packages/twisted/internet/defer.py", line 205, in addCallbacks
            self._runCallbacks()
        --- <exception caught here> ---
          File "/usr/lib/python2.3/site-packages/twisted/internet/defer.py", line 338, in _runCallbacks
            self.result = callback(self.result, *args, **kw)
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 1422, in fetch_real
            fetcher = dummyFetcher.apEndTransfer(fetcher_class)
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 463, in apEndTransfer
            fetcher = fetcher_class(req)
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 317, in __init__
            self.activate(request)
          File "/usr/lib/python2.3/site-packages/apt_proxy/apt_proxy.py", line 573, in activate
            ClientFactory(self), request.backend.timeout)
          File "/usr/lib/python2.3/site-packages/twisted/internet/default.py", line 289, in connectTCP
            c = tcp.Connector(host, port, factory, timeout, bindAddress, self)
          File "/usr/lib/python2.3/site-packages/twisted/internet/tcp.py", line 708, in __init__
            raise error.ServiceNameUnknownError(string=str(e))
        twisted.internet.error.ServiceNameUnknownError: Service name given as port is unknown: service/
proto not found.


bye bye :KS

---

### Post by [woodstock] on 2006-06-06
I can confirm that bug. apt-proxy.log looks quite the same here, buts it's /usr/lib/python2.**4** for me. I installed Dapper on a blank computer and I encountered this apt-proxy problem during setting up the proxy-server.

Has anybody some hints how to solve that problem? I'm no expert but the problem seems to be buried deeply in a python module called "twisted".

---

### Post by [woodstock] on 2006-06-06
I found the solution in a german forum.
Solution:
Edit **apt.conf**. It looks like this after a fresh dapper installation:
> APT::Authentication::TrustCDROM "true"; 
Acquire::http::Proxy "false";

Delete the last line an save **apt.conf**. It should ***then*** look like this:
> APT::Authentication::TrustCDROM "true"; 

Restart apt-proxy:
> sudo /etc/init.d/apt-proxy restart

apt, synaptic,... should work now with apt-proxy if the rest is properly set up.

I don't know why that second line causes the error. I am too lazy to investigate.

---

### Post by sjpwong on 2006-06-07
[QUOTE='[woodstock]']apt, synaptic,... should work now with apt-proxy if the rest is properly set up.[/QUOTE]

Thank-you, thank-you, thank-you.  Wish I looked here a little earlier though!

[QUOTE='[woodstock]']
I don't know why that second line causes the error. I am too lazy to investigate.[/QUOTE]

Perhaps, another day?!

---

### Post by rikymn on 2006-06-12
[QUOTE=sjpwong]Thank-you, thank-you, thank-you.  Wish I looked here a little earlier though!



Perhaps, another day?![/QUOTE]

i modify the ubuntu "client" apt-conf now is:

Acquire::http::Proxy "false";

i restart my debian apt-proxy

but in my ubuntu client apt-update is freezy in this state

root@ubuntu:/etc/apt# apt-get update
0% [In attesa degli header]

---

### Post by rikymn on 2006-06-12
work it:-& 
i replace incorrect line
the /etc/apt/apt.conf file must be:
APT::Authentication::TrustCDROM "true";
:p 

bye


> **rikymn]i modify the ubuntu "client" apt-conf now is:

Acquire::http::Proxy "false" said:**
> 

[QUOTE=sjpwong]Thank-you, thank-you, thank-you.  Wish I looked here a little earlier though!



Perhaps, another day?![/QUOTE]

---

### Post by rikymn on 2007-10-19
In NEW UBUNTU gutsy  i have same problem 
the apt conf is differente (there is /etc/apt/apt.conf.d/)
and i can not remove the line in /etc/apt/apt.conf
There is new information to use apt-proxy??
There is new tool to cache deb package?? 
GRAZIE

---

