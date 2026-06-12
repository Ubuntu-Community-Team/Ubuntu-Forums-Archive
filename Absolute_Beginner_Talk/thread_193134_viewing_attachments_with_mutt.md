---
title: "viewing attachments with mutt"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by jsmidt on 2006-06-09
Somebody sent me a pdf as an attachment.  I know in mutt if I push "v" I see the attachment but how do I view it in a pdf viewer like xpdf?  Thanks.

---

### Post by Burke on 2006-06-10
Well, I've only used Mutt a few times, but I'm pretty sure you can save files to a more convenient location in the attachments menu. Just throw the pdf on your desktop and launch it with xpdf. There's probably a more elegant way, but I can assure you, I don't know it ;)

---

### Post by ape on 2006-06-10
So, you'll notice that when you press 'v' you get not only a list of the attachments, but also what attachment type they are listed as.  Mutt uses the /etc/mailcap file to determine what program to use to display the selected attachment (which you select by hitting <Enter> on the particular item after highlighting it).

Entries from my /etc/mailcap file concerning pdf files look like this:

```
application/pdf; /usr/bin/xpdf '%s'; test=test "$DISPLAY" != ""; description=Portable Document Format; nametemplate=%s.pdf
application/x-pdf; /usr/bin/xpdf '%s'; test=test "$DISPLAY" != ""; description=Portable Document Format; nametemplate=%s.pdf
```

You can also use the 'auto_view' directive in your .muttrc file to configure certain types of attachments to be automatically opened upon opening the email.  This works well for opening html files directly within text mode mutt.

[http://www.mutt.org]("http://www.mutt.org") is a great place to find out all sorts of mutt config details.

Good luck!

--Ape--

---

