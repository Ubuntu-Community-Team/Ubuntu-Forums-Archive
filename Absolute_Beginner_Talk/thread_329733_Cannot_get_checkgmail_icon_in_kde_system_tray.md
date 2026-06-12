---
title: "Cannot get checkgmail icon in kde system tray"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by HomeViaChina on 2007-01-02
I am 100% new to Ubuntu. I'm trying to get checkgmail to work in the kde system tray but having no luck. I've installed it and linked it to the Autostart directory, it works in that it lets me know when I get emails but I can't get it to be in my system tray. All the other posts tell you how to do it in Gnome but I'm using kde, I like it better :) Any suggestions??

---

### Post by shanepardue on 2007-01-02
Try kcheckgmail. It's the KDE alternative.

---

### Post by HomeViaChina on 2007-01-02
Yeh i installed that too, got much the same prob, can't get it in the systray. Checkgmail seems to work better anyway... Still can't get it where it should be though, theres the "add to panel" option but that doesn't do what i want. I thought there'd be some easy method to do it but i just can't find it.

---

### Post by kogber on 2007-01-05
I use checkgmail in KDE, and have it autostart like this successfully:


```
kate ~/.kde/Autostart/start-checkgmail
```

Insert this into it:

```

#!/bin/sh
/usr/bin/checkgmail

```

Make it executable:

```
chmod +x ~/.kde/Autostart/start-checkgmail
```

checkgmail runs in the system tray, after it prompts me for my password (no way i'm saving it as plain text ).   You can run it manually in a console with "/usr/bin/checkgmail"

---

### Post by Marsolin on 2007-01-05
What problem are you having with [KCheckGMail]("http://linuxappfinder.com/package/kcheckgmail")?  I use it and it has been working great.

---

### Post by orb9220 on 2007-01-05
Did you click and check use custom mail icons in prefs. I had to manually check those.
They are there is system tray area of the prefs box.

---

### Post by HomeViaChina on 2007-01-07
Thanks for all the help everyone, I didn't realize that the system tray is an applet! Something so easy to overlook, I just thought it would automatically appear in the panel ](*,)  The advice helped to work it out tho thanx!

---

### Post by NealeT on 2007-01-07
I´m having a similar problem in Ubuntu.  I´m a newbie but I´ve run Ubuntu on a previous machine and never had this problem.  I installed and ran [COLOR="Red"]**checkgmail**[/COLOR] but it runs in its own window.  I can´t figure out how to get it on the panel.  :confused: 
Thanks in advance.

---

### Post by HomeViaChina on 2007-01-08
Are you using kde or gnome? Or some other one that I don't know:)  On kde you have to right click on the panel and choose add applet to panel. Then scroll thru and find system tray and add it. Then every time it runs it should be there. Not sure on gnome. The code above from kogber works to get it to auto start on login. 
Hope that helps a little

---

### Post by orb9220 on 2007-01-08
Don't confuse the applet with the command driven one. There is gmail-notify which is th one that has a entry in menu's under internet. And there is checkgmail which is not the same. 

But to answer your question after checkgmail is installed go to systems>prefs>sessions>
and in startup programs click add and enter:  checkgmail that's it be sure to check on custom icons to show in the tray.

---

### Post by NealeT on 2007-01-08
Thanks, everyone.  I'm running gnome.  and i actually already have it set up to run on startup and have checked the custom icons but it still will not load in the panel.  i installed gmail-notify and it would not load in the panel either (although i've previously run it on Ubuntu and had no problem).  i was thinking about it and i'm wondering if it's because i have two desktops set up on my computer (one runs to my TV).  do you think this could have anything to do with it?
Thanks again.

---

### Post by Mguel on 2007-07-25
> **kogber said:**
> checkgmail runs in the system tray, after it prompts me for my password (no way i'm saving it as plain text ).

to make it save the password encrypted on kubuntu I needed to do:

```
sudo perl -MCPAN -e 'install Crypt::Simple'
```

(if you run checkgmail from a terminal you will see warnings of missing modules for saving the password encrypted)

Cheers,
Mguel

---

### Post by espmartin on 2007-08-01
> **orb9220 said:**
> Don't confuse the applet with the command driven one. There is gmail-notify which is th one that has a entry in menu's under internet. And there is checkgmail which is not the same. 

But to answer your question after checkgmail is installed go to systems>prefs>sessions>
and in startup programs click add and enter:  checkgmail that's it be sure to check on custom icons to show in the tray.

Hello,
I too am VERY new to Ubuntu. I've followed these instructions, but can't find CheckGmail ANYWHERE!!! I've installed it via instructions.

> sure to check on custom icons to show in the tray
So where do I find this option?

Sorry and God Bless,

Martin

---

