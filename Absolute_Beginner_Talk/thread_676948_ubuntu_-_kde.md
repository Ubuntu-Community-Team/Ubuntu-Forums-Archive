---
title: "ubuntu - kde"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Lord DarkPat on 2008-01-24
I'm not able to type the letter before "y". How do I install KDE on <letter before "y">ubuntu?

---

### Post by aysiu on 2008-01-24
> **Lord DarkPat said:**
> I'm not able to type the letter before "y". How do I install KDE on <letter before "y">ubuntu?
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` Log out, select the session as KDE, and log back in again.

---

### Post by LowSky on 2008-01-24
> **Lord DarkPat said:**
> I'm not able to type the letter before "y". How do I install KDE on <letter before "y">ubuntu?

you can't type the letter "t"? but you've done it 8 time already....LOL

---

### Post by aysiu on 2008-01-24
> **LowSky said:**
> you can't type the letter "t"? but you've done it 8 time already....LOL
The letter *x*

---

### Post by Lord DarkPat on 2008-01-24
are there any side effects?

---

### Post by aysiu on 2008-01-24
> **Lord DarkPat said:**
> are there any side effects?
Yes.

Your KDE menu will be cluttered with Xfce applications, and your Xfce menu will be cluttered with KDE applications.

When you log out of KDE and log back into Xfce again, you may notice a random something.desktop file appear in your desktop folder in the Thunar file browser.

Even though *aptitude* should allow you to remove KDE completely if you don't like it, there may be a few residual KDE packages after you remove KDE.

Your boot splash screen may say *Kubuntu* on it.

---

### Post by Lord DarkPat on 2008-01-24
will the problem be solved if I uninstall ubuntu desktop?
And will KDM be installed as well? GDM gives me the creeps

---

### Post by aysiu on 2008-01-24
> **Lord DarkPat said:**
> will the problem be solved if I uninstall ubuntu desktop?
And will KDM be installed as well? GDM gives me the creeps
Which problem? The *x* key not working on your keyboard? And are you using Ubuntu or Xubuntu? Earlier, you seemed to indicate you were using Xubuntu, but now you're saying you might uninstall Ubuntu.

If you install *kubuntu-desktop*. it will install KDM as well and give you the option to use KDM or stick with GDM.

---

### Post by Lord DarkPat on 2008-01-24
will the <before "y">ubuntu interfeerence prblm be solved???
you said that it will be cluttered. I mean that prblm. My <before "Y"> key is broken

---

### Post by aysiu on 2008-01-24
> **Lord DarkPat said:**
> will the <before "y">ubuntu interfeerence prblm be solved??? I don't know.

> you said that it will be cluttered. I mean that prblm. Yes, you can always uninstall the applications that are cluttering your menu.

---

