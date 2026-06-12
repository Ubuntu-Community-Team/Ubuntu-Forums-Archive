---
title: "changing desktops"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by RJ Hythloday on 2008-02-25
So I've searched and can't find the answer to this.

I installed edubuntu because I want the apps that come installed in it.

But I wan't fluxbox for the desktop mgr. It's for a kids pc w/ 900mhz 128ram.

I've installed xdm for the display mgr.

I've tried restarting and restarting x but I've not seen an option to choose a window mgr.

Could I just remove the edu desktop? and would it then start w/ fluxbox? And all the edu apps still be available in the menu?

tia for any help.

Bob

---

### Post by davec64 on 2008-02-25
On the Login screen, you've got an Options button, click on this and under Sessions you'll find a list of Managers you've installed. Select the one you want!
All the best!
I don't know about removing the edubuntu desktop, I suspect if you try and remove this a lot of libraries required for the apps to run may be removed. Perhaps someone with more knowledge could answer this point?

---

### Post by RJ Hythloday on 2008-02-25
For the x login screen all I get is snow w/ a text bar in the middle.

asks for username

password

logs in to edu-desktop

Am I doing something wrong?

---

### Post by davec64 on 2008-02-25
Ahhh, now I'm lost!
With a standard Ubuntu login you get the Options button in the bottom left hand corner.

Sorry, I'm not sure where it would be in Edubuntu!

---

### Post by RJ Hythloday on 2008-02-25
I think it's because I added xdm, I installed it because it's supposed to be lighter than gdm.

could I just sudo apt-remove edubuntu-desktop? and still keep the apps?

---

### Post by davec64 on 2008-02-25
I honestly don't know.

If it was me I would back everything up and have a go, but then again I'm quite happy to take the chance!
My own perverse logic says that you'd probably be ok, but somehow you would want your other window manager to become the default. If no other window manager is installed I think you'd end up with a full linux installation at the command prompt.

If that is the case you could use apt-get to install a window manager.

I don't think you've got your code quite right, I think it's probably:

sudo apt-get uninstall

or sudo apt-get remove

apt-get being the programme and unistall/remove being the switch.

Sorry I couldn't be more help!
Best of luck with which ever option you choose.

As a passing thought, it might be worth starting a new thread and asking the question again. People tend to look for threads with zero replies to give advice to.

All the best!

---

