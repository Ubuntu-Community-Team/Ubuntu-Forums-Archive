---
title: "Proxy servers"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-16
I use my laptop most of the time at school, however to access the internet there is a proxy server there. How can I configure ubuntu so that I can connect using the proxy server so that I can use package managers etc. Details are:

proxy 2
port: 8080
username: computing\alexjeffreys
password: ********

So how will I be able to do this,
Thanks in advanve for any help

Ajeffreys :)

---

### Post by ajmorris on 2007-06-17
in a lot of applications you can specify them manually, but there is a global ubuntu one for applications that can't be specified manually.

Go to System >> Preferences >> Network Proxy

then on the dialog box that comes up enter the proxy details.

---

### Post by argie on 2007-06-17
In 6.06, for apt to work from the command line, I had to edit /etc/apt/apt.conf:

```

ACQUIRE {
http::proxy "http://user:pass@10.1.2.3:80/"
}
```

Also, in Synaptic:
Settings » Preferences » Network

---

### Post by k1001001 on 2007-06-18
Will this also get around proxies against general use? I'm on tour with a drum corps and we stay at a lot of middle schools and high schools, where sites like Myspace and Facebook are often blocked. It's getting pretty obnoxious. Any way around this?

---

### Post by jvc26 on 2007-06-18
It depends very much on how their network is set up. A few years back when at school we had two proxies - one for teachers, one for pupils, once we found that out we changed our proxy settings and that worked fine. However they also may well have some form of filtering software or even a server which does the same job, filtering out content from such sites blocking them. If thats the case circumventing it won't be easy, even if it is possible.
Il

---

### Post by k1001001 on 2007-06-18
The filter seems to be a word-based filter in addition to black-listed websites. When I search the word 'proxy' or even 'Myspace' on any search engine, it triggers the block, meaning it probably has a point-based word filter. However, the word 'Facebook' doesn't trigger this block, which suggests to me that Facebook.com is probably just blacklisted. I talked to one of the teachers earlier and according to him, even they don't have a way around it. There is an option to log in to an override account on the block screen though. I guess there's not really much going around the block without logging into an approved override account.

By the way, it's an 8e6 R3000 filter. The block IP is 10.193.16.41, port 81. Hope this might help.

---

