---
title: "Removing nvidia drivers?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by renzokuken on 2007-05-14
how do i remove the nvidia drivers completely?

i want to remove them and reinstall the latest version. i think the ones i have installed at the moment were done using albertomilone's (tseliot) latest "repo" method.

i will probably use envy to install the newest ones

thanks

---

### Post by dpar on 2007-05-14
If you installed using Envy, there is also an uninstall on Envy.

---

### Post by starcraft.man on 2007-05-14
> **dpar said:**
> If you installed using Envy, there is also an uninstall on Envy.

Well, even if you didn't install with envy, I think ya can still use their uninstall automatically option. Should detect em. Don't forget to switch to your nv drivers, else you will lose your gdm if you reboot. If that doesn't work you can always just do the terminal way:

```
sudo aptitude search nvidia
```

should bring up any installed nvidia things, they will be listed with i or v next to em.

You could then remove em with:

```
sudo aptitude remove x y z
```

where x y and z are whatever was listed in previous.

---

