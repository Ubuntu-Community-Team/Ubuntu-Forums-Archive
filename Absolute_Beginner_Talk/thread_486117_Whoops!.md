---
title: "Whoops!"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by saxsux on 2007-06-27
I was playing around editing with the "main menu" preferences, and I somehow deleted my entire Preferences menu...
Is there any way to get it back?

---

### Post by floke on 2007-06-27
Right click on 'system' and select edit menus - then just check the box for 'preferences'.

---

### Post by p_quarles on 2007-06-27
Right-click on any of the other menus, then choose "edit menus."

---

### Post by saxsux on 2007-06-28
Sorry, I'd like to reiterate; I haven't just unchecked the menu, it just vanished completely.
Without finding out all the commands and icons, and creating the menu from scratch, can I get it back?

---

### Post by Anarchy965 on 2007-06-28
> **saxsux said:**
> Sorry, I'd like to reiterate; I haven't just unchecked the menu, it just vanished completely.
Without finding out all the commands and icons, and creating the menu from scratch, can I get it back?

You could just right click system and click "remove from panel"(make sure "lock to panel" isn't checked first), then right click the top menubar and click "+Add to panel". Once there, scroll down to the "menu bar" item under utilities and drag it up to to top menubar.

---

### Post by saxsux on 2007-06-28
The menu's exactly the same, m'afraid...

---

### Post by saxsux on 2007-06-29
Bump.
I'd really like to get my menu back. Isn't there any way?

---

### Post by p_quarles on 2007-06-29
Well, if none of the suggestions above have worked, I don't know what to tell you. You could just add a Control Panel launcher to the dekstop or on the panel. That will give you all the same functions, at least.

---

### Post by limbourg31 on 2007-06-29
sorry but there really is no way to completely getting it back without trying to edit your menu stuff manually, since you would have actually deleted the information from the actual config file. your best bet would be to check some other threads to see if someone was able to edit the menu files

---

### Post by saxsux on 2007-07-01
Thanks everybody who tried to help.
I just found the configuration file for my menu (~/.config/menus/settings.menu), and deleted this bit:
```

	<Move>
		<Old>Preferences</Old>
		<New>Preferences/Preferences</New>
	</Move>

```

Looks like my Preferences menu had somehow been moved inside itself. :P

---

