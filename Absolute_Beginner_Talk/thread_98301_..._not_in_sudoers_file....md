---
title: "... not in sudoers file..."
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-12-02
Hey...

I am co-root of a server, which is hosted at my mates house when, i created my own account, yet when i try to sudo i get this:

dwyerk is not in the sudoers file.  This incident will be reported.

How do i fix this?

Thanks,
Kris

---

### Post by invalid on 2005-12-02
You will need the default user, with root access, to add you to the sudoers file.
```
man sudoers
```for information on how to do it, using```
visudo
```

Cheers,
Cb

---

### Post by Qrk on 2005-12-02
System-->Administration-->Users and Groups-->Groups-->admin-->properties

I think you may need to run this from a user with admin access, but I'm not sure.

---

### Post by TeeSeeJay on 2005-12-02
[QUOTE=Qrk]System-->Administration-->Users and Groups-->Groups-->admin-->properties

I think you may need to run this from a user with admin access, but I'm not sure.[/QUOTE]

Yeah, the best way would be to get your account added to the admin group, which is already defined in sudoers. Your buddy will have to do it for you.

---

