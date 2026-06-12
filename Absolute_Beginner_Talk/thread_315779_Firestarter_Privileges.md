---
title: "Firestarter: Privileges"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by ityro on 2006-12-09
Hi All,

I am trying to get Firestarter to start at system startup (and Auto Logon) and I am getting close.

I went to System>Preferences>Sessions and selected Startup Programs and added Firestarter to the programs to be run at startup.

At startup I now get the following message "Insufficient Privileges, You must have Root User privileges to use Firestarter". I am the first and only user on this system. I should not add myself to the Root Group, right?

Can someone please tell me what to do next?

THANKS!

---

### Post by meng on 2006-12-09
One might ask why you need to have firestarter at startup. Firestarter just alters your firewall settings (iptables). It doesn't need to be running for your firewall to be in effect.

---

### Post by compwiz18 on 2006-12-09
First off: You probably already know this, but firestarter is active even if the GUI is not display (ie, you don't start it) edit: oops, someone posted while i was typing

Secondly: You don't even need a firewall with Ubuntu unless you are running servers

Thirdly: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon) is what you are looking for

---

### Post by ityro on 2006-12-09
> **meng said:**
> One might ask why you need to have firestarter at startup. Firestarter just alters your firewall settings (iptables). It doesn't need to be running for your firewall to be in effect.

Thank You!  I did not know that. Thought it had to be running.

Thanks again.

---

### Post by DaveBorealis on 2006-12-09
> **meng said:**
> Firestarter just alters your firewall settings (iptables). It doesn't need to be running for your firewall to be in effect.

If you don't mind me butting in with a question....  When I run Firestarter, it places a blue button on my top menu that says 'Firewall running' when I hover the cursor over it.  Yet if I do a 'ps axx', I don't see iptables listed.  What exactly is being run?

Thanks,
Dave

---

### Post by ityro on 2006-12-09
> **compwiz18 said:**
> First off: You probably already know this, but firestarter is active even if the GUI is not display (ie, you don't start it) edit: oops, someone posted while i was typing

Secondly: You don't even need a firewall with Ubuntu unless you are running servers

Thirdly: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon) is what you are looking for

Hello,

No, I did not know. Guess I have my answer, and thanks for the reference.

Thanks Again.

---

