---
title: "how to run firefox as the mail reader of &quot;mail notification 2.0&quot;"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by ryu kun on 2006-09-10
How can I make my gmail address opened by Firefox as a "mail reader" for [Mail Notification]("http://www.nongnu.org/mailnotify/")?

---

### Post by Arevos on 2006-09-10
You have two options. You can install the gmail-notify package and use that, which is similar to the Mail Notification application but specialised for GMail.

Or, if you prefer to use the Mail Notification program, you can change the Mail reader (in Properties -> General) to "firefox http://mail.google.com". If you've checked the "remember me on this computer" checkbox on the GMail login page, then this will take you straight to your inbox. Otherwise, it'll take you to the login screen.

---

### Post by ryu kun on 2006-09-10
Thank you very much.

---

### Post by KSDZ on 2006-09-14
With Arevos' solution mailto: links stop to work,
so I wrote this solution:

```

#!/usr/bin/python

# gmailto: Workaround to use GMail as your default email-client

import sys
import os

if len(sys.argv) >= 2:
	email = sys.argv[1]
	if email[0:7] == "mailto:": email = email[7:]
        email = email.replace('?','&')
	email = email.replace('&subject=','&su=')
else: email = False

os.execlp("gnome-open","","https://mail.google.com/mail/" + (email and "?view=cm&fs=1&to=%s" %(email) or ""))

```

* Hit Alt+F2, type "gksudo gedit", hit enter
* Copy & Pase this code, Save as /usr/bin/gmailto
* Hit Alt+F2 again, type "gksudo chmod +x /usr/bin/gmailto", Hit enter
* Open System > Preferences > Preferred Applications
* Set Mail Reader to Custom
* Set the custom command to: "gmailto %s"

---

### Post by ryu kun on 2006-09-14
Thanks a lot KSDZ.

---

### Post by KSDZ on 2006-09-15
yw,


I updated the script to support extra arguments like subject=, body=
Edit/Delete Message

---

### Post by lemino on 2006-10-02
Did this really work? I only get the login-page, no matter what I try. :(

---

### Post by ryu kun on 2006-10-02
> **lemino said:**
> Did this really work? I only get the login-page, no matter what I try. :(

You should check "remember me on this computer" option in Gmail log in page and let Firefox save your Gmail password.

---

### Post by lemino on 2006-10-02
I already did both those things. Perhaps it has something to do with the fact that I have two gmail-accounts to handle att the same time?

---

### Post by ryu kun on 2006-10-02
Yes, this is the problem. Firefox and Gmail can only remember one Gmail account at the same time. So notification of new mails which come to your second account won't take you to your second Inbox.

---

### Post by Nick Rivers on 2006-12-28
Of course, the best solution (in my mind) is to enable POP3 access in Gmail and then use your favorite email client to access/send your Gmail.  I use Thunderbird to handle my Gmail.

---

