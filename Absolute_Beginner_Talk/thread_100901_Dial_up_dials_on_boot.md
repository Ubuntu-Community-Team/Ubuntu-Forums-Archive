---
title: "Dial up dials on boot"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by lila on 2005-12-08
Hello,
having just turned on my computer to browse some Ubuntu forums, a few seconds after turning it on, during the booting sequence, I heard the dialling up noise from the modem.  I did deactivate it before switching off yesterday.  I don't think it's supposed to do that.  Well, at least I don't want it to, and it hasn't done this before.  I know there will always be things going on in a computer that I don't know about, which it needs to run, but I'd rather they didn't end in enormous phonebills....
Is there anything I can do to stop it from automatically connecting (or attempting to)?
Cheers,
Lila;)

---

### Post by jimcooncat on 2005-12-08
I'm guessing dial-on-demand is set up, and the time synchronization command during the boot process is triggering it. Just a guess.

---

### Post by lila on 2005-12-08
[QUOTE=jimcooncat]I'm guessing dial-on-demand is set up, and the time synchronization command during the boot process is triggering it. Just a guess.[/QUOTE]

A-ha?  Sounds like a possiblilty, but how do I unset that? I've never come across it (I certainly didn't set it up, at least not intentionally...)  
Lila

---

### Post by Mustard on 2005-12-08
If you are using the 'Networking' to connect via dialup, then this will occur.  I initially used this when I first started using Ubuntu, but encountered the same issue as you.

I would install gnome-ppp using synaptic and configure the dialup connection using that, and then disable the dialup connection in your Administration>>Networking menu.

Alternatively you can read this HOW TO on configuring your dialup connection via the terminal and connecting via the terminal as well.

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Personally I prefer to use gnome-ppp

---

### Post by Zonkle on 2005-12-12
I had the same thing happened the other day .... but it doesn't happen always :???:  It happened about two time as I remember :???: . Doesn't happen every boot.

---

### Post by unisol on 2005-12-13
if you are using the networking app and you dont deactivate it this will happen

---

### Post by linuxguiri on 2005-12-29
[QUOTE=Mustard]If you are using the 'Networking' to connect via dialup, then this will occur.  I initially used this when I first started using Ubuntu, but encountered the same issue as you.

I would install gnome-ppp using synaptic and configure the dialup connection using that, and then disable the dialup connection in your Administration>>Networking menu.

Alternatively you can read this HOW TO on configuring your dialup connection via the terminal and connecting via the terminal as well.

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Personally I prefer to use gnome-ppp[/QUOTE]
Mustard, you're just the person I need to talk to! I had a similar train of thought after reading the [DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems") and successfully installed gnome-ppp. 

I can connect to my ISP with gnome-ppp but my internet applications don't seem to realize the computer's online. With the default ubuntu networking app this was solved by checking the "default internet connection" setting, but I can't find something similar in gnome-ppp? Any ideas, please?

---

### Post by Mustard on 2005-12-29
[QUOTE=linuxguiri]Mustard, you're just the person I need to talk to! I had a similar train of thought after reading the [DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems") and successfully installed gnome-ppp. 

I can connect to my ISP with gnome-ppp but my internet applications don't seem to realize the computer's online. With the default ubuntu networking app this was solved by checking the "default internet connection" setting, but I can't find something similar in gnome-ppp? Any ideas, please?[/QUOTE]

I would do a sudo pppconfig command in terminal and select 'change connection' to edit your current connection configuration, then go to the advanced options, and look for the default route setting.  Gnome-ppp is gui frontend for wvdial, and I am pretty sure it takes its setting from those created by the pppconfig command.

---

