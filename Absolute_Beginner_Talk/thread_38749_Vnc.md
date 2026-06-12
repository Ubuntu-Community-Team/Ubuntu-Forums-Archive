---
title: "Vnc"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-06-01
I installed VNC in both my desktop running Ubuntu and my laptop running XP.
Everything seems to work fine, except that the desktop refuses the connection.
Can anybody clue me in?
Thanks in advance

E_M
Ps: I took a look at vnc.conf but nothing jumped at me from that cryptic perl code.

---

### Post by reynoldlariza on 2005-06-01
well i used WinVNC on my XP and just used Terminal Server Client on Ubuntu linux. 

I can view and control the desktop of ubuntu under my XP, and use Terminal Server Client to log-on to XP.

configure XP to accept remote connections from system properties add a User (e.g. Guest),  then on Ubuntu also configure it too to accept remote connections.
no need to use the VNC from Ubuntu, just the TSC to connect to XP.

For more information there's an instruction on XP about it from XP's help.
In ubuntu, just do configure it to allow remote conections :)

my apology if my message tend to be repetitive, just i'm kind'a having a heavy head a byte. ;-)

---

### Post by NewbieNik on 2005-06-02
I'm using RealVNC on a windows XP SP2 laptop and the standard Ubuntu hoary install on another. Set up remote desktop on Ubuntu "System/Preferences" to accept remote connections with password.
Can control Ubuntu fine remotely. 

Going the other way, I have just set a Password for VNC on the XP system and then, as mentioned before, used terminal server client on VNC protocol to access it.

You may get refused if you're accessing the wrong machine remotely. Have you checked that you have the correct names or IP addresses?

---

### Post by Error_Msg on 2005-06-02
This worked out well while testing at home.
The only snag is that Ubuntu pops a dialog saying that another user is trying to connect and you have to allow the connection.

E_M

---

### Post by Error_Msg on 2005-06-02
Never mind, never mind.

E_M
Ps: It never ceases to amaze me the power of a little checkbox hidden away in some preferences dialog box. :grin:

---

