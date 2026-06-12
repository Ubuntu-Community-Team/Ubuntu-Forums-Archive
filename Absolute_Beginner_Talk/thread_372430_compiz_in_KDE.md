---
title: "compiz in KDE"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-02-28
I had an attempt on compiz in KDE by installing the compiz, compiz-core and compiz-plugin.
Nonetheless, this doesn't really work out for KDE.

Once I reboot my computer, it loads the desktop which is blank. I suppose it has loaded KDE properly but it is just that the panels and all the icons are not shown.

Any help? If not, how can I remove compiz completely and have the same old desktop back? 
Doesn't seem to work out just by removing the package. Think there must be some conf file not being edited.

Advice please. thanks

---

### Post by in_flu_ence on 2007-02-28
I think the issue about the blank screen is that compiz (maybe also for beryl) that it doesn't work well with xorg. I am not sure if it actually edit the xorg.conf.

When you are at the blank screen, exit X by using ctrl-alt-backspace and get into the console login.

Then, I tried to use a backup copy (e.g. xorg.conf.1 from /etc/X11) to replace the current xorg.conf.

Reboot the computer.

It should restart and should have the KDE back. Nonetheless, for my case, I still have a laggy KDE and Xorg takes up basically 100% of my CPU.

While I have no idea where exactly is going wrong, i actually uninstall the entire kubuntu-desktop. Basically everything KDE in the system and

Do a sudo aptitude install kubuntu-desktop to reinstall the 100+ packages that has been deleted earlier on. 

Then, I have my entire system back as original without any trace of compiz.

Of course, there might be some experts out there who might be able to pin point to the specific places to delete rather than the entire KDE packages.

But nonetheless, I think this will offer a remedy to those adventurers who regret going for compiz prematurely.

Hope it helps. Now my Xorg is running just at 0.3% of CPU.

---

### Post by tonyr1988 on 2007-02-28
I can't speak from personal experience (I'm a Gnomie), but you may wanna try out Beryl:

[http://www.beryl-project.org/](http://www.beryl-project.org/)

It's a "fork" (offshoot) of Compiz, and I've heard that, as a general rule, it's got a lot fewer Gnome dependencies, meaning that it will run on KDE a lot better than Compiz. You can check out their wiki for more information about it.

---

### Post by in_flu_ence on 2007-03-01
I did in fact tried Beryl. Nevertheless, it doesn't worth the pain for now after the time spent on compiz.

I had attempted Beryl in the past (recently in fact). It makes my system lags quite abit. so i don't think I will want to venture into it again.

Tonyr: I have a similar desktop spec as yours. do you have beryl in your desktop. If so, maybe you can drop me a line on how you set up your Beryl and I will try to attempt it again when I have taken a long enough break fro my aftermath.:P

Cheers

---

### Post by in_flu_ence on 2007-03-31
I am lucky to get my 32bit gnome laptop working well with compiz (ATI X200 as graphic card).
Very smooth and stable. Tried booting and rebooting it and it just run.

I follow the guide ([http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/))

---

