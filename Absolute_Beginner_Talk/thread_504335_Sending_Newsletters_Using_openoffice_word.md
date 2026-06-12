---
title: "Sending Newsletters Using openoffice word"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by rwizibuntu on 2007-07-19
Hello,
I am trying to setup a newsletter fo my business but when i try sending it through the openoffice mail merge wizard i get the message below

<class 'smtplib.SMTPSenderRefused'>: (530, '5.7.0 Must issue a STARTTLS command first h7sm7869785nfh', u'xxxxxxxxxxx@gmail.com'), traceback follows
  File "/usr/lib/openoffice/program/mailmerge.py", line 183, in sendMailMessage
    self.server.sendmail(sender, recipients, msg.as_string())

what is the best way to configure the system?
Is there any other good mail merge program i can use?

---

### Post by ihristov on 2007-07-19
Not familiar with mail merge, but the particular error "Must issue a STARTTLS" means that the SMTP host that you are using requires STARTTLS (a security encryption protocol).

You have to find the settings in OO where you have setup the parameters for the SMTP server and specify that it should use STARTTLS or possibly SMPTS could work. Maybe this is not a setting in OO, but a global for the system. Take a look at the OO documentation about the sending e-mail configuration.

---

