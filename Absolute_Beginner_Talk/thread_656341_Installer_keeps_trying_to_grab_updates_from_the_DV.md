---
title: "Installer keeps trying to grab updates from the DVD"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by e30drift on 2008-01-02
I installed 7.10 from a DVD and when I go to use the Update Manager, it says that there are no updates, when I feel (from past experience) that it should be pulling it from the internet.  Using the Package manager, I tried to enable the custom settings from Compiz, but it will not show Emerald or Compiz-Manager.  

I tried following a tutorial on HowToForge.com and was greeted with errors about saying "deb" was not a command...  strange.


Is there a way to switch the updates from the DVD to the internets?

---

### Post by phr0ze on 2008-01-02
Open system->admin->software sources.
Check off all the boxes except for source code on the ubuntu software page.
Uncheck the CD rom selection because it's more of a pain to find the CD than to download it. 

Click the updates tab and check the 'important security updates' and 'recommended updates' boxes.

Close the window and run update manager.

---

### Post by LowSky on 2008-01-02
yes go to system> admin> software sources, turn off cd

---

### Post by e30drift on 2008-01-02
ok, so, im a noob at this...

I figured it out and I'll post the solution for future noobs such as myself to regain my dignity.

Under System>Administration>Software Sources 
uncheck the "Installable from CD/DVD" and then check off what you want downloaded from the internet. Go to the next 2 tabs and do the same.

Hit "Close" and then wait for Ubuntu to query all available updates from the internet, download then and then you will have to manually launch the update notifier from the top right and initiate the installation.


[edit]  damn you guys are QUICK!  just say the replies to my thread!
This is now my favorite forum!!

Thanks to you 2 who replied back!

---

