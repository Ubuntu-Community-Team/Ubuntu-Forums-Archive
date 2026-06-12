---
title: "Installed Brightside, but where is it now?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by _Pieter_ on 2007-06-03
Hi all!

I installed Brightside by typing into the terminal: "sudo apt-get install brightside".
However, the program does not show up in any of the menus, and when I try to run 'brightside' from the 'run application' window, it does nothing and when I type 'brightside' in a terminal it says 'Deamon already running, exiting...'.

What's the deal?

---

### Post by noodle43 on 2007-06-03
go into your terminal and type 
sudo dmesg | tail 
post results

---

### Post by _Pieter_ on 2007-06-03
Thanks for your reply, Noodle, but I already figured it out: when I type 'brightside-properties' in a terminal window, the program pops up and I can configure the options. But thanks anyway!:)

---

### Post by Sweet Mercury on 2007-06-04
> **_Pieter_ said:**
> Hi all!

I installed Brightside by typing into the terminal: "sudo apt-get install brightside".
However, the program does not show up in any of the menus, and when I try to run 'brightside' from the 'run application' window, it does nothing and when I type 'brightside' in a terminal it says 'Deamon already running, exiting...'.

What's the deal?

I installed, then uninstalled that package. But if I remember correctly, under GNOME, go to **System --> Preferences** and there should be an option called **Screen Actions**; you can configure it there.

---

### Post by os.getlogin on 2007-06-11
> **Sweet Mercury said:**
> I installed, then uninstalled that package. But if I remember correctly, under GNOME, go to **System --> Preferences** and there should be an option called **Screen Actions**; you can configure it there.

This helped.  Why did you uninstall?

---

