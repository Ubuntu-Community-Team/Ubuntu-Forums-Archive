---
title: "wget and Tor node network"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by logicus on 2007-10-15
hey you guys

I'm trying to get wget, which is a fantastically powerful command, to use tor.
I've edited the .bashrc and the .profile to include 

http_proxy=http://127.0.0.1:8118/
HTTP_PROXY=$http_proxy
export http_proxy HTTP_PROXY

Also I've seen to that privoxy is up and running.

However it does not seem to have any effect.

Whenever i use wget to download the whatismyip.com address, it still shows the same old ip-address.

I'm using feisty fawn.

Help, please.

:(



Sincerely

Peter

---

### Post by julian67 on 2007-10-16
[how-to-use-wget-through-proxy]("http://blog.taragana.com/index.php/archive/how-to-use-wget-through-proxy/")

> For Linux/Unix:
export http_proxy="http://proxy.example.com:8080"

Replace proxy.example.com with your actual proxy server.
Replace 8080 with your actual proxy server port.

You can similarly use ftp_proxy to proxy ftp requests. An example on Linux would be:
export ftp_proxy="http://proxy.example.com:8080"

Then you should specify the following option in wget command line to turn the proxy behavior on:
&#8211;proxy=on

Alternatively you can use the following to turn it off:
&#8211;proxy=off

So the command I used to export was:

```
export http_proxy="http://127.0.0.1:8118"
```

and the wget command was:

```
wget -proxy=on www.whatismyip.com
```

which verified my ip address to be anonymous/identifiable as a tor exit node

---

