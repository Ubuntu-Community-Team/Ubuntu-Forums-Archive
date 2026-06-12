---
title: "How to configure Synaptic through shell?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-02-14
In my feisty i wish to change synaptic's settings to use a proxy server. However whenever i go to properties and click apply or ok it just freezes. This happens even if i don't change anything.

My question is can i configure all the settings of synaptic through the shell or through a config file?

---

### Post by rai4shu2 on 2007-02-14
I think all of Synaptic's settings are in /root/.synaptic/synaptic.conf

However, you really shouldn't be having some trouble with freezes. Type this from a shell:

gksudo synaptic

See if the shell is reporting some activity during one of these freezes.

---

### Post by DerHesse on 2007-02-14
go for /etc/apt/apt.conf
There you can specify a proxy.

```
...
Acquire::http::Proxy "http://user:pass@proxy_ip:proxy_port";
```

---

### Post by ajmorris on 2007-02-14
> **rai4shu2 said:**
> I think all of Synaptic's settings are in /root/.synaptic/synaptic.conf

However, you really shouldn't be having some trouble with freezes. Type this from a shell:

gksudo synaptic

See if the shell is reporting some activity during one of these freezes.

No activity is reported in the shell during the freeze, however, when i start up synaptic i get this :

(synaptic:5833): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/synaptic/glade/system-upgrade': No such file or directory

(synaptic:5833): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(synaptic:5833): libglade-WARNING **: Couldn't find image file: system-upgrade

---

### Post by ajmorris on 2007-02-14
> **DerHesse said:**
> go for /etc/apt/apt.conf
There you can specify a proxy.

```
...
Acquire::http::Proxy "http://user:pass@proxy_ip:proxy_port";
```

This file is empty for me.


Also i have tried setting a global proxy in proxy settings, however this did not impact any of my applications such as firefox or synaptic.

---

### Post by ajmorris on 2007-02-14
> **rai4shu2 said:**
> I think all of Synaptic's settings are in /root/.synaptic/synaptic.conf

However, you really shouldn't be having some trouble with freezes. Type this from a shell:

gksudo synaptic

See if the shell is reporting some activity during one of these freezes.

I have configured the proxy settings through this and it works fine. Thanks heaps

:)

---

### Post by DerHesse on 2007-02-15
> **ajmorris said:**
> This file is empty for me.

....

Of course it's empty. You have to add this line.

---

### Post by ajmorris on 2007-02-15
> **DerHesse said:**
> Of course it's empty. You have to add this line.

lol, sorry ok. But i configured it in the actual synaptic config and it works to connect to the proxy. However i get a "size mismatch" error when trying to download.

---

### Post by DerHesse on 2007-02-16
have a look here:
[http://ubuntuforums.org/showthread.php?t=151120](http://ubuntuforums.org/showthread.php?t=151120)

---

