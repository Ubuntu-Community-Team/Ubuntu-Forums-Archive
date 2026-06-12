---
title: "A couple of questions with xubuntu"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-20
While trying to configure my auto-start applications, I have somehow managed to have nm-applet start up four times and conky two times every time I boot up. how do I change it to only one each?

Second, my desktop is, for some unknown reason, pure black. It doesn't matter whether or not I change the picture, it remains black. When I enable compiz fusion, the top 1/8th of the background image is visible as is the bottom 1/8th. The taskbar in compiz also allows me to see the background, but only where the taskbar is. The problem still occurs even if Conky is off.

If you don't understand and would like screenshots, just ask.

---

### Post by julian67 on 2008-02-21
If you're using Xubuntu Gutsy then nm-applet is already one of your autostarted applications by default, there should be no need to add it again to the list (which can be found Settings>Autostarted Applications. Try to remove all except 1 mention of it. (Did you install Xubuntu only or did you add the Xubuntu desktop after installing regular Ubuntu or Kubuntu?)

As for Compiz in Xubuntu Gutsy......it's a problem which is why it isn't part of Xubuntu by default. I loved using Beryl in Xubuntu Feisty, it worked brilliantly and used few resources, but Compiz in Ubuntu Gutsy is tied in very tight with Gnome and Metacity (the Gnome window manager) and I couldn't make it work satisfactorily in Xubuntu (problems with the window decoration and general performance).  I'm just using standard 2D desktop for Xubuntu Gutsy. Conky should work fine except you might not be able to have both conky and your desktop icons at the same time. Perhaps someone else can correct me if this is not the case. 

You can go back to allowing Xfce to manage the desktop by Settings>Desktop Settings and checking the box "Allow Xfce to manage the desktop" and hopefully you will soon be back at the normal Xfce desktop with icons visible for removable drives/media etc. I recall that if I run conky then these are not available, but you can add a removable drives applet to the panel.

---

### Post by intense.ego on 2008-02-21
Thanks, julian67, the last thing you mentioned (settings>desktop settings...) worked. I can see my desktop and all the icons, etc again. 

Still, when I boot up my computer 4 nm-applets and 2 conkys open. Could this be because  under Settings>Sessions and Startup Settings, "Launch Gnome Services on Startup" is enabled?

---

### Post by julian67 on 2008-02-21
> **intense.ego said:**
> Thanks, julian67, the last thing you mentioned (settings>desktop settings...) worked. I can see my desktop and all the icons, etc again. 

Still, when I boot up my computer 4 nm-applets and 2 conkys open. Could this be because  under Settings>Sessions and Startup Settings, "Launch Gnome Services on Startup" is enabled?

that shouldn't do it, I have the same enabled. Have a look in ~/.config/autostart and make sure there is only one instance of nm-applet and one of conky. Just delete any extra instances.

---

### Post by intense.ego on 2008-02-22
I looked in the folder you told me, and found only one instance of each, but found two instances of firestarter (a firewall), one that is 143b and one that is 159b. Which one do I remove?

Also, when I went to settings>autostarted applications I found something titled Network Manager that was unchecked and that "Network Manager (Network Manager Applet)" was checked. What does this mean?

---

### Post by julian67 on 2008-02-22
> **intense.ego said:**
> I looked in the folder you told me, and found only one instance of each, but found two instances of firestarter (a firewall), one that is 143b and one that is 159b. Which one do I remove?

Also, when I went to settings>autostarted applications I found something titled Network Manager that was unchecked and that "Network Manager (Network Manager Applet)" was checked. What does this mean?

I don't know how you've set up firestarter and am not suggesting any change. why not just remove all mentions of network manager applet from your autostarted list and see what happens.

---

### Post by intense.ego on 2008-02-22
I will do that and see what happens next time i reboot.

---

