---
title: "Apt-get problems"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by barnesdmd on 2007-08-01
Hi all, hoping for a little help from some kind person,

I've used ubuntu before as a desktop but am trying to put together a home server so the learning curve is greater now I've got no GUI to play with and the terminal is something I've kept away from until now.

I've got 7.04 server installed on a VIA mini-itx successfully and my NIC appears to be working (ie I can ping local and www addresses). However when I try and do any installs via apt-get I get errors saying no installation candidate no matter what the package is (e.g. openssh-server).

My theory was that this had something to do with the fact that I installed from CD but no longer have the CD drive attached, however I've edited the /etc/apt/sources.list file and commented out the CD as a source so I'm not sure whats wrong now. My understanding is that without the CD drive it will try and check on the web, it looks like it can't see the repositories properly but as I can ping them I'm not sure whats happening!

Can anyone help?

Regards,

Duncan

---

### Post by rich.bradshaw on 2007-08-01
Have you tried

sudo apt-get update

to get a list of what's avaliable?

---

### Post by tist on 2007-08-01
Dear Duncan

Have you already done ```
apt-get update
``` If that doesn't work, can you post your sources.list, error messages that apt-get update gives, and the output of ifconfig?

You might also want to check out aptitude if you're going to install packages from the CLI. Running it just like that gives you a GUI, but you can also run it from the CLI as replacement for apt-get.

Cheers
tist

---

### Post by barnesdmd on 2007-08-01
sorry! all fixed, running apt-get update solved it!

thanks for your prompt replies guys! very much appreciated!

---

