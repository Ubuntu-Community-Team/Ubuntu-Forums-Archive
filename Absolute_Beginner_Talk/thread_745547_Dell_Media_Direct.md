---
title: "Dell Media Direct"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-04-04
I have an Inspiron 1521 and I know the Dell Media Direct button will mess up my computer because I have ubuntu--heck, even when i had windows on it and I pressed it by accident I hgad to call dell for help because it tried to install and gave me an error. How do I remove the Dell Media direct partion (even though I don't see it on the hard drive, it must be hidden or something). On this website:[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420)
for a Dell Inspiron 1420 it says to disable the media direct button i have to go into the bios and turn off the FCM. Where in the BIOS do i find this FCM? I went in and tried looking for it but don't find it.

---

### Post by talsemgeest on 2008-04-05
Just start up gparted and delete the partition.

---

### Post by fetisha on 2008-04-06
Nope, it doesn't show up on the partition editor, but I was dumb *** and wanted to test it out and see if it would work, and unfortunately the button does work. So does any one know how to help?

---

### Post by fetisha on 2008-04-06
I went into the BIOS and looked under "Onboard Devices" and didn;t see anything called FCM or Flash Cache Module. :( But I know the darn button still works and it messed up my computer. Ubuntu loads grub and gives me an error 17.

---

### Post by fetisha on 2008-04-07
Re-installed ubuntu, but i know that the button works (obviously, because I was stupid enough to try it the other day). Now, since it doesn't show up as a partition on gparted and FCM doesn't show up in the BIOS, is there something I can do? Like, is it hidden somewhere on my computer?

---

### Post by anjilslaire on 2008-04-07
If you *really* want it gone, zero the drive. It'll force  a complete reinstall, ansd wipe *all* your data.

```

sudo dd if=/dev/zero of=/dev/sda

```

Boot the ubuntu Live CD, and do the above from a terminal. It took a couple hours on my 1420 if I remember correctly.

Then, install Ubuntu as normal, and carry on. The Media Direct key does nothing but throw a splash screen then switch to grub, or do nothing after the system is booted. :)

---

### Post by fetisha on 2008-04-08
Thanks. I;m doing it now. It's taken an hour so far, but at least it's doing something. Thanks again for the advice.

---

### Post by anjilslaire on 2008-04-10
Glad I could help.

How'd it go? Fix that pesky Media button? An extra bonus, is that ubuntu uses the button to launch your media player. I use kubuntu, so it launches amarok for me :)

---

### Post by fetisha on 2008-04-10
> **anjilslaire said:**
> Glad I could help.

How'd it go? Fix that pesky Media button? An extra bonus, is that ubuntu uses the button to launch your media player. I use kubuntu, so it launches amarok for me :)

Yeah, worked like a charm. It throws up the dell media stuff but then loads grub.

---

