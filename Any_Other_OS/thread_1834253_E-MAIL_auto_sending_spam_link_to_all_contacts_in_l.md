---
title: "E-MAIL auto sending spam link to all contacts in list"
date: 2011-08-27
forum: Any Other OS
---

### Post by DougieFresh4U on 2011-08-27
Ok, so my Mother (in her 70s) uses WinXP.
Her email account is sending a spam (link to some Canadian ****** drug sight) to ALL her contacts on her list. It's been quite embarrassing as she runs a business website and contacts all over America are receiving this.
I have 'google' this and it seems to be a problem all over with yahoo and AOL and other email clients being affected. But no solution has been mentioned.
I would really be glad if some one could shed some light on this and how I might 'fix'.
I have gotten the email twice to all 3 of my email addresses. If I opened this link, will it affect/infect my computer as well running Ubuntu and Debian?
Thanks to any one who might be able to assist with this.

---

### Post by SeijiSensei on 2011-08-27
First, if she hasn't done so, she must disconnect her computer from the Internet.  Otherwise it's highly likely it will continue to relay spam.

Next you need to see if you can remove the malware with the range of tools available for Windows like [malwarebytes]("http://www.malwarebytes.org/").  If you're lucky, you'll clean out the crap.  If not you'll need to reinstall Windows from scratch.

---

### Post by Oxwivi on 2011-08-27
If, after you've disconnected her, the spams are still being sent, the her email ID and password has been compromised. Change them immediately along side recovery questions.

Of course you should change the password in case of local malware as well, just in case.

And no, Windows malware won't affect Linux machines. Similar to the case of trying to install Windows programs in Linux.

---

### Post by Iowan on 2011-08-27
Moved to Other OS/Distro Talk

---

### Post by lisati on 2011-08-27
Another thing to check is the possibility that her email address is being spoofed, faked or forged: it's easy enough to do if you know how.

---

### Post by SeijiSensei on 2011-08-29
> **lisati said:**
> Another thing to check is the possibility that her email address is being spoofed, faked or forged: it's easy enough to do if you know how.

Since you have a couple of examples of the spam, you can tell right away if they're being spoofed.  Look at the complete headers of the message and see how it was routed.  (Usually the simplest method is to view the message "source.")  If you know how your mother is connected to the Internet, say over a cable or DSL line, look at the IP address of the host that originated the message.  Does it appear to come from a residential IP of that provider?  

The other possibility as was mentioned is that the spoofing is happening entirely independently of your mother.  This is called a "[joe-job]("http://en.wikipedia.org/wiki/Joe_job")," where messages are sent with the From address forged with a legitimate sender, in your case, your mother's email address.  We had this problem just the other day at a client's site; one of the staff members was joe-jobbed, and the organization's mail server was deluged with non-delivery notices as a result.

I've also seen spam being sent from apparently legitimate accounts at places like Hotmail and AOL.  These are cases where the person's credentials have been stolen.  If your mother uses a webmail service, and the messages you received look like they came legitimately from that service, she needs to start changing her passwords across the Internet.

The fact that the messages are being sent to people in her Contacts list suggests that these last two alternatives are less likely than her machine being infected with malware.

---

