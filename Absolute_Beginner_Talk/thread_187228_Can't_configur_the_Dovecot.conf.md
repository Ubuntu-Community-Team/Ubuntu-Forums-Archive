---
title: "Can't configur the Dovecot.conf"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Jengle on 2006-06-02
I am trying to install Dovecot.  When using a text editor to configure dovecot.conf I get a message "could not open the file etc/dovecot/dovecot.conf
access denied"

any suggestions?

---

### Post by blackjack6.21.91 on 2006-06-02
Try running
     sudo gedit /etc/dovecot/dovecot.conf

I'm guessing you need root privelages to edit the file

---

### Post by Jengle on 2006-06-02
[QUOTE=blackjack6.21.91]Try running
     sudo gedit /etc/dovecot/dovecot.conf

I'm guessing you need root privelages to edit the file[/QUOTE]


That was the ticket...Thanks](*,)

---

