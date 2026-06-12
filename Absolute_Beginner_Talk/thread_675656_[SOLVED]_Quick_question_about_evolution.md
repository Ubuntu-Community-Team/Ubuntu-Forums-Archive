---
title: "[SOLVED] Quick question about evolution"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-22
How do I set up gmail, and yahoo email accounts into evolution?
I need to know what kind of mail client they are...? I guess?

---

### Post by Arthur Archnix on 2008-01-22
I don't know about yahoo, but gmail has instructions available that tell you what settings to use. Ignore the fact that they are targeted towards specific programs (outook, thunderbird, etc.) and just find the settings they tell you to change in evolution.

If you need to change the smtp port in evolution you do it by adding a colon after your server, followed by number. Eg., smtp.gmail.com:995

---

### Post by balaknair on 2008-01-22
In Gmail you can use POP3 or IMAP once you enable it
To enable it you have to log into your Gmail account in your browser, go to the settings page(Upper left corner of the inbox page)>Forwarding and POP/IMAP>there you can choose enable POP or IMAP as you want. Links to Configuration instructions are provided for each on that page.
POP in Gmail seems to perform better in my experience(and that of a few friends), so I suggest you go with POP rather than IMAP. Plus it's harder to mess up with POP.
IMAP on the other hand is more advanced and allows 2-way interaction- changes you make in your Evolution inbox will be reflected in your Gmail inbox. POP on the other simply downloads the messages in your Gmail inbox to your computer and even if you lose the stuff on your PC(accidentally deleting it, hard drive failure etc), there will still be a backup on the gmail server. So if you're really new to this I suggest you try POP first and later when you're comfortable try out IMAP.

For Yahoo mail, POP/IMAP is not currently supported.

---

### Post by Jeezus on 2008-01-22
Thanks guys!
I appreciate it!

---

### Post by y-lee on 2008-01-23
> **Jeezus said:**
> How do I set up gmail, and yahoo email accounts into evolution?
I need to know what kind of mail client they are...? I guess?

I use ypop3 for yahoo, see [Ypops for linux]("http://fileforum.betanews.com/detail/YPOPs_for_Linux/1033572889/3").

---

