---
title: "Ctrl-Alt-Del way to kill a process?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Viper Daimao on 2007-03-22
Hey guys,

I'm looking for some key bindings or how to set some up to bring up the system monitor, like how ctrl-alt-del brings up the task list in windows. Is there something that does this already? I just want something to do for when my laptop gets slow from running out of ram or something and I need to close something quickly to get it to respond.

---

### Post by mac.ryan on 2007-03-22
If I am not wrong Automatix2 ([www.getautomatix.com]("http://www.getautomatix.com")) can install you a small something that will bind system monitor exactly that way....

...another option is to add to one of your panes the "force quit" icon (right-click on the panel --> "add to panel" ). This way you can click on it, click on the window of the unresponsive programme, and... kill it!

I suppose there are at least another half dozen ways to do that, however.

---

### Post by aidanr on 2007-03-22
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Ctrl.2BAlt.2BDel_to_open_System_Monitor_in_GNOME)

---

### Post by chili555 on 2007-03-22
The grey-haired old linux geek way; in a terminal:```
sudo killall gaim
```Or whatever you want to kill. sudo killall ex-wife's lawyer.

---

### Post by jordanmthomas on 2007-03-22
You wouldn't need to use sudo to kill gaim though,
```
killall gaim
``` would be sufficient.
Even better would be
```
killall -SIGTERM gaim
```
which would let gaim close itself.

Just using killall basically doesn't let the program save its state before dieing, but sometimes it's necessary.

---

### Post by tns on 2007-04-24
I realize this is a really old thread, but I can't believe nobody suggested "top". Running top from the terminal brings up a live process monitor. It has keyboard commands, so if you hit "K", it will prompt you for the Process ID to kill.

---

