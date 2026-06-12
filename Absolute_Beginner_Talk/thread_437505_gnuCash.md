---
title: "gnuCash"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-08
I installed gnuCash and there is no icon in my applications menu.  I trued to run gnucash from the command line and it can not find the application.  I assumed that it simply was not in the path so I did a search for it and I found several icons but not the application.  Where does it get installed to and what is the command line to run the application?

Thank you

---

### Post by JAPrufrock on 2007-05-08
> **michael_besselman said:**
> I installed gnuCash and there is no icon in my applications menu.  I trued to run gnucash from the command line and it can not find the application.  I assumed that it simply was not in the path so I did a search for it and I found several icons but not the application.  Where does it get installed to and what is the command line to run the application?

Thank you

It should be in /usr/bin.   The executable file name is gnucash.  So from terminal run sudo /usr/bin/gnucash, and it should open.

Also check system - preferences - main menu to see if it's there. If it is all you have to do is check it to add it to your applications menu.  If not, you will have to create a file in /usr/share/menu.

---

