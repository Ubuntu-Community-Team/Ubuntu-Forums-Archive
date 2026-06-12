---
title: "&quot;Users and Groups&quot; among others..."
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Gir_^ on 2006-07-25
Lots of times when i'm reading the forums/help guides they refer to the system/admin/SOMETHING... to which I don't have. I can't find the area that it says "Users and Groups" for example... any reason for this?

---

### Post by Ben Armston on 2006-07-25
Certain menu items can only be accessed run if the user has special admin rights. If the user doesn't have these rights then the menu items are not even shown. To get the admin rights you will need to add your user to the admin group. 

In order to do this you will need to have a user already on the system who is a member of the admin group. The first user added to the system (during the installation) is a member of the admin group so you should be able to use that account to do so.

Hope this helps.

---

### Post by avtolle on 2006-07-25
If you follow the advice in post #2, the desired "Users and Groups" will show up in System-->Admin-->Users & Groups.

---

### Post by Ben Armston on 2006-07-25
How to actually do this might be useful ;).

From the terminal:

```
sudo usermod -G admin -a <your_user_name>
```

or if you login as the user created during the installation, then you can use system->administration->users and groups

---

### Post by Gir_^ on 2006-07-25
When i installed, i was never asked to create a user, all i was ever asked for was a "password"... therefore, i doubt i have any user that is a memeber of the admin group. and now my mouse broke like it always does after about 5 min in ubuntu!! AWESOME.

---

### Post by Gir_^ on 2006-07-25
and no, ben Armstrong that didn't work... maybe because i rebooted to fix my mouse... nope, tried it again and still doesn't work.

---

### Post by Ben Armston on 2006-07-25
> **Gir_^ said:**
> and no, ben Armstrong that didn't work

I presume that you're refering to the command line. Could you try it again and post the error message that it gives. Also, could you provide the output of

```
groups
```

---

