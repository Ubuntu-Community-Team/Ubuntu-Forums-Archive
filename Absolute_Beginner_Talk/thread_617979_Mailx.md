---
title: "Mailx"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-19
I installed mailx with 
sudo apt-get instaill mailx
i also got
sudo apt-get install mailutils

however, it doesnt seem to be working properly.

When i type:

 ifconfig | awk '{print  $2}' | head -2 | tail -1 | sed 's/addr://' | mail -s "MY IP" [email]jordler0@gmail.com[/email]

and then to check:

kristie@Sparktop:~$ mail
"/var/mail/kristie": 5 messages 1 new 1 unread
 R   1 Mail Delivery Syst Mon Nov 19 17:14  39/1290  Mail delivery failed: returning message to sender
 R   2 Mail Delivery Syst Mon Nov 19 17:24  39/1302  Mail delivery failed: returning message to sender
 R   3 Kristie Sparksman  Mon Nov 19 17:32  16/485   Kristie Sparksman
 U   4 Mail Delivery Syst Mon Nov 19 17:46  39/1297  Mail delivery failed: returning message to sender
>N   5 Mail Delivery Syst Mon Nov 19 19:24  37/1278  Mail delivery failed: returning message to sender



Note the "Mail delivery failed: returning message to sender"  Why is this failing?  I had an error earlier that said it could not send to remote domains.  Does anyone know what needs to be added to get mailx to send to remote domains such as gmail or hotmail?
Thanks.

---

### Post by jordank on 2007-11-20
are there even plugins for this program, and would they effect if i can email remote domains? this whole situation has me confused.

---

