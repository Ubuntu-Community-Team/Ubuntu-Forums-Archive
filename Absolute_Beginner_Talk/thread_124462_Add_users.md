---
title: "Add users"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by D__ on 2006-02-01
I've just installed Ubuntu 5.10 and I'd like to add some more users.  I went to System > Users and groups.  I was asked my password, entered it and ... nothing happened.  I've tried again and there's an icon in the taskbar saying "starting users and groups" but nothing happens.

Could someone point me into the right direction?

thanks

---

### Post by steve.horsley on 2006-02-01
Open a command prompt and enter the command **users-admin**. Let us know what happens, posting any error messages.

---

### Post by Sutekh on 2006-02-01
[QUOTE=D__]I've just installed Ubuntu 5.10 and I'd like to add some more users.  I went to System > Users and groups.  I was asked my password, entered it and ... nothing happened.  I've tried again and there's an icon in the taskbar saying "starting users and groups" but nothing happens.

Could someone point me into the right direction?

thanks[/QUOTE]
Can you run any application from the System -> Aminstration menu?

What is the output of
```
groups <your_username>
```

---

### Post by sprok8 on 2006-02-01
Are you logged in using the first account you created when you installed Ubuntu?

If you aren't, and you are logged in as a different user, then the easiest way to add users to use the first account again. While you're editing the Users and Groups dialogs, make sure you tick Administration as a task for any other users that should be allowed to run these tasks (such as the account you may be using).

If you already are using the first account you created, then the above won't help you. Sorry!

---

