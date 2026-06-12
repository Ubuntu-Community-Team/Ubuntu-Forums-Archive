---
title: "Thunderbird problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-06-09
I have installed mozilla-thunderbird, but I can't delete attachments, I've found a mozilla guide how to do it, the program asks me if I really want to do it because it can't be undone, but the attachment is still there, nothing changes=( Please help me.

---

### Post by neorou on 2007-06-11
What version are you using? 1.5.x.x? From repository? 

If you got it from repository, are you using POP or IMAP? If IMAP, does your server have a non-standard retention policy? IMAP problems can be solved by talking with your e-mail server admin. Make sure it's not that first.

If you are using POP, do you use attachment folders the same way Eudora does? Or do you have Thunderbird save attachments? By default, it should download attachments embedded in the messages.
Do you think you have disk permission issues? Try fixing permissions in your home folder.
Your Tbird profile should be saved in your home folder (/home/username/.mozilla-thunderbird/profile/x1x1x1x1.default - or something like this).

Also, if you use attachment folder in some random directory, that is a very high probability of permission issues as well...

---

### Post by sancho panza on 2008-05-17
I too have the same issue, and none of the above tips help. Thunderbird can delete attachments on some emails on an account, but cannot delete attachments on other emails of the same account. The undeletable attachments also have no definite pattern, some are jpegs, some are doc files, etc.

The only solution is to manually open the inbox file and delete the entry of that attachment. Its just not practical.

---

