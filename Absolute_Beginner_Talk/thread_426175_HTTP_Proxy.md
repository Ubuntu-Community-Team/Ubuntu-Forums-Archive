---
title: "HTTP Proxy"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by omkarwagh on 2007-04-28
I am a student and we use http proxies on our campus. But I have direct connection to the internet at my home. How do I unconfigure the proxy settings?

Thanks in advance.

---

### Post by madmetal on 2007-04-28
> **omkarwagh said:**
> I am a student and we use http proxies on our campus. But I have direct connection to the internet at my home. How do I unconfigure the proxy settings?

Thanks in advance.

system >> preferences >> network proxy

---

### Post by omkarwagh on 2007-04-28
tried that before itself. doesnt work. Any other ideas.
firefox is working nice(obvi since im posting here) but synaptic still searches for the proxy.

---

### Post by madmetal on 2007-04-28
> **omkarwagh said:**
> tried that before itself. doesnt work. Any other ideas.
firefox is working nice(obvi since im posting here) but synaptic still searches for the proxy.

you should really contact the network administrator..
when people face this kinda problems i always suggest to contact the administrator..
if windows updates pass through proxy the same should work with ubuntu and other linux distros..

---

### Post by bapoumba on 2007-04-28
> **omkarwagh said:**
> firefox is working nice(obvi since im posting here) but synaptic still searches for the proxy.
apt-get, aptitude and synaptic will use** /etc/apt/apt.conf** file for proxy settings. Createthe file if you do not have any,  and look [here]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html") in the acquire group:
> HTTP URIs; http::Proxy is the default http proxy to use. It is in the standard form of [http://[](http://[)[user][:pass]@]host[:port]/. Per host proxies can also be specified by using the form http::Proxy::<host> with the special keyword DIRECT meaning to use no proxies

I have 2 files, one for home ("Direct"), one for work (proxy set up).

---

### Post by omkarwagh on 2007-04-29
thanks
i knew i had to change the apt.conf file but i didn know what to put in it. i tried saying acquire:http_proxy="" but that didn work
guess it shud be "direct"
thanks

---

### Post by bapoumba on 2007-04-29
> **omkarwagh said:**
> thanks
i knew i had to change the apt.conf file but i didn know what to put in it. i tried saying acquire:http_proxy="" but that didn work
guess it shud be "direct"
thanks

here is my apt.conf_maison (home, no proxy):
```
ACQUIRE {http::proxy "direct"};

```

apt.conf_univ (work, proxy):
```
ACQUIRE { 
http::proxy "http://myproxy.mydomain.fr:3128"
};

```
Replace myproxy, mydomain and the port with your actual ones.

I overwrite the etc/apt/apt.conf file with either one depending from where I am connected.
```
sudo cp apt.conf_xxx /etc/apt/apt.conf
```
Of course if you are in the proper directory. If not, give the complete path to your apt.conf_xxx.

---

