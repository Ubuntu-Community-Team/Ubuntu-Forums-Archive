---
title: "lots of broken things!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-27
I've been trying to create a server and have had a whole bunch of problems.

They started when trying to install Postfix - I made a post about it [here]("http://ubuntuforums.org/showthread.php?p=4416371#post4416371") but I thought I'd carry on with the rest of the tutorial whole I waited for somebody to help with that.

Then I had a problem with dependencies and I had to remove things via synaptic, which solved the dependencies problem.

I now get the error;

```

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

``` 

This appears seemingly randomly and only goes away if I reboot my machine.

I then tried to install apache, and when I needed to restart it then this happens:

```

root@simon-desktop:~# /etc/init.d/apache2 force-reload
/usr/sbin/apache2: error while loading shared libraries: /usr/lib/libldap_r.so.2: unexpected PLT reloc type 0x8d01900e
   ...fail!

```

This error happens when I try to start other processes too.

Can anybody shed some light please as I've only been following a tutorial and none of these things were supposed to happen!

---

### Post by JoshuaRL on 2008-02-28
Try this:
```

sudo apt-get install --reinstall libldap2
sudo apt-get install libldap-2.36-0 libldap2-dev
sudo apt-get update
sudo apt-get upgrade

```

Does that help?

In explaination I looked through Synaptic for a library matching that error and found those three, one of which was already installed on mine.

---

