---
title: "onboard and Password Prompts"
date: 2009-08-21
forum: Assistive Technology &amp; Accessibility
---

### Post by gabrielbenjamin on 2009-08-21
I'm running Ubuntu 9.04 Netbook Remix on the AspireOne. I've noticed that at least one password prompt, the one for the Update Manager, won't accept input from onboard, because it makes other windows inaccessible. Is there a workaround for this?

Thanks in advance.

---

### Post by arky on 2009-08-24
Might be a bug, AFAIK update-manager uses gksu which works well with onboard. Can you try running this command in a terminal and see if it accepts input from onboard.

gksu update-manager

---

### Post by gabrielbenjamin on 2009-08-28
Didn't work, because the same prompt appears. However, on a lark, I tried this:
sudo update-manager
requests my password via terminal, which suits me fine.

---

### Post by tazztone on 2009-11-03
u could also copy your pw in the clipboard before the pw-window opens.. guess its easier to hack your pc that way

---

### Post by me13221 on 2010-02-23
I am using onboard and karmic and I still have this problem.  In, e.g., update-manager I cannot type in my password because the password-prompt window is modal.  I can login at gdm greeter using onboard just fine, but I can't do any administration once in the session.

Is there a fix?

---

### Post by deadhp1 on 2010-03-05
There is a fix.  Actually there are 2,  you can do either.

The first fix is to open up gconf-editor
(do not use sudo as these settings are user specific)
Navigate to apps/gksu and make sure the check box next to "disable-grab" is checked.

Or you can go into Accessibility Options and choose Password Dialogs as normal windows"

I've been using this with touchscreens/virtual keyboards for a while now. 
Hope it helps!

---

### Post by me13221 on 2010-03-10
Thanks! That did the trick.

---

