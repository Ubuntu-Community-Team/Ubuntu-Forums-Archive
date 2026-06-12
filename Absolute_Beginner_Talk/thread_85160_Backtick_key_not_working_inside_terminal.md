---
title: "Backtick key not working inside terminal"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by mfyahya on 2005-11-01
My backtick key beeps instead of printing ` at the command line. It works fine with shift to produce tildes ~ though. It works ok everywhere else too. 
I'm pretty sure I messed it up myself while playing with various desktop settings, but I can't remember where.

Please help.

PS. The beep is from the regular speakers, not the PC speaker

---

### Post by gord on 2005-11-02
are you sure your running in the right keyboard layout for you? system -> preferences -> keyboard -> layouts in hoary

---

### Post by mfyahya on 2005-11-02
yes, I'm using a Dell inspiron 6000 laptop with the keyboard set to US English.
Like I said earlier the ` key works fine everwhere except on the command line. I tested all the keys, everything works as expected. I can even do ~ on the commadn line, just no `
This is really wierd.

---

### Post by gord on 2005-11-02
you sure you havn't messed about with the keyboard shortcuts? (try pressing F10 and then pressing `)

---

### Post by mfyahya on 2005-11-04
I tried that and discoverd more wierdness. The <F5> through <F12> keys produce ~ at the terminal command line. They're ok every where else. And I still cannot type ` inside terminals.

---

### Post by mfyahya on 2005-11-06
The good guys on #ubuntu showed me how to fix this. Apparently I had 'Editable menu accelerators' turned on in the Menu and Toolbar prefs, and then I had accidently mapped ` to prev_tab in the terminal menus. 
So I learned to safer to have that option turned off!
This command showed the problem:
gconftool-2 -R /apps/gnome-terminal/keybindings | grep grave
Hope this helps someone.

---

