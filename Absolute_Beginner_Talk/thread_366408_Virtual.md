---
title: "Virtual"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Falconxx on 2007-02-20
I have a dual boot system, XP Pro and Ubuntu. Both work great.

Now I want to install Vitual PC 2007. Anybody have this setup or something
like it. Will there be any problems booting into the different systems by adding
Virtual PC 2007?

Thanks

Falconxx

email:  [email]bobba_fett@sympatico.ca[/email]

---

### Post by Strider on 2007-02-20
Hi,

You can't run Linux on Virtual PC 2007.  If you have XP as your host system you can use VMWare to run Linux.  If you have Ubuntu as the host system you can also use VMWare.  Virtual PC 2007 only works for MS based OS along with OS/2.

-Mike

---

### Post by Falconxx on 2007-02-21
What I want to do i install Virtual PC to operate with XP Pro but do not want it to interfere with Ubuntu. I do a lot of checking on spyware and malware programs in windows. I can use Virutal Pv for this. Ubuntu runs on a separate drive by itself. This arrangement I have
setup works great.

Thanks

Falconxx

---

### Post by jkeyes0 on 2007-02-21
> **Strider said:**
> Hi,

You can't run Linux on Virtual PC 2007.  If you have XP as your host system you can use VMWare to run Linux.  If you have Ubuntu as the host system you can also use VMWare.  Virtual PC 2007 only works for MS based OS along with OS/2.

-Mike

Actually, I've got Ubuntu 6.10 on VPC 2007. It took some extra steps to install for me, but it's definitely there. When I started the LiveCD, the color depth defaulted to 24-bit, and VPC won't handle anything higher than 16, so I had to drop to TTY1 (Ctrl+Alt+F1) and edit the xorg.conf file to make the default depth 16, then kill/restart the X server (Ctrl+Alt+F7, then Ctrl+Alt+Backspace).

I had to do the same thing after I installed the system, if I remember correctly, but it's a one-time thing, and it's running just fine right now.

---

### Post by nipper_uk on 2007-02-21
> **jkeyes0 said:**
> Actually, I've got Ubuntu 6.10 on VPC 2007. It took some extra steps to install for me, but it's definitely there. When I started the LiveCD, the color depth defaulted to 24-bit, and VPC won't handle anything higher than 16, so I had to drop to TTY1 (Ctrl+Alt+F1) and edit the xorg.conf file to make the default depth 16, then kill/restart the X server (Ctrl+Alt+F7, then Ctrl+Alt+Backspace).

I had to do the same thing after I installed the system, if I remember correctly, but it's a one-time thing, and it's running just fine right now.

Just tried following your instructions to install 6.1 on VPC 2007 but cannot get it to go. Could you explain what TTY1 one is please?

Thanks

---

### Post by jkeyes0 on 2007-02-21
> **nipper_uk said:**
> Just tried following your instructions to install 6.1 on VPC 2007 but cannot get it to go. Could you explain what TTY1 one is please?

Thanks

TTY1 is basically command line. When I booted my VPC the first time, the screen went to a strange resolution, so I hit Ctrl+Alt+F1 (left Ctrl and left Alt, or it won't work) to drop to a command line. Ctrl+Alt+F1 through F6 will give you command line access when the desktop isn't working properly.

---

