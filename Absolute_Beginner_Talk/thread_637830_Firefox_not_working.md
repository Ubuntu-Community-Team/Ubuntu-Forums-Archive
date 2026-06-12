---
title: "Firefox not working"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by finito on 2007-12-11
I just installed a fresh copy of Xubuntu 7.10 32-bit. Ubuntu was dieing on me. anyway, The only this I have done is install the Modem which is a Connaxant HSF. I used the drivers from linuxant.com. I tried Pigdin Messenger to verify.

So now to the problem. I can't open Firefox. I click it and then it shows up on the taskbar and then it disappears. So far I tried:

        - Killing the Process and relaunching it.
        - Typing firefox in Terminal.
        - Restarting the Machine.
        - Removing from Synaptic and Reinstalling.
        - Completely Removing from Synaptic and Reinstall.

none of these helped.  

Please help.

---

### Post by shafin on 2007-12-11
what do you get when you type firefox in terminal?

---

### Post by finito on 2007-12-11
it says Firefox doesn't exist  and then gives you that sudo apt get install firefox  I am giving you this off my head as its annoying to boot back into Xubuntu, but thats basically what it says.

btw I tried Firefox and firefox since terminal is caps unfriendly.

---

### Post by mcduck on 2007-12-11
Try removing the .mozilla directory to remove all Firefox settings. (It's a hidden directory inside your home dir).

Also, start Firefox from a terminal so you can see if it outputs any error messages.

---

