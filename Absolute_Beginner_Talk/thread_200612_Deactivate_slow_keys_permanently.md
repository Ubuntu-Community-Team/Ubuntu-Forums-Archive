---
title: "Deactivate slow keys permanently?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by muhkayoh on 2006-06-20
How can I deactivate the slow keys pop-up permanently?  I have several things that I'm doing that require me to hold the shift key, and these operations keep getting interrupted by that pop-up.  And before asking this question, I did a search on "slow keys" but only got a bunch of unrelated threads.

Thanks,

Matt Jordan

---

### Post by muhkayoh on 2006-06-20
Bump.

---

### Post by muhkayoh on 2006-06-21
And a one-ah, and a two-ah, it's for Santa...

---

### Post by warjowuch on 2006-07-06
I am also longing for a solution for the same (irritating!) 'problem', so I do another bump

Maybe this is related to all those accesibility-features, so it should be hidden in one of them...

---

### Post by warjowuch on 2006-07-06
Ah, found it in gconf-editor:

/desktop/gnome/accessibility/keyboard/ slow en sticky-keys there to config

three hooraays :-)

---

### Post by amccabe on 2006-07-07
I was unable to turn off slow-keys in gconf-editor, but I have figured out another way.

Go to:  System->Preferences->Keyboard

at the bottom of the dialog box between Help and Close is "Accessibility..."

press Accessibility

The "Keyboard Accessibility Preferences" window opens. Un-check "Enable keyboard accessibility features" at the top of the box.

That's it. I haven't had the "Slow Keys" dialog question come back.

---

### Post by warjowuch on 2006-07-15
Wow
THanks!

---

