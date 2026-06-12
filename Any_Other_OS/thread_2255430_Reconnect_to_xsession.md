---
title: "Reconnect to xsession"
date: 2014-12-05
forum: Any Other OS
---

### Post by bkvaluemeal on 2014-12-05
When I run startx and then change to a new tty the gui closes, but the server is still running. How do I make it so that I return to the gui on that tty?

---

### Post by coldcritter64 on 2014-12-05
The GUI only exists on one tty, usually tty7 (ctrl + alt + F7) or higher, even if you launch from a lower number tty (1 to 6). If you swap to say tty2 with ctrl + alt + F2 then to return to the GUI use ctrl + alt + f7, if that is blank try other higher tty terminals it should still be there on one of them. 

I have on occasion found it on tty8 usually after I have messed with and had to recover a session it can be found on another terminal, check all higher tty terminals up to ctrl + alt + F12, it should be there unless you have some sort of more serious problem in play.

---

### Post by bkvaluemeal on 2014-12-05
I should clarify that I'm trying to build my own personal distro from the ground up. I've installed xorg, openbox, tint2 and configured my .bashrc to automatically run startx. I want the gui to start on the tty I log into, not tty7. The problem is, like I said, the gui breaks when I switch ttys. There has to be a way to fix that because it works on every other distro.

---

### Post by coldcritter64 on 2014-12-05
> I want the gui to start on the tty I log into, not tty7.I have done minimal installs of both Ubuntu and Debian. Every time I have used startx from tty1 the GUI is automatically launched on tty7, if from tty2 then the GUI used to fire up on tty8. I assumed that was normal procedure for X to do so. ttys 1 to 6 were always used for text consoles only, 7 to 12 are for GUIs. 

With one particular Debian net-install with XFCE installed from the console, firing up startx on ttys 1 to 6, would put a separate desktop session on ttys 7 to 12, an up to six headed set up.

> I've installed xorg, openbox, tint2 and configured my .bashrc to automatically run startx. That sounds quite a bit different to how I've set up installs that used startx. But I suspect if configured right X should still work in a similar fashion. Wait for more experienced users to advise you on this with your set up ;). [B]
Edit:[/B] Is this on an Ubuntu minimal base or a full install with openbox as another desktop option ?

> The problem is, like I said, the gui breaks when I switch ttys. Exactly how does the GUI "break" ? 
This may be getting past my ability to help much, some others here may have to help if you have a more serious configuration problems with this being a custom build. 

Good luck with this, sounds an interesting project. I'll be keeping an eye on it.

---

### Post by coffeecat on 2014-12-05
> **bkvaluemeal said:**
> I should clarify that I'm trying to build my own personal distro from the ground up. 

*Thread moved to **Any Other OS**.*

---

### Post by bkvaluemeal on 2014-12-05
> **coldcritter64 said:**
> I have done minimal installs of both Ubuntu and Debian. Every time I have used startx from tty1 the GUI is automatically launched on tty7, if from tty2 then the GUI used to fire up on tty8. I assumed that was normal procedure for X to do so. ttys 1 to 6 were always used for text consoles only, 7 to 12 are for GUIs.

I didn't realize it did that. I understand now, but how could I make it start on tty1 and not tty7? Is that a wise thing to do?
> **coldcritter64 said:**
> Is this on an Ubuntu minimal base or a full install with openbox as another desktop option ?

I'm using a Debian base install, but between Ubuntu and Debian the base is the same iirc.

---

### Post by steeldriver on 2014-12-05
How exactly are you running startx from your .bashrc file? that sounds potentially problematic to me (.bashrc is sourced for any shell, not just a login shell, I think). Perhaps you should move the startup to ~/.bash_profile? You'd still need to consider what might happen for remote shells.

You should be able to specify the virtual terminal explicitly to startx - I just tried it on my 12.04 laptop i.e. after stopping lightdm and switching to tty2 (Ctrl-Alt-F2) I logged in and then executed

```

exec startx -- :0 vt2

```

Confirming that it really did start on vt2:

```

$ w  
17:46:02 up 31 days, 11:58,  4 users,  load average: 0.00, 0.32, 0.87
USER         TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
steeldriver  tty2                      17:33   12:18  14.22s  0.00s xinit /etc/X11/
steeldriver  pts/0    :0.0             17:34   11:22   0.25s  0.25s bash

```

I can switch back and forth successfully using the Ctrl-Alt-Fn keys, just the same as when the default lightdm instance is started on vt7

---

### Post by bkvaluemeal on 2014-12-05
> **steeldriver said:**
> How exactly are you running startx from your .bashrc file? that sounds potentially problematic to me (.bashrc is sourced for any shell, not just a login shell, I think). Perhaps you should move the startup to ~/.bash_profile? You'd still need to consider what might happen for remote shells.

Like this:
```
if [[ -z $DISPLAY ]]; then temp=$(tty) && exec startx -- :${temp:8} vt${temp:8}; fi
```

What's different between ~./bashrc and ~/.bash_profile?
**Edit:** After reading [this]("http://hacktux.com/bash/bashrc/bash_profile") I think I should change it.

---

