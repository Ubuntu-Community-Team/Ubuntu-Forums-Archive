---
title: "how to list user from console"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2006-01-04
hi, 
I have a monitorless ubuntu box with ssh access... and i don't know how to list the users from the console... anybody know how to do this?

thanks

---

### Post by piedamaro on 2006-01-04
To find who is logged in use: 'who'
To find which users are configured on a system try: 'cat /etc/passwd'
To find additional info on a user type: 'finger <username>'
Hope this helps ;)

---

### Post by ape on 2006-01-05
The 'w' command also has some useful info that supplements the info shown by `who`.

---

