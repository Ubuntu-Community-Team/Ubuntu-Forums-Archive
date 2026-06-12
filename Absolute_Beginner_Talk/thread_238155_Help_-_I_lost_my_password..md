---
title: "Help - I lost my password."
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by sbutton on 2006-08-17
I've run passwd -d from root for the only user that I have set up on the system, and now I can't login.

I thought this would have the effect of allowing me to log in without a password. 

I know a lot of people say this is not a good idea, but anyway...

How do I get in now?

Thanks,

steve

---

### Post by taurus on 2006-08-17
Boot into recovery mode from GRUB menu, then at the prompt, type

```

passwd john
(assuming john is the user login name...)

```

---

### Post by Klaidas on 2006-08-17
Boot your system in recovery mode and reset the password :)

EDIT: Ah, I was too slow

---

