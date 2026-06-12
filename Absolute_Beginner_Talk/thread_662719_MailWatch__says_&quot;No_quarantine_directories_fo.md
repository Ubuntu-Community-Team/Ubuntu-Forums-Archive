---
title: "MailWatch  says &quot;No quarantine directories found&quot;"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by fychan on 2008-01-09
Ok, treat me as a complete Linux n00b - you won't miss by far that way :D

I've got Ubuntu (Gutsy) up & running as a home server - using Postfix to handle incoming mail, Dovecot to provide an IMAP interface and a combination of MailScanner & spamassassin to try & filter out spam (no anti-virus installed yet, as each client machine is running it's own already it's not a /very/ high priority).

I installed MailWatch the other day, in the hope that it would allow me to re-identify HAM and SPAM that the other programs had mis-diagnosed and it's all up and running nicely - with the last 50 messages showing on the homepage, and the black/white lists running just fine - but when I click on the "Quarantine" link, it lists the top of the tap & options fine then just says:

"No quarantine directories found" 

I've used Google a lot trying to solve this issue - and a lot of people seem to get function errors & all sorts in connection with this message.  I'm getting no errors (not even in the Apache logs), just a friendly (and uninformative!) message.  I've checked all the permissions (as per all the posts I've found) and they're all good.  I've gone through the [Wiki ]("http://mailwatch.sourceforge.net/doku.php?id=mailwatch:faq#i_can_t_get_mailwatch_to_see_my_quarantined_e-mail") and made all those changes, I've also run the "fix_quarantine_permissions" script in the MailWatch install directory to no avail.

Has anyone got any ideas at all?  I'm at my wits end now... :confused:

Cheers

---

### Post by fychan on 2008-01-14
Any help on this really would be appreciated...

Phil

---

