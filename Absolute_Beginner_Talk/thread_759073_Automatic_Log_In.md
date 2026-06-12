---
title: "Automatic Log In"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by wavemaker on 2008-04-18
Gooday all. I have had a look around and can't seem to find what I am looking for. [I] am the only user on this puter and it's an experimental box, so nothing important on it. I have been using the auto log-in for a few weeks now and all was well. However it now no longer works. I may have changed a setting in the log-in window drop down box but I'm not sure. What are the original settings in this area.? Whenever I tick the "Enable auto log-in" box it unticks its self when I close the box. Bit of a mystery but no-one is going to die if I can't sort it. Any help appreciated. Regards, James.

---

### Post by racoq on 2008-04-18
> **wavemaker said:**
> Gooday all. I have had a look around and can't seem to find what I am looking for. [I] am the only user on this puter and it's an experimental box, so nothing important on it. I have been using the auto log-in for a few weeks now and all was well. However it now no longer works. I may have changed a setting in the log-in window drop down box but I'm not sure. What are the original settings in this area.? Whenever I tick the "Enable auto log-in" box it unticks its self when I close the box. Bit of a mystery but no-one is going to die if I can't sort it. Any help appreciated. Regards, James.

Try this in the console:

```

gksudo gedit /etc/gdm/gdm.conf-custom

```

find the following lines

```

[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

```

replace with this (or add these lines if the previous configuration was not available)

```

[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=true
AutomaticLogin=your_user_name

```

I think this will help

---

### Post by zvacet on 2008-04-19
**System>admin>login window>security tab**>you will find it there(dropdown menu with user names).

---

### Post by wavemaker on 2008-04-19
Thanks for that. Will give it a burl soon, when I go back to Ubuntu, I have Mandriva up at the moment.

---

