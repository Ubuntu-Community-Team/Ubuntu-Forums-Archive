---
title: "How to pick unique UID"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-01-31
How do you know that the UIDs and GIDs you have chosen are unique? Do you have to read /etc/passwd /etc/group ? How can I check whether the numbers I have picked up are unique and does the useradd command with the -u and -g options work if they are not unique (better not work).

---

### Post by Wicca on 2008-01-31
If you add a user, the system generates an unique UID for that user; there is no need to do that manually. Why do you want to do that?

I've never tried, but i'm quite sure the system will warn you if you try to give a user an UID that's already in use.

---

