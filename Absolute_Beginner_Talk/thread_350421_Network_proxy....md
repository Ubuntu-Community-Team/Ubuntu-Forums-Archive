---
title: "Network proxy..."
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-01-31
Hello,

I installed ubuntu a couple days ago (and im just lovin it). Now I want to get some things to go trough a proxy (evolution/thunderbird and gftp). Now I'm having some trouble with that. But I just found the network proxy option. (under system >> preferences >> network proxy.

Is it true that if I set that EVERYTHING will go trough that proxy? So that my email program (evolution or thunderbird) and gftp as well as firefox will all go trough that proxy?

---

### Post by freemanda3 on 2007-01-31
this option you found is for system wide gnome settings which means that any program that has been designed to work in the gnome enviroment will use this proxy setting. the prime example of this is firefox. if you don't specifically go in and set the browser up with the the proxy you desire then it wil try and do a direct connection. another example is the dictionary lookup in  applications-accessories-dictionary. it will go directly off the system wide settings that you setup under the proxy configuration.................lata

---

### Post by bapoumba on 2007-02-01
Hi,
package managers (synaptic, apt-get, aptitude) won' t use global GNOME proxy settings either.
They use the **/etc/apt/apt.conf** file.

---

### Post by airtonix on 2007-07-04
actually, i have a proxy on my home gateway, squid.

its shaping access to certain sites.....and also making sure it doesnt shape access to others.

thingis .... the clients that connect to it....well i have defined the proxy in gnome-network-settings...

guess what?

apt-get honours it.

so does wget.

but now for some reason(whislt using openbox now) it wont. what gives....

edit: **/etc/apt/apt.conf **is empty too.

doing an apt-get update throws errors citing being unable to connect to the proxy..

---

### Post by bapoumba on 2007-07-04
You can create the apt.conf file:
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")

Here is mine as an example:
```
$ cat apt.conf 
ACQUIRE { 
http:: proxy "http://proxy.mydomain:myport"

```

Note: I added an extra <space> between "::" and "p", otherwise a :p smiley shows up.

---

### Post by gusanto on 2008-06-18
Hi there,
I don't know why now in my desktop there is "Network Proxy" shortcut.  What is that and is it safe to just remove it from the desktop?
Many thanks.

---

