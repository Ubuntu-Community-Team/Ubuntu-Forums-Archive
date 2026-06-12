---
title: "Application Path?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Sig_ZA on 2007-06-17
I'm not sure how paths work in linux.
I've installed Gmail Notifier and it asks me for the path to the browser (Firefox). :?:

---

### Post by kevinlyfellow on 2007-06-17
Just about everything is in /usr/lib/firefox but the binary is linked in /usr/bin/firefox

---

### Post by BaffledMollusc on 2007-06-17
> **Sig_ZA said:**
> I'm not sure how paths work in linux.
I've installed Gmail Notifier and it asks me for the path to the browser (Firefox). :?:

To find out the path to an application you can type "which application_name" in terminal. If you do "which firefox" you'll probably get "/usr/bin/firefox"

This is the path, so try entering that. If it doesn't work, it might want the path without the application name, i.e. "/usr/bin"

---

### Post by Sig_ZA on 2007-06-17
which application_name - Nice!
A million thank yous...

---

