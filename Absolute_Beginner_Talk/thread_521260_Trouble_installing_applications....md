---
title: "Trouble installing applications..."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-08-09
Oi. I am a bit frusterated. I had to format Ubuntu because ever since I install Wine the system went totally crazy.

Now I'm having trouble installing certain programs that were working fine on the old install.

Okay... Pidgin and CheckGmail.

I got them both from getdeb.net, the Pidgin-data file is already install, but when I actually try to do the application I get the message  

```
error dependency is not satisfiable: libavahi-compact-how|0
```

And check Gmail says... ```
error dependency is not satisfiable: libgtk2-trayicon-perl
```

Also, how do I remove GAIM?

---

### Post by splintercellguy on 2007-08-09
Remove the packages you got, then get the Pidgin debs from there: [http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/](http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/)

---

### Post by Cheese Roller on 2007-08-09
I am very new to Linux. How do I remove what I have, I know I use Synaptic, but HOW do I use it?

---

### Post by splintercellguy on 2007-08-09
Search for pidgin, then click on the check box for it and select Mark for Removal.

---

### Post by Cheese Roller on 2007-08-09
Alright, what a bout getting rid of GAIM, and installing CheckGmail

---

### Post by splintercellguy on 2007-08-09
For Pidgin, this might help: [http://ubuntuforums.org/showthread.php?t=474071](http://ubuntuforums.org/showthread.php?t=474071) CheckGmail I'll have to lookup.

---

### Post by sailor2001 on 2007-08-09
pidgin is just an alias for gaim (legal issues with gaim) checkgmail is in synaptics

---

### Post by Cheese Roller on 2007-08-09
I'm getting Pidgin to have the latest version.

---

### Post by Cheese Roller on 2007-08-09
Okay guys, I found an alternative to check g-mail.

But yeah, I still have trouble understanding Synaptic.

How do I remove what I have already installed with Pidgin, and how do I remove the old version, Gaim?

If I recall there is a code to remove all instances of GAIM.

---

### Post by splintercellguy on 2007-08-09
If you do not like Synaptic, there is always the command-line:

sudo apt-get remove <package name>

Follow the directions in the thread I mentioned; there is a dependency bug with the Gaim package on Ubuntu which the thread tries to workaround.

---

### Post by Cheese Roller on 2007-08-09
what do you mean?

Is there more to it than ```
sudo apt-get remove gaim
```?

---

### Post by splintercellguy on 2007-08-09
Yes. There is a bug with the gaim package that causes you to also remove ubuntu-desktop when you remove gaim. The thread I pointed you to works around this by supplying a transition package. For most other packages, sudo apt-get remove <package> works fine.

---

### Post by Cheese Roller on 2007-08-09
Well, you forgot that I already installed a part of pidgin. How do I get rid of it?

---

### Post by splintercellguy on 2007-08-09
ubuntu-desktop is a metapackage that encompasses basically GNOME and some other Ubuntu packages. From [http://ubuntuforums.org/showthread.php?t=474071](http://ubuntuforums.org/showthread.php?t=474071), you don't remove gaim per se because of the dependency bug. Instead, you install the Pidgin deb, and then install the Gaim transitional package to effectively "remove" it.

---

### Post by Cheese Roller on 2007-08-09
AH! I think I got it okay I will try this replacer thing!

---

### Post by Cheese Roller on 2007-08-09
Okay also Evolution Mail has a dependency too, how do I remove that?

---

### Post by splintercellguy on 2007-08-09
Can you post the terminal output?

---

### Post by Cheese Roller on 2007-08-09
Okay, I did that thing to replace GAIM with Pidgin, it said to install it after I installed Pidgin.

Now GAIM is just updated. What gives? Do I need to type the code to remove GAIM now?

---

### Post by splintercellguy on 2007-08-09
No, leave gaim as is. The pack you installed is a dummy package which points to Pidgin to work around the bug.

---

### Post by Cheese Roller on 2007-08-09
> **splintercellguy said:**
> No, leave gaim as is. The pack you installed is a dummy package which points to Pidgin to work around the bug.

So I DO have to keep GAIM?

When I search for GAIM in I get results.

---

