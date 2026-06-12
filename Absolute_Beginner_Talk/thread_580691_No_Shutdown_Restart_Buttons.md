---
title: "No Shutdown Restart Buttons"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-10-19
I am missing my shutdown and restart buttons when I hit the quit button since upgrading to Gutsy.

I have seen many posts saying to solve it by switching to GDM, or KDM. This does not seem to make a difference.

I have also seen suggestions to use System > Administration > Login Window .... [x] Show Actions menu. This does not work as the Login Window app has disappeared since the upgrade.

I also heard it could be related to XGL wich was installed when I enabled desktop effects. I have uninstalled XGL server and disabled desktop effects and removed all compiz stuff. Still no luck.

Any Ideas?

---

### Post by loganm10 on 2007-10-19
it could be that user doesnt have enough privileges?

Can that user use sudo? because Im pretty sure to use the shutdown -whatever command you need superuser privileges

---

### Post by CaptainInsaneO on 2007-10-19
You can shutdown using```
sudo shutdown -P now
```

You can restart using```
sudo shutdown -r now
```

I know this doesn't entirely fix your problem, but it gives you a good workaround for the time being until you can figure out how to get your buttons back.

---

### Post by DSn0wMan on 2007-10-19
1. The user does have shutdown priveledges.
2. I don't mind shutting down from the terminal, but I am not going to show my wife how to do this, or give her sudo.

---

### Post by CaptainInsaneO on 2007-10-19
I think the Login Window suggestion will be your best bet at this point then. :)

If it's missing from your menus, you could probably get to it in terminal by typing

```
gksu /usr/sbin/gdmsetup
```

---

### Post by DSn0wMan on 2007-10-19
Very cool, I was wondering where that program might live. I'll try it when I get home. Thanks!

---

### Post by DSn0wMan on 2007-10-19
Thanks CaptainInsain0 that did the trick.

---

### Post by CaptainInsaneO on 2007-10-20
Glad to hear it, I love being of service. :)

---

