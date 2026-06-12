---
title: "rootkit scan results"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-11-25
hey was hoping someone can give me a and understanding these results cause im a little confused

from rkhunter-

 Performing file properties checks

      /usr/bin/ldd                                             [ Warning ]
      /usr/sbin/xinetd                                         [ Warning ]

 Performing trojan specific checks

     Checking for enabled xinetd services                     [ Warning ]

 Performing system configuration file checks

     Checking if SSH root access is allowed                   [ Warning ]

 Performing filesystem checks

     Checking for hidden files and directories                [ Warning ]


from chkrootkit-

     Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/java-6-sun-1.6.0.03/.systemPrefs
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/XML/Parser/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/XML/DOM/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/VmPerl/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/HConfig/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/VMware/VmdbPerl/.exists
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/MIME/Base64/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/Authen/PAM/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/auto/URI/.packlist
/usr/lib/vmware/perl5/site_perl/5.005/i386-linux/VMware/.exists
/usr/lib/firefox/.autoreg
/usr/lib/j2se/1.4/jre/.systemPrefs
/usr/lib/j2se/1.4/jre/.systemPrefs/.system.lock
/usr/lib/j2se/1.4/jre/.systemPrefs/.systemRootModFile
/lib/modules/2.6.22-14-rt/volatile/.mounted
/usr/lib/j2se/1.4/jre/.systemPrefs

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[4272])


anyone got any ideas what any of this means?

thanks for your help

alex

---

### Post by darkeale on 2007-11-25
ok looks like these things are connected to vmware, so there safe enough

right?

---

### Post by darkeale on 2007-11-26
anyone?

---

