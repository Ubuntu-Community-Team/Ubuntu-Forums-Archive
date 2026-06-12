---
title: "Former Fedora/RedHat User Here"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ubuntology on 2007-10-26
I have about 10 years in with Red Hat and Fedora, but I've recently switched all of my machines to Gutsy. Almost everything works perfectly out of the box, but I still feel a bit lost.
In Fedora, if I wanted to restart Apache, I could run service httpd restart
What's the Ubuntu equivalent of that?

And if I wanted to set whether a service started at boot, the command was chkconfig httpd on/off

is there something like this in Ubuntu?

---

### Post by llamakc on 2007-10-26
For apache you can run from the command line:

sudo apache2ctl stop (or start) and a select few other options. Run `sudo apache2ctl` by itself to see the options.

Perhaps sysv-rc-conf would help with establishing what services run at boot? I believe there's also a graphical frontend called "bum".

HTH.

---

### Post by ubuntology on 2007-10-26
That's exactly what I needed.
Thanks!

---

