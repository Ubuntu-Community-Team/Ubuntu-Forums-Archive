---
title: "How to revert to original PPAs"
date: 2013-05-25
forum: Any Other OS
---

### Post by MaZaMo on 2013-05-25
Hey I installed some PPAs and now I forget which ones they are and I have a long list (looking on software sources). How do I know which PPAs are the important ones that come with the system? I would like to remove everything else.

---

### Post by HiImTye on 2013-05-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
ubuntu repos have either .canonical.com or .ubuntu.com domains

---

### Post by ibjsb4 on 2013-05-25
Ubuntu does not come with any installed PPAs by default.

---

### Post by MaZaMo on 2013-05-25
So i can remove all my PPAs? I use Elementary OS btw.

This is one: [http://ppa.launchpad.net/elementary-os/os-patches/ubuntu](http://ppa.launchpad.net/elementary-os/os-patches/ubuntu). It looks like something I shouldn't remove

---

### Post by MaZaMo on 2013-05-25
What if I do remove something important on accident, such as security updates. How do I get it back?

---

### Post by ibjsb4 on 2013-05-25
Just uncheck them using "software sources", that way you can easily reinstall any of them if so desired.

Edit: And yes, that Elementary PPA looks like something you would want to keep.

[URL="https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories"]https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories






[/URL]

---

### Post by deadflowr on 2013-05-25
I don't run Elementary, but if software sources is the same, then the PPA are all listed under 'other software'.
Browse that tab for your PPAs, and uncheck the ones you want to stop using.

---

### Post by MaZaMo on 2013-05-26
I'm having another problem. On software sources, under the updates tab, I can't check any of those updates in the list, such as important security updates.

---

### Post by Frogs Hair on 2013-05-26
To display all sources in the terminal PPA or otherwise use the following. ```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

This application is available for Ubuntu PPA management also. [http://www.webupd8.org/2012/10/y-ppa-manager-0092-released-with-new.html](http://www.webupd8.org/2012/10/y-ppa-manager-0092-released-with-new.html)

---

### Post by oldos2er on 2013-05-26
Moved to Other OS/Distro Support.

---

### Post by monkeybrain2012 on 2013-05-26
Well by removing the ppa from sources list you only disable it so you won't get further updates, but it won't remove software already installed from the ppa. If you want to downgrade the software to the original version along with dependencies you should install ppa-purge and then run it 

sudo apt-get install ppa-purge

sudo ppa-purge nameofppa

---

### Post by MaZaMo on 2013-05-30
Thank you! I reinstalled Elementary OS, and I'm going to try to be more careful next time.

---

