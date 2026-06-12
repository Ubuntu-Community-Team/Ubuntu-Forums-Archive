---
title: "Mail::Spamassassin::Plugin::DCC Error"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2006-12-19
Hi guys,

I am trying to set-up and configure a postfix mail server on Ubuntu Edgy (AMD64) from aprrox 3 different guides that help with the configuration of clamav, spamassassin, postgrey, virtual mail, squirrelmail, squid, pyzor, DCC, razor and MAilscanner.

I am currently working off the MailScanner guide ([http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu))

I have managed to get to the point where I have to test SpamAssassin using the command - su postfix -p -c 'spamassassin -x -D -C /opt/MailScanner/etc/spam.assassin.prefs.conf --lint'

When it runs it shows 2 errors in the terminal - see below

[2429] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/Spamassassin/Plugin/DCC.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 78) line 1.
[2429] warn: plugin: failed to create instance of plugin Mail::Spamassassin::Plugin::DCC: Can't locate object method "new" via package "Mail::Spamassassin::Plugin::DCC" at (eval 79) line 1.
[2429] dbg: plugin: loading Mail::Spamassassin::Plugin::Razor2 from @INC
[2429] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/Spamassassin/Plugin/Razor2.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 80) line 1.
[2429] warn: plugin: failed to create instance of plugin Mail::Spamassassin::Plugin::Razor2: Can't locate object method "new" via package "Mail::Spamassassin::Plugin::Razor2" at (eval 81) line 1.

Can anyone direct me as how to try and resolve these issues?

Thanks in advance

---

