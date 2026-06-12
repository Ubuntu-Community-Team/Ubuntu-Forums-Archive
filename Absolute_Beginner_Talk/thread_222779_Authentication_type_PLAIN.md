---
title: "Authentication type PLAIN"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2006-07-25
Why does evolution show this error msg when I try to reply to email with an attachment that I have added.  "ISP does not support requested authentication type PLAIN".  What am I doing wrong or what do I have to correct?

---

### Post by wombat20 on 2006-07-25
> **kwjaxon said:**
> "ISP does not support requested authentication type PLAIN".

It may be that your ISP insists upon better authentication that just plain.  The easiest way to sort this out is to go (within Evolution) 

Edit -> Preferences.

Select your default Mail Account and press the Edit button.  A dialog box pops up.

Under the Sending Email tab, press the Check for Supported types button.  That should ensure you use only authentication the ISP likes.

If it's only happening with attachments then I recommend contacting the ISP.  Have you tried this with any other email clients?

---

### Post by kwjaxon on 2006-07-25
Sorry to be slow.  That took care of the problem.  Thanks for everything.

---

