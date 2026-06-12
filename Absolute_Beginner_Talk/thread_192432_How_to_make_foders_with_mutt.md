---
title: "How to make foders with mutt"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by jsmidt on 2006-06-08
I have ubuntu mail coming to me.  I want to save it in an ubuntu mail folder.  Instead it always saves it to mbox.

I set:

mailboxes = ubuntu

But when I exit it still promts me to save the ubuntu stuff to mbox.  Also there does not to even be an ubuntu folder.  So how do I:

1.)  Have mutt create an Ubuntu Folder for Ubuntu mail.
2.) Recognise Ubuntu mail and send it to the Ubunu folder instead of mbox.

Thanks.

---

### Post by LxP on 2006-06-22
[QUOTE=jsmidt]I have ubuntu mail coming to me.  I want to save it in an ubuntu mail folder.[/QUOTE]
With the mail highlighted or open for viewing, hit the 's' key. This will ask you for a location to save the mail. Entering '=ubuntu' (including the equals sign) and then hitting Enter will instruct Mutt to move the message into a mailbox called 'ubuntu', creating first if necessary. ('=' is shorthand for something like 'the default location to store all mailboxes' and will most likely expand automatically to '/home/*username*/Mail/ubuntu'.)

To open this mailbox at a later date you do the exact procedure as above, except hitting 'c' (for 'change to') instead of 's'.

Hope this helps!

---

