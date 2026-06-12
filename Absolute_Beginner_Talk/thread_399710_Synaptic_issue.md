---
title: "Synaptic issue"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by kahrytan on 2007-04-02
Why doesn't Synaptic use my theme style? Look at screenshot. The title bar is fine but controls are not.

---

### Post by justin whitaker on 2007-04-02
There are a bunch of theme related synaptic issues on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/synaptic?field.searchtext=theme&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/synaptic?field.searchtext=theme&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

This looks like this bug:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/63909](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/63909)

How about adding to the bug report and putting a screenshot up there?

---

### Post by bapoumba on 2007-04-02
Try:
```
sudo ln -s /home/your_login/.themes /root/.themes
sudo ln -s /home/your_login/.icons /root/.icons
sudo ln -s /home/your_login/.fonts /root/.fonts
```
see if it helps.

---

### Post by Nythain on 2007-04-02
to explain what bapoumba just said...

synaptic is using roots themes and whatnot... following the commands listed i believe would set roots themes to be that of your user account, thus keeping it looking like the rest of your ubuntu

---

### Post by bapoumba on 2007-04-02
Oh, thanks Nythains :)
I should add that you have to replace "your_login" with your actual user login.

/me will try to remember not to do several things at the same time, and thus pay more attention to the  answers /o\

---

### Post by kahrytan on 2007-04-02
Thanks. Would it be safe to make Themes be set at the root level?

---

