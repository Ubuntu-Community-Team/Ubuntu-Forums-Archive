---
title: "copy thunderbird filters from one gusty to another"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-11-07
Hi, I have two machines running Gusty with Thunderbird Imap accounts.  I would like to copy one set of message filter from one to the other. Can i do so and if so any guides?

---

### Post by kebes on 2007-11-08
> **pfwd.tech said:**
> Hi, I have two machines running Gusty with Thunderbird Imap accounts.  I would like to copy one set of message filter from one to the other. Can i do so and if so any guides?

According to this page:
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Filters](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Filters)

The message filters are stored in a file called "msgFilterRules.dat". The exact location of this file depends on which account you stored the rules in. If you linked the rules to the "Local Folders" account then you can find that file in your thunderbird settings folder, in the "Local Folders" sub-folder.

The full path on your system is probably something like:
/home/username/.mozilla-thunderbird/oiqj9f89.default/Mail/Local Folders/msgFilterRules.dat

So just copy that file to the profile directory on the other computer, and it should automatically recognize your filter rules.

---

### Post by AnRkey on 2008-07-16
kebes: Thanks for this.

For the rest of you... the file I had to move for my imap account was in a sub directory for my imap account.

```
/home/username/.mozilla-thunderbird/rgxdngtj.default/ImapMail/192.168.0.245/msgFilterRules.dat
```

It looks like each account that you have set up has it's own copy of this rules file.

I hope this helps someone else too.

R

---

