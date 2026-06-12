---
title: "Brightness control on Asus UL20A"
date: 2011-06-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Frantic_Earthling on 2011-06-04
I have just installed 11.04 (with Unity) on an UL20A laptop.

The install went without a hitch.

Everything works, with the exception of the brightness and speaker function keys.

The key press registers after at least one minute which makes the function unusable and besides, it seems to have no effect.

In other words, when I press "Brightness Up" or "Down", the graphic display showing the key press appears a minute or so later and the brightness does not change.

I have tried to add "nomodeset acpi_backlight=vendor" to /etc/default/grub and did a "sudo update-grub" as suggested elsewhere on this forum, to no avail.

Has anyone experienced the same problem?

---

### Post by Frantic_Earthling on 2011-06-05
Bump....




> **Frantic_Earthling said:**
> I have just installed 11.04 (with Unity) on an UL20A laptop.

The install went without a hitch.

Everything works, with the exception of the brightness and speaker function keys.

The key press registers after at least one minute which makes the function unusable and besides, it seems to have no effect.

In other words, when I press "Brightness Up" or "Down", the graphic display showing the key press appears a minute or so later and the brightness does not change.

I have tried to add "nomodeset acpi_backlight=vendor" to /etc/default/grub and did a "sudo update-grub" as suggested elsewhere on this forum, to no avail.

Has anyone experienced the same problem?

---

### Post by Frantic_Earthling on 2011-06-06
Bump!

---

### Post by Frantic_Earthling on 2011-06-10
If anybody is interested, the following workaround worked for me:

[http://ubuntuforums.org/showthread.php?p=10923228#post10923228](http://ubuntuforums.org/showthread.php?p=10923228#post10923228)

---

### Post by vicherr on 2012-02-11
[FONT=Arial][SIZE=2]**Correct Solution:**

Enter the command:[/SIZE][/FONT][FONT=Arial][SIZE=2]

*[FONT=Lucida Console][SIZE=2]sudo gedit /etc/grub.d/10_linux[/SIZE][/FONT]*[/SIZE][/FONT][FONT=Arial][SIZE=2]  *[FONT=Lucida Console][SIZE=2]*******[/SIZE][/FONT]*

Edit [/SIZE][/FONT] [FONT=Arial][SIZE=2]
[FONT=Lucida Console]*GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA "*[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]

add[/SIZE][/FONT][FONT=Arial][SIZE=2]
[FONT=Lucida Console]*GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA ****acpi_backlight=vendor**"*[/FONT]

Save.[/SIZE][/FONT][FONT=Arial][SIZE=2]

In the terminal window:[/SIZE][/FONT][FONT=Arial][SIZE=2]

[FONT=Lucida Console]*sudo update-grub*[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]

Reboot.[/SIZE][/FONT][FONT=Arial][SIZE=2]


[FONT=Lucida Console]*******[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2] **NO **[FONT=Lucida Console]*/etc/default/grub*[/FONT] !!!!!!!!!!!!!!!!![/SIZE][/FONT]

---

