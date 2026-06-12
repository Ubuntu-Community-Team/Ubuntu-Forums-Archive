---
title: "Email signature"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-02-17
I'm using Ubuntu as a mail relay for all my in/outbound email. How can I add a signature to all outbound email?

---

### Post by houseofmore on 2006-02-17
You would do that within your mail client settings.

---

### Post by localzuk on 2006-02-17
which MTA are you using? Postfix?

The only method I can think of is to have a seperate content filter - such as an email scanner - which does it for you.

Take a look at the list of content filters available here: [http://www.postfix.org/addon.html](http://www.postfix.org/addon.html)

---

### Post by localzuk on 2006-02-17
This would only be any use if all clients were controlled by the user - what if he wants to add a line such as 'Sent by company x' to all emails?

---

### Post by uopjohnson on 2006-02-17
Changing an outgoing mail on the server is a tricky business and I don't recommend it.   

modern email messages are often composed of multiple parts and formatted in a variety of ways.  Traditionally it was fairly straight forward to add a block of text to the bottom of an all text email and you will still see this on programs (like web mail, yahoo, etc) that control the sending environment.
However the issue arises when a user is able to send mail from whatever Mail User Agent (evolution, thunderbird, pine, etc) they want because then the server has to make a decision about where to break into the mail in order to add a signature block.  

If possible you should just use your mail program (thunderbird, or evolution) to add signatures to outgoing mail.  
What are you hoping to accomplish by doing this? 

If you are still interested in accomplishing this I would suggest moving this post over to the server channel so that more experienced postfix users can give you a hand.
Otherwise if you need help adding signatures with your mail program then let us know what you are using to send mail.

---

### Post by My-dial-up on 2006-02-17
Have asked in the 'server' section.

[http://ubuntuforums.org/showthread.php?t=132086](http://ubuntuforums.org/showthread.php?t=132086)

---

