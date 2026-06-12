---
title: "Start Bumblebee at boot"
date: 2012-04-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Scripting22 on 2012-04-28
Hello,

Since a few hours I got Bumblebee on Precise Pangolin working like a charm. It doubles the battery lifetime of my laptop! So far everything great, but I have to start de bumblebee daemon manually every time I boot Kubuntu.

My question is. How start the bumblebee daemon at boot? Simply adding the command

```
bumblebee --daemon
``` 

is not the right way to do it I've read somewhere on the Net. So, does anyone here have a clue how I could do this?

Cheers,

---

### Post by Lekensteyn on 2012-04-30
You can add the PPA as described in [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)
It'll install a daemon that automatically start at boot time.

Otherwise, if you want to install from source, copy the scripts/upstart/bumblebeed.conf file to /etc/init/

Also, bumblebeed has a manual page. When installing from the PPA, run `man bumblebeed`. The authorative documentation is the wiki, see also [http://bumblebee-project.org](http://bumblebee-project.org).

---

