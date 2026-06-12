---
title: "Setting smtp to use port 26"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by NetDoc on 2007-09-29
My ISP blocks port 25 and so I have my cpanel server to use port 26. It's easy enough to set in Outlook, but I am trying to break away from Micro$oft. Any direction on how to do this would be wonderful.

---

### Post by macogw on 2007-09-29
What mail client are you using?  In Thunderbird, it's in the smtp settings.

edit: or are you talking about where do you set it in the mail server?

---

### Post by NetDoc on 2007-10-01
I am using "Evolution Mail" which is a part of the ubuntu install package. Should I switch to Thunderbird to do this?

---

### Post by mlentink on 2007-10-01
Perhaps you could tell us a bit more of what precisely you want to achieve. You say your ISP blocks port 25, which they do for a reason, and no, problem whatsoever if you relay your outgoing mail over their servers.

---

### Post by NetDoc on 2007-10-01
> **mlentink said:**
> Perhaps you could tell us a bit more of what precisely you want to achieve. You say your ISP blocks port 25, which they do for a reason, and no, problem whatsoever if you relay your outgoing mail over their servers.I want to use my mail servers and not theirs: mail.scubaboard.com. Is there a way to make smtp use port 26???

---

### Post by mlentink on 2007-10-04
> **NetDoc said:**
> I want to use my mail servers and not theirs: mail.scubaboard.com. Is there a way to make smtp use port 26???

Theoretically, yes. Depends on the MTA used, But the point is, your mail.scubaboard.com is set up to listen on port 25, as that is the standard for smtp. So if you send out stuff on port 26, that mailserver will never receive it. The firewall on the machine the MTA is running on might very well even block traffic on that port, as it belongs to an unofficial protocol.
Perhaps, if that mailserver is private, you could set up a tunnel to it?

---

### Post by ronald.higgins on 2007-10-04
I'm not saying it's not possible to tell your MTA to send out on port 26 (depends on the MTA) but the receiving MX Server / Next Hop is not going to be listening on port 26 for SMTP, unless maybe you have another mailserver outside of your ISP's network that will listen on Port 26 and then relay via port 25 ....

---

### Post by duggers on 2007-10-08
My ISP listens on port 2525. Is there a way of setting the SMTP port to other than 25 in Evo????? Otherwise I am going to have move back to Thunderbird...

---

### Post by duggers on 2007-10-08
Found the answer. you specify the port as part of the server name in the Sending Mail prefs:

my.mailserver.com:port

---

