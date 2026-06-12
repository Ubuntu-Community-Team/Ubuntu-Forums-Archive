---
title: "FireFox 2 permission issue"
date: 2007-01-16
forum: Apple PPC Users
---

### Post by Uta on 2007-01-16
I have no search engines in my toolbar and I can not add any search engines. I have started FireFox in the "safe-mode" and reset everything and still no search engines. If I start FF as root, I do have search engines. I chmod 777 the searchplugins folder but still no search engines. I have done an uninstall and then a reinstall still no search engines. Why do I have search engines as root and not as my regular user? How do I fix this permission issue? Thanks!

---

### Post by Uta on 2007-01-16
After many days of trouble shooting this and trying all the fixes I could find, I finally concluded that the "Default" user for FireFox was corrupted so I started Firefox in the terminal with this command:

firefox -ProfileManager

This gave me the opportunity to delete the "default" user and create a new user and when I opened FireFox I had my search engines back.

---

