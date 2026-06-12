---
title: "sudo dpkg -i Fedora 16 equivalent?"
date: 2011-11-11
forum: Any Other OS
---

### Post by doppel.ganger on 2011-11-11
I want to install LibreOffice, so I downloaded the big archive, extracted it into my Downloads folder. I know how to do this on Ubuntu with sudo dpkg -i, but don't know the Fedora 16 equivalent of this command. When I select all the RPMs and hit enter, it opens an individual window for each one. Help!

-DG

---

### Post by nothingspecial on 2011-11-11
Moved to Other OS/Distro talk.

---

### Post by haqking on 2011-11-11
```
rpm -i 
```

and

```
man rpm
```

---

### Post by matt_symes on 2011-11-11
Hi

Use yum

[http://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/](http://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/)

Similar to apt-get.

Kind regards

---

### Post by haqking on 2011-11-11
> **matt_symes said:**
> Hi

Use yum

[http://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/](http://www.cyberciti.biz/faq/rhel-centos-fedora-linux-yum-command-howto/)

Similar to apt-get.

Kind regards

ahh yeah good point, i got sidetracked with the whole rpm thing ;-)

---

### Post by matt_symes on 2011-11-11
Hi

> **haqking said:**
> ahh yeah good point, i got sidetracked with the whole rpm thing ;-)

Actually, after re-reading the first post, your post is nearer to what the poster is asking for. :)

Now he has both commands. :popcorn:

Kind regards

---

### Post by doppel.ganger on 2011-11-11
Did I do this right?

```
[thomas@Thomas-Fedora ~]$ sudo rpm -i ~/Downloads/LibO_3.4.4rc2_Linux_x86_install-rpm_en-US/RPMS/*.rpm
[sudo] password for thomas: 
javaldx: Could not find a Java Runtime Environment! 
javaldx: Could not find a Java Runtime Environment! 
javaldx: Could not find a Java Runtime Environment! 
[thomas@Thomas-Fedora ~]$ 

```

---

### Post by matt_symes on 2011-11-11
Hi
[FONT=monospace]
[/FONT]> Could not find a Java Runtime Environment!It's looking for jre. Have you installed Java ? Have you set JAVA_HOME and updated your PATH  environmental variables ?

Kind regards

---

### Post by coffeecat on 2011-11-11
@doppel.ganger, isn't Libre Office in the Fedora repos, or is Fedora still using Open Office?

Whatever - you might find this guide useful.

[http://www.mjmwired.net/resources/mjm-fedora-f16.html](http://www.mjmwired.net/resources/mjm-fedora-f16.html)

---

### Post by shuttleworthwannabe on 2011-11-11
F16 vanilla (LiveCD version) I think does not come with LibreOffice--you have to download it from the repos in Add/Remove Apps I think.

---

