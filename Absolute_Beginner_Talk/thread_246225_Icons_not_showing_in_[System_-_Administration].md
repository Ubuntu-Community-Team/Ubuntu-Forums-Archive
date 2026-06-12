---
title: "Icons not showing in [System - Administration]"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by floatingboy on 2006-08-28
Hello,

I'm new to Linux.  I initally had one username that I created when I installed Ubuntu.  I just decided I wanted a different name, so I went to System - Administration - Users and Groups

This allowed me to delete my current one, and add a new one.  I made sure the new one's priveledges were all checked off (including Perform System Administration).  

I logged off, made sure that my old username was no longer available, and then logged into my new one.  However, for some odd reason the only options in my System - Administration bar are "Device Manager", "Network Tools", "Printing", "System Log", and "System Manager".  What happened to the rest??  There was alot more before. 

I even tried logging into root, and the same 5 options are only available there too.  What's going on here?  

Thanks for the responses in advance.

---

### Post by croak77 on 2006-08-29
Alt-F2 type alacarte. You'll be able to add items to your menu.

---

### Post by floatingboy on 2006-08-29
When I enter alacarte, all of the options are checked off but they still don't appear!

I think I know what I did.  I deleted the user that had the 'sudo' priveledges on my machine.  Am I screwed?

How do I make this user have the sudo ?

---

### Post by floatingboy on 2006-08-29
Figured it out!


I restarted in single user mode (root)

and typed:

adduser 'username' admin




worked like a charm!


Thanks.

---

