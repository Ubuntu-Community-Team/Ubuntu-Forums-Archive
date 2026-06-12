---
title: "No borders/menus in gutsy"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2007-10-14
I have tried everything I could find, I have put the line in xorg.config, I have tried running compiz --replace -c emerald &. I cannot get borders working with compiz, I also cannot get beryl-manager to install. Is there some other way to get this issue corrected? It says that it cannot load the plugin: Emerald, which i have installed and have 0.3.0ish?

---

### Post by Squizzle on 2007-10-14
Detailing your graphics card or chipset will likely help people help you and assist in finding a driver or solution :)

---

### Post by ThrobbingBrain66 on 2007-10-14
> **mtgrocks04 said:**
> I have tried everything I could find, I have put the line in xorg.config, I have tried running compiz --replace -c emerald &. I cannot get borders working with compiz, I also cannot get beryl-manager to install. Is there some other way to get this issue corrected? It says that it cannot load the plugin: Emerald, which i have installed and have 0.3.0ish?

What are you trying to run...Beryl or Compiz Fusion?

Beryl isn't developed or supported anymore.  Did you use any 3rd-party repos to install that may be conflicting with Gutsy's default packages?

---

### Post by mtgrocks04 on 2007-10-15
I have an Intel i810 chipset, I am using compiz fusion as it is the default for Gutsy. I have emerald installed but I do not have borders on my windows.

---

### Post by entwisi on 2007-10-15
I originally had this issue when libdecorator wasn't installed correctly. try re-installing it. I also had to use compiz --replace ccp & to get it running properly on my Feisty install

---

### Post by Amol_Karmarkar on 2007-10-25
Try using the emerald window manager. To do this you need to install emerald

sudo apt-get install emerald

Then in the Compiz Settings utility click on the window decoration icon and add the following in the command line field:

emerald --replace

This enables the borders, ensure the following plugins are also enabled :

Move Window and Place Windows

You can change the border appearance by going to the emerald theme manager under System->Preferences..

---

### Post by TadH on 2007-10-25
You probably already did this but, system>preferences>apearance>make sure u have extra visual effects on, or custom which ever is there.

---

### Post by leona on 2007-10-28
I've got this problem.
I have Gustly which I upgraded from Fiesty.
Have enabled the desktop effects, and now I find I have no window borders, min, max and close menus options.
I have a Nvidia chipset, using the  New nvidia drivers via the restriced driver component.
How do I get my borders back?
Thanks.

Edit update, solved after reading this post. 
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

**When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"**

---

