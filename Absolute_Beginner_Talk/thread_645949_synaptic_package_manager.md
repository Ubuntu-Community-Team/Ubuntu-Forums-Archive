---
title: "synaptic package manager"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2007-12-20
I have been having a problem where I can't find the icon to synaptic package manager, so I typed synaptic package manager into the terminal. This opens the program, but I can't apply any changes.
I think this has something to do with administrative priveliges but I don't know how to fix it. 

I also tried adding sudo to the front of the command, but after prompting me for a password, it simply does nothing and doesn't open synaptic.
Thanks in advance for the help!

---

### Post by Joeb454 on 2007-12-20
Try opening it via System > Administration > Synaptic Package Manager

---

### Post by metalpancake on 2007-12-20
yea, I wish I could. There is no icon. That's why I tried to run it in the terminal in the first place.

---

### Post by PaganHippie on 2007-12-20
You can run synaptic from the command line with root privileges by putting either sudo or gksu before it:

```
sudo synaptic
```or

```
gksu synaptic
```

---

### Post by metalpancake on 2007-12-20
I tried doing that and it doesn't seem to do anything when I hit enter. Is it meant to open synaptic in another window?

---

### Post by emackey3k on 2007-12-20
Also, to get your icon back I think you should be able to right click your System menu on the panel and choose 'edit menus'.  Under administration you should see Synaptic Package Manager.  If there is not a check mark next to it click it and it should be there.

---

### Post by RomeReactor on 2007-12-20
Hi. Try launching it as:
```
gksu /usr/sbin/synaptic
```

Also make sure you didn't uninstall it by accident:
```
sudo aptitude install synaptic
```

Make sure there are no typos when entering the commands.

---

### Post by Shazaam on 2007-12-20
Open terminal and type this in...
```
alacarte
```

This code will open the Alacarte Menu Editor. Poke around in "System>Administration" and see if Synaptic is there and if the checkbox is still checked.

---

### Post by metalpancake on 2007-12-20
ok, so i went into the edit menu screen and found synaptic. I ticked the box, but after a few seconds it unticked itself!:confused:

---

