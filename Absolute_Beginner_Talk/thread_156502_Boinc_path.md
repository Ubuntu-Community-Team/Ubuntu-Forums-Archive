---
title: "Boinc path?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-07
Hi,

I installed boinc using apt-get and everything worked fine. It still works fine :)
But I have a gdesklet I want to use with boinc, and I need to know where it is installed. Pff.. cant find it?

Anybody knows the path of boinc, when you use apt-get to install it?

Thanks

---

### Post by Darkriser on 2006-04-07
maybe there's an easier way but try find that package in Synaptic, right-click with mouse and select Properties. Then go to "Files Installed" tab (i'm writing from head, so the name may vary a little bit) and there you should see all files (with full path) installed.

---

### Post by aktiwers on 2006-04-07
Thanks for your quick reply.

But look, how can I see where its installed? this is what it tells me:

```
/.
/usr
/usr/bin
/usr/bin/boinc_cmd
/usr/bin/boinc_client
/usr/share
/usr/share/doc
/usr/share/doc/boinc-client
/usr/share/doc/boinc-client/README.Debian
/usr/share/doc/boinc-client/copyright
/usr/share/doc/boinc-client/buildinfo.gz
/usr/share/doc/boinc-client/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/boinc_cmd.1.gz
/usr/share/man/man1/boinc_client.1.gz
/etc
/etc/default
/etc/default/boinc-client
/etc/init.d
/etc/init.d/boinc-client
/usr/bin/boinc
/usr/share/man/man1/boinc.1.gz


```
Is /usr/share/doc/boinc-client/ then the folder Im looking for?

---

### Post by Darkriser on 2006-04-07
well, the binary itself is installed in /usr/bin/boinc_client, /usr/bin/boinc_cmd and /usr/bin/boinc

however, gdesklets will probably need to access some log file or project directory, where progress can be read from. try reading something about gdesklets configuration for boinc.

the /etc/default/boinc-client stands for configuration files. the others seem to be documentation.

---

### Post by aktiwers on 2006-04-07
Okey thanks.

All the gdesklet ask for is BOinc Path:

Thats it, but I still dont seam to be able to find it. I tryed the 2 paths above, but without luck.

---

### Post by Darkriser on 2006-04-07
did you try /usr/bin/boinc also?

hm....if this doesn't work,either try google or maybe anyone else could help.

---

### Post by aktiwers on 2006-04-07
yes that one didnt work either.
I have been googling this for an hour, with no luck. 

Im pretty new to Ubuntu and linux, and I still dont get it with those installments. Apps and other installed stuff, never seem to be only one place? Why is that?

If anyone can help me find the path to boinc, that is needed for my boinc gdesklet to work, I will be more than happy :)

Thanks for all your help Darkriser! :)

---

### Post by dcstar on 2006-04-07
I find kboincspy a more useful monitoring utility.

---

### Post by mrfrost on 2006-04-11
Read /usr/share/doc/boinc-client/README.Debian, your question is answered there. The default BOINC data directory that is used by the boinc-client package is /var/lib/boinc-client/

 - Frank

---

### Post by Louis Cypher on 2007-12-20
> **mrfrost said:**
> Read /usr/share/doc/boinc-client/README.Debian, your question is answered there. The default BOINC data directory that is used by the boinc-client package is /var/lib/boinc-client/

 - Frank

Thx, that helped me to setup KboincSpy.

---

