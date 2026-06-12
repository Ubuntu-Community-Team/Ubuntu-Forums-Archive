---
title: "Does anyone have the problem of disappearing windows rotating the XGL Cube?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2006-10-03
Everytime I rotate the cube, the windows are sometimes missing or hidden, I have to keep clicking so that they reappear. It's annoying, I don't know what it is but only happens when I use the shortcut keys to rotate cube or select a task from the panel below. This does not happen when I manually rotate the cube using the mouse.

Could it be the shortcut keys that are messing things up?

---

### Post by tribaal on 2006-10-03
I have the same problem.

I noticed the windows are visible again when I switch to and intermediate desktop. That's to say, when I switch to the target window when it's not showing up in the Desktop viewer applet. :)

It's pretty weird and annoying, but hopefully it'll be fixed once Compiz becomes more stable (it's still pre-release software).

Hope this adresses your point.

- trib

---

### Post by Bagboy23 on 2006-10-03
> **tribaal said:**
> I have the same problem.

I noticed the windows are visible again when I switch to and intermediate desktop. That's to say, when I switch to the target window when it's not showing up in the Desktop viewer applet. :)

It's pretty weird and annoying, but hopefully it'll be fixed once Compiz becomes more stable (it's still pre-release software).

Hope this adresses your point.

- trib

Thanks for the reply, but I have noticed that on my friends laptop with Suse 10.1, Windows just naturally stick and are available. So it seems that not everyone is having this problem.

---

### Post by Bagboy23 on 2006-10-03
> **Bagboy23 said:**
> Thanks for the reply, but I have noticed that on my friends laptop with Suse 10.1, Windows just naturally stick and are available. So it seems that not everyone is having this problem.

It seems to be fixed using this:

[http://forum.beryl-project.org/topic-4564-maximized-windows-disappear-when-rotating-with-window](http://forum.beryl-project.org/topic-4564-maximized-windows-disappear-when-rotating-with-window)

Please report back and let me know as I was asked to file some sort of a bug report.

---

### Post by mcduck on 2006-10-03
That was a bug in the latest and last version of Compiz-Quinnstorm. You'd better move on to using Beryl now (as Compiz-Quinnstorm is no more), and that will fix your problem too :) 

Here's the quick & simple instruction for updating from Compiz-Quinnstorm to Beryl:
> Quick installation instructions for the QuinnStorm repository:

People using the QuinnStorm repository have to install the following packages, and add beryl-manager to their list of startup programs (replacing compiz-manager or compiz-start if you used it before)

xserver-xgl libgl1-mesa libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes 

If you have any own cgwd themes you should export them first, and then rename them from xxx.cgwdtheme to xxx.emerald, so that you can then import them to EmeraldThemer (new name for compiz themer)..

---

### Post by Bagboy23 on 2006-10-04
Problem still exists even in Beryl. Although now it doesn't disappear when rotating the cube but it does disappear when selecting tasks from gnome panel.

---

