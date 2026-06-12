---
title: "Not so much Ubuntu, more a Thunderbird matter?"
date: 2012-03-26
forum: Any Other OS
---

### Post by freshminted on 2012-03-26
The damnedest thing. My colleague runs Windows 7, well someone had to. His fault free experience with Thunderbird soured a few days ago when he found that the same message keeps popping into his incoming email message box, blocking out all other incoming emails.

After stripping out Thunderbird and Firefox, rebooting and then making a fresh install of just Thunderbird, the problem came back. A check with a certain Microsoft Essentials virus hunter did absolutely nothing!

Now my colleague trusts me. I have suggested that if I strip out  everything from his machine, a rather nice HP, and reformat the drive with Ubuntu 11.10, he will have all the functionality but none of the problems. Fortunately his printer is an HP, and his Fuji camera seems to be compatible, so I see only a win - win situation by saying bye-bye to Win-Win 7.

However, if you think the problem can be resolved in an alternative way, I would be delighted to hear your views.

---

### Post by SeijiSensei on 2012-03-26
Is he using POP or IMAP?  The problem you describe sounds like the server is not properly marking a message as read.

If he's using POP with the "leave mail on server" switch checked, that can sometimes cause problems like the ones you describe.  If he wants to leave the mail on the server, he should be using IMAP rather than POP.  It's much more reliable in this situation.

---

### Post by freshminted on 2012-03-26
Thanks SeijiSensei, You may well be right. It is a pop server from BTInternet, which hasn't been changed, well not until I started to try it out. There is no Imap facility with them, and their default seems to be to leave the message on the server. I shall have a look at it again tomorrow when I see him and try to reset it either as imap, or more likely to save contents to his own machine.
Thanks again

---

### Post by SeijiSensei on 2012-03-26
In Thunderbird, check Account Settings > Server Settings and see if "leave messages on server" is checked.  This is typically a client-side setting.  Most ISPs don't want you leaving the mail on the POP server for storage reasons.  I once ran a POP server with a daemon that refused to accept this option precisely to keep people from storing too much mail on the server.

---

