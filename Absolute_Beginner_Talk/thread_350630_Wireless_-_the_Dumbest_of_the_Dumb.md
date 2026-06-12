---
title: "Wireless - the Dumbest of the Dumb"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by fdbjr on 2007-01-31
I just installed 6.10, and would like to migrate fully. I am sick of Microsoft. But Windows XP does automatically id and configure wireless networks in the vicinity, of which there are a large number nearby, including my own secured cable-modem LAN and Google Wi-Fi (I live in Mountain View, Ca.

      How do I get Ubuntu simply to id wireless networks in the vicinity? And how do I configure the network, which Windows did more or less automatically? Thanks in advance.

---

### Post by dbbolton on 2007-01-31
wifi radar

---

### Post by fdbjr on 2007-01-31
What's that? And where is it?

---

### Post by dbbolton on 2007-01-31
go to applications > add/remove

it's a wireless network browser that allows you to save profiles of various networks.

---

### Post by kolinab on 2007-01-31
```

sudo aptitude install wifi-radar

```

Then look for 'wifi-radar- in your applications menu under internet. Wifi radar works well for me to detect wireless networks in the area and connect to them. I think you'll find once you open it up that you will be able to do what you need. Others here I believe use network-manager, and I think it may be good as well, but I couldn't get it working as easily or as quickly as wifi-radar so I stuck with the latter. 

Good luck with it!

---

### Post by jelkimantis on 2007-01-31
> **fdbjr said:**
> What's that? And where is it?

Uhm. Wow, ok, maybe you should really listen to [www.linuxreality.com](www.linuxreality.com)

You'll find wifi radar in synaptic.  LinuxReality Episode like 19 and 20 are an ubuntu install on the air.  He discusses synaptic and how to install it.

jsl

---

### Post by pegazuz on 2007-01-31
> **kolinab said:**
> ```

sudo aptitude install wifi-radar

```

Then look for 'wifi-radar- in your applications menu under internet. Wifi radar works well for me to detect wireless networks in the area and connect to them. I think you'll find once you open it up that you will be able to do what you need. Others here I believe use network-manager, and I think it may be good as well, but I couldn't get it working as easily or as quickly as wifi-radar so I stuck with the latter. 

Good luck with it!

I couldn't find it with a search in either Synaptic or Adept Package managers although I could find it with a Google search. Now I have to figure out how to install it without using these package programs which make it so simple.

---

### Post by punx45 on 2007-01-31
have you configured the wireless adapter yet?  most are not ready to work after an install.

---

### Post by raul_ on 2007-01-31
You need to activate the extra repositories, in order to have more software available:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

PS: I would recommend that guide i linked as a BIBLE

---

### Post by pegazuz on 2007-02-02
> **kolinab said:**
> ```

sudo aptitude install wifi-radar

```

Then look for 'wifi-radar- in your applications menu under internet. Wifi radar works well for me to detect wireless networks in the area and connect to them. I think you'll find once you open it up that you will be able to do what you need. Others here I believe use network-manager, and I think it may be good as well, but I couldn't get it working as easily or as quickly as wifi-radar so I stuck with the latter. 

Good luck with it!

I have KnetworkManager and it worked fine yesterday but then today it wouldn't connect.  I finally got it to connect by disabling the wireless, removing my wireless network and restarting everything.  Now I wonder if it will work next time i boot up.  I would like to try wifi radar.  Do I need to remove KnetworkManager first or just disable it and then try start wifi radar?

---

