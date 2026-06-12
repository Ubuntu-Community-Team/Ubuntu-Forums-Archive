---
title: "how to use mail command?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-10-16
i am trying to use the mail command to post mail from my terminal but it is not working. what softwares should i need to install to use mail from my terminal?
thanks in advance.

---

### Post by skymt on 2006-10-16
I believe you need to use a mail server. [Postfix](https://help.ubuntu.com/community/Postfix) is probably the easiest to set up. Be sure to configure it to route mail through your ISP's outgoing server. Otherwise certain ISPs (like mine, Verizon) will block your mail as spam because it doesn't come from a known mail server.

Or, just install and use the msmtp command (sudo apt-get install msmtp), which is designed for systems without their own mail servers. Post back if you have trouble setting it up.

---

### Post by TheWizzard on 2006-10-16
install also mailx

---

