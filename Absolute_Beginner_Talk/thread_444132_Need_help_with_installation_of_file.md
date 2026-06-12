---
title: "Need help with installation of file"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by zhenwei on 2007-05-15
Hi,

I trying to install an extension patch file in Ubuntu server for RT. The file name is RT-Extension-CommandByMail-0.05.tar.gz and i have uncompile it. I used the command to perl Makefile.PL to install, but i encounter the following error:

root@btpdevsup:/home/tmp/RT-Extension-CommandByMail-0.05# perl Makefile.PL
Cannot find the location of RT.pm that defines $RT::LocalPath in: inc /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /opt/rt3/lib /opt/lib/rt3 /opt/lib /usr/local/rt3/lib /usr/local/lib/rt3 /usr/local/lib /home/rt3/lib /home/lib/rt3 /home/lib /usr/rt3/lib /usr/lib/rt3 /usr/lib /sw/rt3/lib /sw/lib/rt3 /sw/lib
Path to your RT.pm:

I locate the file RT.pm in the directory /opt/oss/share/rt-3.4.5/lib. Even though i type it  in as show below

Path to your RT.pm: /opt/oss/share/rt-3.4.5/lib. I encounter the same error.

Thanks in advance for any help.

---

### Post by sankarv on 2007-05-30
try to set the same value in the variable respective to perl showing the path above and then try again. it may work.

---

