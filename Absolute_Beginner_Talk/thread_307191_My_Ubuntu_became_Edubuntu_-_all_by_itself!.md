---
title: "My Ubuntu became Edubuntu - all by itself!"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Voldmer on 2006-11-26
I installed Ubuntu. Succesfully, too. And I used it for a couple of days. Then, suddenly yesterday, when being shut down for the night, it brought up a "Edubuntu" logo on the screen, instead of the Ubuntu" one. And today, when powering the system up, it likewise proclaimed to be "Edubuntu".

My questions are two-fold:

1. How can something like that happen?

2. Does it matter at all?

Best regards,

Stefan W. Christensen
Unashamed Linux  newbie

---

### Post by meng on 2006-11-26
I can't answer Q1. I know that if I install Ubuntu, then install kubuntu-desktop or xubuntu-desktop, the startup/shutdown logo changes, and doesn't necessarily change back if you subsequently uninstall those desktops.

I can answer Q2 though. If it's just the logo at startup and shutdown, and nothing else seems to have changed (i.e. you still have GNOME and all the applications that were installed before) then it doesn't make any difference. There must be a simple way to change that logo, but I don't know it!

---

### Post by DoorGunner on 2006-11-26
The problem is that every time you add a desktop. The new desktop theme will want to take over. I had this probelem with kde giving me Kubuntu start up splash.

Easy enough Fix. 

all you should have to do is this
$sudo update-alternatives --config usplash-artwork.so
then just press the option you want to keep.

when you are adding extra desktops it is an idea to save your ubuntu usplash somewhere else. Kde was particularly aggressive and copied over my ubuntu. 

Your usplash-theme-ubuntu.so is located in /usr/lib/usplash/

:)

---

### Post by Voldmer on 2006-11-26
Thanks for the advice; just followed the "sudo" recommendation, and so far that seems to have been the right way; it gave me two options, Ubuntu and Edubuntu, the latter of which was set to be the default. Changed it back, but for now nothing has happened; I suspect that the change will manifest itself when the system is turned on next time.

Best regards,

Stefan W. Christensen

---

### Post by DoorGunner on 2006-11-26
Yep. It should go back on restart. If it doesnt that means that edubuntu over wrote the .so.....

If this happens let me know...

---

### Post by kiyometane on 2006-11-26
Your ubuntu became edubuntu.
One time i boot ubuntu but i was logged into windows!
I dont know how that happened

---

### Post by Aualin on 2006-11-26
run sudo initramfs -k all -u after update-alternatives

---

