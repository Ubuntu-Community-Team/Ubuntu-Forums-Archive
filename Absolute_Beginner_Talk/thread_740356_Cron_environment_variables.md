---
title: "Cron environment variables"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by weezer316 on 2008-03-30
Just tore my last hair out!!!

Right, basically, i have a problem. I have a perl script i want cron to run. I have set up the cronjob, but cron refers to perl 5.8.8 looking for the modules. See below:

Can't locate Date/Formatter.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 6.
BEGIN failed--compilation aborted at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 6.


Now, perl5.10 modules are located in usr/local/lib/site_perl/perl5.10

How do i get cron environment to check here for the modules? Or failing that, how can i remove perl 5.10 as I didnt install it form synaptic and make uninstall wont work.

Beer in it for whoever gives me the right answer cause im going utterly mad with it.

---

### Post by collinp on 2008-03-30
Search for pearl 5.10 in Synaptic, it should be there regardless if you installed  it with it or not. Then click on the green square next to it and click "Uninstall". Then search for Pearl 5.8.8 and install what is needed for this job.

---

### Post by weezer316 on 2008-03-30
Well it aint there mate, only one is 5.8.8 core perl modules. Any other ideas?

---

