---
title: "How do I send e-mail from Ubuntu?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ksuchewie on 2007-08-28
Hello, I am a newbie to Ubuntu.  I've been using it for 3 days now, and I am mainly using it to run Nagios to monitor cisco switches.  I read that I can setup it up so that nagios can e-mail me if a switch stops reponding to a ping.  I looked at some documentation for setting up mailx but I am guessing I have done something wrong because mailx won't work.  I was wondering if anyone knows of a how-to for setting up some mail client in Ubuntu to send out e-mails.

Thank you so much.

---

### Post by mlentink on 2007-08-28
Ubuntu installs Evolution by default. 
Applications > Office > Evolution 
will start it up. Enter your account details and you're all set.

---

### Post by Mornedhel on 2007-08-28
Dude, I somehow don't think he's looking for Outlook. Sounds to me like sendmail/postfix stuff.

---

### Post by Fixman on 2007-08-28
Or, if you want to do some command-line, you can install the mailx package

sudo apt-get install mailx

then use the mail function to send mails

---

### Post by ksuchewie on 2007-08-28
I don't think I setup mailx correctly because it doesn't send mail out ???:confused:

---

### Post by ksuchewie on 2007-08-29
can someone walk me through mailx?

---

### Post by ksuchewie on 2007-08-29
I am now able to send e-mail using postfix ([https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)), but now how do I setup mailx to go through or use the settings that work for postfix?

---

