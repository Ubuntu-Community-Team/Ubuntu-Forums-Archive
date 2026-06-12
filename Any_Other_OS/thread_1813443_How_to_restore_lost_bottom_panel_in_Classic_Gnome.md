---
title: "How to restore lost bottom panel in Classic Gnome"
date: 2011-07-27
forum: Any Other OS
---

### Post by rewyllys on 2011-07-27
I've accidentally lost the bottom panel on my desktop.  I'm using Linux Mint 11 Main, which is essentially Ubuntu 11.04 with Classic Gnome.  

I've tried re-installing gnome-panel, using the Synaptic Package Manager, but this failed.

So I'd appreciate any and all suggestions as to what to do to restore the bottom panel.

Thanks in advance.

---

### Post by era86 on 2011-07-27
Do you still have the top panel?  I believe you can just right-click and say "New Panel...".  Then you just have to restore all your icons and such by right clicking the new panel and going to "Add to Panel...".

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-add-more-panels-to-your-ubuntu-desktop/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-add-more-panels-to-your-ubuntu-desktop/)

---

### Post by westie457 on 2011-07-27
> **rewyllys said:**
> I've accidentally lost the bottom panel on my desktop.  I'm using Linux Mint 11 Main, which is essentially Ubuntu 11.04 with Classic Gnome.  

I've tried re-installing gnome-panel, using the Synaptic Package Manager, but this failed.

So I'd appreciate any and all suggestions as to what to do to restore the bottom panel.

Thanks in advance.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

I know this works on the top panel. Maybe it will work for the bottom one as well.

---

### Post by rewyllys on 2011-07-27
> **era86 said:**
> Do you still have the top panel?  I believe you can just right-click and say "New Panel...".  Then you just have to restore all your icons and such by right clicking the new panel and going to "Add to Panel...".
That did the trick!  Many thanks.:popcorn:

One more question, please:  What is the name of the applet that shows, and enables moving among, two or more desktops?

Answering my last question:  It's the Workspace Switcher.

---

### Post by uahmed on 2012-05-11
> **westie457 said:**
> ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```I know this works on the top panel. Maybe it will work for the bottom one as well.


Hi i lost my bottom panel and when i run your code i lost my other alone panel too :P . so please dont run that i find this solution 

run these command on terminal 

[INDENT]gconftool-2 --shutdown
 rm -rf ~/.gconf/apps/panel
 pkill gnome-panel
[/INDENT]

---

### Post by pbhill on 2012-09-01
That works! Thanks.

---

