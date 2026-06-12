---
title: "/var/www/* Permissions"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-05
I know I may be the 101 person to ask this question, but I have searched the Forum and google and still have no idea!

Basicly... I have created an account user called test and that is part of the group ftp.

Do I need to: 

 *[FONT=Calibri]sudo chown -R test /var/www/*[/FONT]*
  *[FONT=Calibri]sudo chgrp -R ftp[/FONT]**[FONT=Calibri]/var/www/*[/FONT]*
  

And thats it... is there anything else i should do or need to know?

Kind Regards

Robin Lennox

---

### Post by nhandler on 2007-03-05
That should do it. Give it a try.

---

### Post by robinlennox on 2007-03-05
Cheers for that!

Just one last question....

I am using proftpd, and the umask is set to 022 022, i had to change it to 002 002, to get the upload permissions to work... is this normal?

Kind Regards

Mr Noob :lolflag:

---

