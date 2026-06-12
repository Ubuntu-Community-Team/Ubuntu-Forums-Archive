---
title: "Mac &quot;Mail&quot; compatible email client?"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by 2cute4u on 2008-04-30
I just set up my iMac to have a shared home directory for both OS X and Ubuntu. I've been able to use symbolic links to make programs on both platforms share data, preferences, bookmarks, etc. but I'm still looking for an email solution.  I want to find an email client, that can use the same mailbox, folders and files as mac mail, so that if I check my mail in one, it is updated in the other.  Does anyone know of a good email client that can do that?

---

### Post by cyberdork33 on 2008-04-30
> **2cute4u said:**
> I just set up my iMac to have a shared home directory for both OS X and Ubuntu. I've been able to use symbolic links to make programs on both platforms share data, preferences, bookmarks, etc. but I'm still looking for an email solution.  I want to find an email client, that can use the same mailbox, folders and files as mac mail, so that if I check my mail in one, it is updated in the other.  Does anyone know of a good email client that can do that?
use thunderbird on both OSX and Ubuntu.

---

### Post by Tommy on 2008-04-30
> **2cute4u said:**
> II want to find an email client, that can use the same mailbox, folders and files as mac mail, so that if I check my mail in one, it is updated in the other.  Does anyone know of a good email client that can do that?

As someone else pointed out, Thunderbird will do that, and Evolution probably will, too. However, the "secret" tip nobody has pointed out is called IMAP.

"normal" old fashioned email grabs each message using Post Office Protocol ("POP") and permanently copies the message to your email account, where it may or may not be available to any other program.

If, however, you access your email using IMAP, the messages can stay on the server, and when you move them to folders, mark them read or delete them, the changes are visible to every other client you connect with.

Here at my home office I have three email accounts that I connect to using IMAP, so whether I connect to my email from my wife's iBook, my own Ubuntu desktop, or my cell phone, the messages are all visible, and any changes I make to one appears on all the others.

Some email providers do not support IMAP, but it's becoming very common. It's actually easier on the server than POP. The only downside to the provider is you will probably keep all your email on the server. But services like Google Mail provide lots of space, and they allow IMAP too. (You have to specifically activate it.)

---

### Post by alriemi on 2008-06-12
[http://bab.com/news/full_news.cfm?id=99836&cat_id_cache=29](http://bab.com/news/full_news.cfm?id=99836&cat_id_cache=29)

---

### Post by stream303 on 2008-06-12
> **cyberdork33 said:**
> use thunderbird on both OSX and Ubuntu.

+1

I personally go this route by using Mozilla Thunderbird on both machines - although I have never shared the data between them with a common data mailbox.  That would definitely be neat.

---

### Post by pijon on 2008-06-12
I'm switching between Linux and OS X all the time. I don't like IMAP, so I've configured Mail.app not to delete any new mail (newer than a week old) on the server. So when I switch to Ubuntu, Thunderbird downloads the mail too.

---

### Post by _alex_ on 2008-06-12
I use IMAP; Mail in OS X, and Evolution in Ubuntu. I also set up Evolution at work. The best thing about IMAP is that it's client agnostic, so in theory you can use any client on any OS (though the setup to get them to use the same spam folder, trash folder etc takes a little while, but it's worth it IMHO).

---

### Post by cyberdork33 on 2008-06-12
> **_alex_ said:**
> I use IMAP; Mail in OS X, and Evolution in Ubuntu. I also set up Evolution at work. The best thing about IMAP is that it's client agnostic, so in theory you can use any client on any OS (though the setup to get them to use the same spam folder, trash folder etc takes a little while, but it's worth it IMHO).

I use thunderbird portable at work, and thunderbird on my Mac in OS X and in Ubuntu. 2 IMAP accounts. works fairly well. (Thunderbird for OS X seems to lockup sometimes).

---

### Post by Tommy on 2008-06-13
> **pijon said:**
> I don't like IMAP
I should probably just let it go, but what's not to like about IMAP? I believe in most clients you can configure it to copy the messages permanently, just like POP, and the hosting companies say it's easier on their servers. :)

---

