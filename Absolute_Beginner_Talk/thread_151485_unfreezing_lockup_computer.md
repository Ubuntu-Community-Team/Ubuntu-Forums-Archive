---
title: "unfreezing lockup computer"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-03-28
I certainly qualify as absolute beginner with Ubuntu.

After installing ubuntu I had to change the network settings to manually set IP and gateway. After I made the change, the system froze.  The wheel wasn't turning. I couldn't switch between windows. None of the drop-down menus were accessible.

Is there a keyboard command similar to Windows CTRL-ALT-DEL that will allow me to identify the trouble?

I had to shut power to the computer and turn it back on to get out.  

When the machine rebooted, the network connection worked as expected.  (Here I am...)

---

### Post by IYY on 2006-03-28
Ctrl+Alt+Backspace kills the X-server, returing you to the login screen.

---

### Post by codejunkie on 2006-03-28
even if the computer is hard locked pressing ```
ctrl+alt+sysrq+b
``` will force it to restart.

---

### Post by jlhughes on 2006-03-28
[QUOTE=IYY]Ctrl+Alt+Backspace kills the X-server, returing you to the login screen.[/QUOTE]


Ctrl+Alt+Backspace drops me to a command prompt with a login prompt.

Once I log in, how do I restart the GNOME desktop?

---

### Post by IYY on 2006-03-28
sudo killall Xorg
sudo killall gdm
sudo gdm (if it doesn't start by itself)

---

### Post by jlhughes on 2006-03-28
After Ctrl-Alt-Backspace I'm dropped to the prompt.  

I sign in using my username and password.

I give the sudo killall Xorg and the sudo killall gdm commands.  The Xorg command replies that there are no Xorg tasks to kill.

When I do sudo gdm (to restart the desktop), I'm told: "Only root wants to run gdm."

I am the only user. Why am I not seen as "root"?  (We are definitely in absolutely beginner territory here.)

John

---

### Post by trent dillman on 2006-03-28
Instead of sudo gdm, or killall anything, do it the proper way using init scripts.

After the CTRL+ALT+Backspace and console login:

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

---

### Post by gunderwood on 2006-03-28
try 

sudo /etc/init.d/gdm restart

from the command prompt to restart the gdm server.

---

### Post by trent dillman on 2006-03-28
gunderwood:

:-) I usually end up typing from the terminal in X, and the restart won't work. I guess I'm just used to having to stop, then log in, then start again. :-P

---

### Post by gunderwood on 2006-03-28
That's what I use when I have to restart X after a restart of X stalls. But I actually wouldn't have mentioned anything had I seen your post. You musta submitted just before me. 

Greg :)

---

