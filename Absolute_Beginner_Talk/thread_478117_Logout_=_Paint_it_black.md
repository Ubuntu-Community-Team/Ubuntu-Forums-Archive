---
title: "Logout = Paint it black"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Saint_Schizophrenia on 2007-06-19
I'm running Kubuntu Feisty with 6 separate accounts. At least once a day when one of us logs out, instead of going to the login page, the screen just goes black. The only thing that responds is the mouse arrow. Using F7 or F8 to try to switch users does nothing because often there is only one user logged in anyway. No keystroke or combination of keystrokes has any effects. Banging on the keyboard has shown no effect and neither does cursing the computer, I usually just end up turning off the power and restarting it.

I'm at the end of my knowledge on the subject (as the banging on the keyboard and cursing might have tipped you off).

Anyone have any ideas? If you need more info about the specifics of my system, just let me know.

Thanks in advance.

thesaint

---

### Post by eentonig on 2007-06-19
Since it seems like X is getting hung up, you could try to use a new X session for every login. 

In system\Administration\Login Window

In the first tab, you have a checkbox to "Restart the X server with every login"

See if that changes anything.

---

### Post by Saint_Schizophrenia on 2007-06-19
I'll give that a shot and see how it works. Thanks.

---

### Post by damdim on 2007-06-19
kdesu kate /etc/kde3/kdm/kdmrc

Find the following and make the value "true"

# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
TerminateServer=True

---

### Post by markoloka on 2007-06-19
I don't  have such text.

---

