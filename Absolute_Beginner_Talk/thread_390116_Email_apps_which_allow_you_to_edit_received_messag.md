---
title: "Email apps: which allow you to edit received messages?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by nghab on 2007-03-21
Although I am using Ubuntu more often than Windoze (excluding work), and have previously used other distributions (Libranet, Xandros, others) I still download my email  to a Windoze box because I haven't found an email application that allows me to edit messages received in the inbox.

What I mean by that is if, for example, I receive an e-newsletter or a listserv digest and I am interested in saving only portions of it that are of interest to me and deleting the rest of the bulk, I want to be able to edit and save the relevant parts--within my email directories/"folders"-- without having to resort to saving it as a text message and filing individual word processing files.

Eudora (and Eudora Light) has long had that functionality.  Even M$Outlook (work) allows me to do that.  But as far as I can tell, neither Thunderbird nor Evolution does.  I haven't tried K-Mail yet to find out (I also don't want to set up a dozen different email programs speculatively just to test them all), but the documentation I've seen doesn't refer to any such capability.

The following excerpt from the Eudora manual refers to the kind of feature I'm looking for in a Linux email application:

----
Editing Incoming Messages

You can edit the message body in an incoming message if you select the Pencil button in the toolbar. You can also edit the Subject in the Toolbar (this is the subject shown in the message summary), and you do not need to select the Pencil button to do this.To edit an incoming message, click on the Pencil button to turn it on, then edit the message body. When you are done, save your changes and close the message.

-----

(In M$Outlook, it's Edit --> Edit Message rather than Eudora's "pencil" button.)

----


Can anyone on this list recommend one that has such a function does, or am I doomed to keeping a Windoze machine going just so I can continue to use Eudora.  (I haven't installed or tried WINE yet, and perhaps that might be a way to run Eudora, but with the right functions, I'd prefer to use an open source email application rather than continuing with Eudora... okay, I know that Eudora is going open source, but still only in Windoze and Mac, so what I really mean is a native Linux application.)

Thanks.

Now go have a beer...

---

### Post by NJC on 2007-03-21
I'm at work and not near my Tbird computer but I wonder if the Edit as New feature would do it? Or maybe this Extension would work:

[https://addons.mozilla.org/thunderbird/3563/#genid3](https://addons.mozilla.org/thunderbird/3563/#genid3)

---

### Post by nghab on 2007-03-21
> **NJC said:**
> I'm at work and not near my Tbird computer but I wonder if the Edit as New feature would do it? Or maybe this Extension would work:

[https://addons.mozilla.org/thunderbird/3563/#genid3](https://addons.mozilla.org/thunderbird/3563/#genid3)

I may be misinterpreting it, but it seems that "Edit as New" lets you compose a "new" message with the text of the received message, no?

The only "solution" I found documented was:

[http://kb.mozillazine.org/Edit_a_stored_message](http://kb.mozillazine.org/Edit_a_stored_message)
"You can move a message to the Drafts folder, double click on it, edit it, save it as a draft, and then move it back to the original folder. This lets you change the message body. The main disadvantage is that it creates a new message with you as the sender and the current date/time. So you may want to also use one of the methods in the next section to restore the visible headers."

...which wasn't really saitsfactory because of the stated disadvantage

(Is "edit as new" different from this?)


and the other suggestion to edit the entire .mbx file in a text editor seems clumsy and inconvenient.  It's not that I'd be afraid of screwing something up, but that the .mbx file could be very long, so would be tedious.

---

### Post by moore.bryan on 2007-03-21
*like above, sylpheed can "re-edit," but i think it's only with messages you send,  not received ones...*

---

### Post by nghab on 2007-03-21
.

---

### Post by NJC on 2007-03-22
> **nghab said:**
> I may be misinterpreting it, but it seems that "Edit as New" lets you compose a "new" message with the text of the received message, no?

Unfortunately that's exactly right. I saved after trying a Edit as New and it saved into Draft folder. It's possible someone has written an Extension for what you need.

---

