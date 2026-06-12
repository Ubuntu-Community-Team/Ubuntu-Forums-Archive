---
title: "Sessions problem."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by panosru on 2007-09-16
Hi, my problem is simple to understand but for me its not simple to solve as all these years i was windows user. Every time i go to System -> Preferences -> Sessions and make any changes to the list after a reboot or logout my changes are not saved :( although i have checked the "Automatic save sessions on change" on Sessions Options.. :(

EDIT:
I noticed now that when i make changes to Sessions window and pres close button then if i open it again (without any logout or reboot) changes are not there :(

EDIT2:
I connected with root user and anything works fine but with my user not working :(


EDIT3:
Ok problem solved, **isthatall** from #compiz-fusion IRC channel helped me and thank him very much! :D

For anyone that might have the same problem follow these steps:

1) Go to System -> Administration -> Users and Groups

2) Create a user with Administration right

3) login with the new user and open the terminal there run:

```
sudo chown -R old_username /home/old_username
```

then login with your old user and your done! :D

---

### Post by Ubuntized! on 2007-09-17
Please mark this as Solved

---

