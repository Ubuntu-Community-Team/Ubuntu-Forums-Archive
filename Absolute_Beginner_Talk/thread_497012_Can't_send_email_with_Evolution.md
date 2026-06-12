---
title: "Can't send email with Evolution"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by steamshooter on 2007-07-09
I'm having a problem with Evolution. I can receive email. But, it won't send. I'm 99% confident that my settings are correct. This is what I get when I try to send a test:

"Error while performing operation.

DATA command failed: Requested action not taken: mailbox unavailable"

I have searched my fingers to the bone and can't seem to fix it.
I have cleared the /etc/hosts file.

BTW: Getting my sound to work was no easy task for me but I did it!!! :guitar:

TIA
Brad

---

### Post by p_quarles on 2007-07-09
Do you mind posting the settings for your outgoing mail server? I might be able to help if I can see what you're working with.

That said, I know that one frequent cause of this kind of error is that many ISPs block port 25 from accessing SMTP servers other than their own. So, if you're using Google's SMTP server, your ISP might be the problem. Is that possible?

---

### Post by steamshooter on 2007-07-09
Thanks for the quick reply.

I'm using smtp.charter.net
server requires athentication: I've tried this checked and not checked. It doesn't seem to matter.
No encryption for the security setting
Athentication: Login
My username
and Remember password is checked.

I ran across topics about port 25 being blocked but, I haven't been able to get in there far enough to know if that's the case. I'm not afraid of the terminal, I just don't know how to use it effeciently yet.

---

### Post by p_quarles on 2007-07-09
That sounds like it should work (but it's not, I know).

Hmm. I didn't use Evolution for long before switching to Thunderbird (something to consider), but I think the options were pretty similar. I just checked out Charter's home page, and it says they do require a secure connection on SMTP. Usually, though, there are several options for the kind of secure connection. Try clicking on SSL (the most used one), and make sure that the outgoing port changes to 465. It should do this automatically, but if not, change it. 

If that doesn't work, I don't know. Sorry.

For what it's worth, I never had that problem with Evolution, but I did find it to be kind of buggy on my machine.

---

### Post by steamshooter on 2007-07-09
It still won't work. Maybe I should start looking at alternatives? Thanks again for trying. I'll put it on the back burner and let it simmer awhile. 

Brad

---

### Post by geoffatmk on 2008-01-28
Brad

Don't know if you ever got this sorted but it happens to me from time to time and the onhly wayt to clear it is to take the email(s) out of the outbox (ususally it is just the top one that is causing the problem) and rebuild it to resend it.  This usually clears it for me.  Can not give you any idea why it happens.

Geoff

---

