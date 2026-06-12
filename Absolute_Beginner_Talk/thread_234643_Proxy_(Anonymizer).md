---
title: "Proxy (Anonymizer)"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Contrid on 2006-08-11
Hey Everyone,

I'm proud to say that I've managed to get many things done in my first day of using Ubuntu...and the experience is great.

In Windows I used to have an application called Anonymizer, which I guess is similar to Hide IP Platinum. The reason why I used these applications is because they allowed me to use anonymous proxy servers in order to handle session cookies better. (preventing me from being continuously kicked out of sites with session cookies.)

Does anyone know where I can find something similar for Linux (Ubuntu 6.06). Unfortunately I dumped my Windows partition, so I can't use those apps through Windows anymore.

All help is greatly appreciated. :)

All the best,
Contrid.

---

### Post by CarpKing on 2006-08-12
Have you looked into Tor? 
tor.eff.org

---

### Post by Contrid on 2006-08-12
I tried that, but I couldn't get it to work.

> sudo apt-get install tor

...just says that the package cannot be found, so I have no idea what to do. Maybe you could pass me some helpful advice. It will be appreciated. :)

---

### Post by j-strap2 on 2006-08-12
Follow the instructions here:

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

Don't use the default ubuntu package of Tor - last time I looked, it was and old, deprecated version.

---

### Post by pvdg on 2006-08-12
> **Contrid said:**
> I tried that, but I couldn't get it to work.



...just says that the package cannot be found, so I have no idea what to do. Maybe you could pass me some helpful advice. It will be appreciated. :)

Tor is available in the Universe repository. You must add Universe before you can download and install tor using Synaptic or apt-get install.
If you need help on how to add the Universe repository, take a look at
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories).
I hope this helps. Sorry if I'm telling you something you already know.

EDIT: I hadn't read j-strap2's post before; I think you should follow his advice. Howerver, you should add the Universe repo anyway.

---

### Post by Contrid on 2006-08-13
> **pvdg said:**
> Tor is available in the Universe repository. You must add Universe before you can download and install tor using Synaptic or apt-get install.
If you need help on how to add the Universe repository, take a look at
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories).
I hope this helps. Sorry if I'm telling you something you already know.

EDIT: I hadn't read j-strap2's post before; I think you should follow his advice. Howerver, you should add the Universe repo anyway.

No...you're not telling me anything that I already know. :)
Ok...it seems like I managed to isntall it thanks to you guys. I knew how to add respiratories, but I just don't really understand how everything fits together.

Now...
How do I configure tor? Where do I find it on my system. It is there, but I just don't know where it is, and how to configure it. Currently it isn't doing what I expect it to. I guess it's not active or something. :-k

---

### Post by Contrid on 2006-08-13
I'm still confused, but I've made some progress. My problem is that I can't edit the 'config' file. I don't have the permissions to do that. Please see the screenshot below :

[IMG]http://www.tribulant.com/IMG/permission.png[/IMG]

Other than that...I've installed Privoxy, and the extensions are in my browser.

---

### Post by j-strap2 on 2006-08-13
It looks like the Universe version is 1.0.16 whereas the latest stable release is 1.1.23. You should definitely use the latest version.

Do something like 'sudo gedit /etc/privoxy/config' to get the required permissions for editing.

---

### Post by druvoid on 2006-08-17
I got current versions of Privoxy and Tor installed, and got Proxy Switcher working in Firefox, but when I turn on Privoxy, I get a page with a big 503 and this error message at the top:

Your request for [http://ubuntuforums.org/showthread.php?t=10825](http://ubuntuforums.org/showthread.php?t=10825) could not be fulfilled, because the connection to ubuntuforums.org (127.0.0.1) could not be established.

In Firefox --> Tools --> SwitchProxy --> Manage Proxies --> Privoxy --> Edit, I have the Manual Proxy Configuration button checked.  The HTTP Proxy is set to localhost and the port to 8118.  The SOCKS v5 button is marked.  Below that there is a box labeled "Automatic proxy configuration URL."  The button next to the label is blank and the box under it is empty. 

What do I need to change?  I am running Breezy.

(If I knew how to capture the  Proxy Info panel that I just described, I would just paste it in here.)

---

### Post by The Seeker on 2006-08-17
If you're using Firefox check out [FoxyProxy](https://addons.mozilla.org/firefox/2464/).

---

### Post by j-strap2 on 2006-08-17
druvoid, have you configured privoxy correctly by editing its configuration file (as detailed in Step 2 here: [http://tor.eff.org/docs/tor-doc-unix.html.en](http://tor.eff.org/docs/tor-doc-unix.html.en))?

---

### Post by druvoid on 2006-08-20
Thanks, **j-strap2** and **TheSeeker**!  I removed everything and started over using FoxyProxy and making sure that I meticulously followed the steps on **j-strap2's** link.  Everything appears to be working wonderfully now.  :)

---

### Post by druvoid on 2006-08-20
Eh, I celebrated too soon.  Turns out I was using an outdated version of tor, so I updated to the 1.1.23, the current version.  Then tor couldn't open the logfile and wouldn't start, so I chowned it to my username.  Now I get this:

druvoid@MyMachine:~$ sudo /etc/init.d/tor start
Password:
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Aug 20 10:03:45.373 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Aug 20 10:03:45.440 [notice] Initialized libevent version 1.1a using method epoll. Good.
Aug 20 10:03:45.506 [warn] /var/lib/tor is not owned by this user (debian-tor, 114) but by druvoid (1000). Perhaps you are running Tor as the wrong user?
Aug 20 10:03:45.506 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Aug 20 10:03:45.507 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

So then I tried to start it without sudo, and got the following:

druvoid@MyMachine:~$ /etc/init.d/tor start
Cannot access /var/run/tor directory, are you root?

Do I need to completely remove tor and privoxy and start over?

---

### Post by j-strap2 on 2006-08-21
The service should start itself automatically, but to do it manually you should do it as root like you did initially.

The /var/lib/tor should be owned by debian-tor - you can:

```
sudo chown debian-tor /var/lib/tor
```

and all should be hunky-dory.

---

