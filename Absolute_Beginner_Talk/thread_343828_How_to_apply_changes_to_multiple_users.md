---
title: "How to apply changes to multiple users"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by CT Husky on 2007-01-22
I recently moved to an all-Ubuntu machine. FYI, i don't have much computer experience; just fumbling through as best I can with your help.

There are three users on the machine.

When I apply a change to an application such as Firefox, for instance enabling the IE extension option in the Firefox browser, is there a way to apply the same changes at the same time to the non-root users, without logging into their accounts and installing each item separately?

Thanks for any input.

---

### Post by aysiu on 2007-01-22
Extensions are installed to a subfolder of /home/*username*/.mozilla/firefox

So when you install an extension, it doesn't apply to all the other users. You may--and I'm not sure if this'll work--want to symlink the extensions folder to all the other users (a symlink in Linux is just like a shortcut in Windows or an alias in Mac).

---

### Post by Stephen Howard on 2007-01-22
I think they go into /usr/lib/firefox/extensions/.  Firefox checks there everytime its run.

---

