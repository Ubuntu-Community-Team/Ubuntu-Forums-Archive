---
title: "Creating 2nd user for diffrent desktop"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-23
Hello, 
id like to make a new user account to test virtualbox and stuff, i just created a new "desktop" user, but i cannot use some administration tasks, like enabling resources. 

So do i need to create the 2nd user as administrator, or is there another way?

Thanks
:popcorn:

---

### Post by Aseld on 2007-12-23
Yes you need to make the second user an administrator. Do it from "Users and Groups" in System->Administration.

---

### Post by shareMenaPeace on 2007-12-23
ty

:guitar:

---

### Post by shareMenaPeace on 2007-12-23
Maybe you can tell me also how to get rid completly of the desktop user i created?

i choosed delte in user and group smanager ...but no success - trying to manual delete the home dir of this user says permission denied...

If i try 

sudo rm user  it says .. cannot delteits a folder.... what command please? And is this the correct way?

Thanks

---

### Post by Aseld on 2007-12-23
```
deluser [username]
```

---

### Post by shareMenaPeace on 2007-12-23
Thanx :)

:guitar:

---

