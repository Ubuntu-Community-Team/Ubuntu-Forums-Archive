---
title: "getting GNOME to load at startup"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by dhamilton on 2008-04-05
I was messing around with the sessions manager, and turned off the automatic load of gnome at startup.

 I then decided that I wanted gnome to load at the start as per usual. However, the entry had disappeared from the startup sessions options.

So I created a new one with "startx" as a command, but that didn't work. Then I tried "gnome-session" which also didn't work. 

So what am I doing wrong? 

Thanks in advance.

---

### Post by billgoldberg on 2008-04-05
> **dhamilton said:**
> I was messing around with the sessions manager, and turned off the automatic load of gnome at startup.

 I then decided that I wanted gnome to load at the start as per usual. However, the entry had disappeared from the startup sessions options.

So I created a new one with "startx" as a command, but that didn't work. Then I tried "gnome-session" which also didn't work. 

So what am I doing wrong? 

Thanks in advance.

You could reinstall the "ubuntu-desktop".

That should fix things.

---

### Post by dhamilton on 2008-04-05
> You could reinstall the "ubuntu-desktop".

As per your suggestions I tried reinstalling gnome.

```

sudo apt-get --purge remove ubuntu-desktop
apt-get install ubuntu-desktop

```

However this did not solve my problem. I tried the same with gnome-session, which was of no use either.

Thanks for the prompt reply though. Do you have any other ideas?

---

