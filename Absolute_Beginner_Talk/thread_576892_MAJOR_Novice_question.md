---
title: "MAJOR Novice question?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by pdumbelton on 2007-10-15
Thanks for taking the time to read & hopefully help me a newbie...

I have never used Linux before. There, I said it,,, I feel better already.

I have just installed ubuntu 6.06 Lamp server & am trying to get webmin to work to allow me to configure apache, mysql & so on.
I have followed the articles I have found regarding install of webmin but when I run the install it errors. 

dpkg Dependency problems prevent configuratio of webmin
webmin depends on libnet-ssleasy-perl; however package libnet-ssleasy-perl is not installed.

I get the same statement for the following files. libauthem-pam-perl, libio-pty-perl, libmd5-perl.

Do I need to download & install Perl5 first? my ubuntu install document didn't mention needing to do this...
Should I be using a different version of ubuntu?... I do require it to have apache & mysql but should I install differently not chosing the Lamp server option right @ the beginning of the install.
Having lived in the microsoft world for to long command line work is foreign to me... I don't mind learning but if there is a simpler way for me I'd rather go that route..?

Your feed back for a poor ubuntu novice would be greatly appreciated.

---

### Post by [S|G] on 2007-10-15
You only need to install the missing packages. You can use the package manager (synaptic) to do it or open a terminal and type this:
```
$sudo apt-get install libauthen-pam-perl libio-pty-perl libmd5-perl libnet-ssleasy-perl
```

---

