---
title: "Cannot send mail via Evolution"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by panorack on 2007-04-30
I'm running Ubuntu 6.11 with a broadband connection to the internet using a Netgear modem via my Ethernet on-board chip. 

Internet connections are fine and Evolution downloads all my mail OK but it will not send mail. I have checked the configuration of the smtp settings and they are all correct. 

When I click the 'Send/Receive' button the progress info box shows receiving 'Complete' but the progress bar shows full against the send option with the message, 'sending message 1 of n' but will not clear. Neither Evolution or the computer have locked up as I can continue to work in Evolution but this progress box will not go until I press cancel. Needless to say the mail has not been sent.

Can anyone help with this. :(

---

### Post by SendDerek on 2007-04-30
I'm not sure if this helps, but some ISP's will require that you use their SMTP servers to send outgoing mail.  So, even if you have for example, gmail's POP3 and SMTP addresses set correctly, you'll need to use your ISP's SMTP server.  

mail.google.com
smtp.yourisp.net

Could this be the problem?

---

### Post by ajgreeny on 2007-04-30
I'm certain SendDerek is right; you need to ensure your smtp server is the right one for you ISP, with whom you log in to the internet, not the smtp mail server of the mail account you are using.  Whoever your ISP is shpuld be able to tell you their smtp server name, or you can probably find it on the internet easily.  Just change the mail account properties to ensure you use this smtp server, whichever mail account you are using for sending, and all should be OK.

---

### Post by panorack on 2007-05-01
Thanks guys, that was the problem. I changed to my ISP server and everything works fine. :)

---

### Post by KCormier on 2007-05-01
Please mark your thread as resolved once a solution has been posted. Log in, edit the first post in your thread, then choose the &#8220;Check box if your thread **IS** resolved&#8221; radio box. Save your changes, and you're done.

from [http://ubuntuforums.org/showthread.php?t=65842](http://ubuntuforums.org/showthread.php?t=65842) :)  Good to hear you got it sorted out!  I didn't know about that one!

---

