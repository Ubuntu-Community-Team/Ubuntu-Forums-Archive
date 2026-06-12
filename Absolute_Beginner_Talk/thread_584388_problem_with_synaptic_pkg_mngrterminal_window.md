---
title: "problem with synaptic pkg mngr/terminal window"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by halligan46 on 2007-10-20
While trying to get googleearth to work, unsuccessfully, I found the following message when I opened synaptic package manager.  Also in add/remove programs.

FAILED TO CHECK FOR INSTALLED AND AVAILABLE APPLICATIONS

THEN FOLLOWS;  THIS IS A MAJOR FAILURE OF YOUR SOFTWARE MANAGEMENT SYSTEM. PLEASE CHECK FOR BROKEN PACKAGES WITH SYNAPTIC,CHECK THE FILE PERMISSION AND CORRECTNESS OF THE FILE etc/apt/sources.list and reload the software information with; SUDO APT-GET UPDATE AND SUDO APT-GET INSTALL-F.

I can't figure out what to do since I am unable to open Synaptic or ad/remove software.  I've tried entering the above lines in the terminal with no success, I must be missing something.

If any any one is able to steer me in the right direction I would be most greatful

thanks in advance

Jimthomas

---

### Post by barkej on 2007-10-20
What response do you get when you type ```
SUDO APT-GET INSTALL -F
``` in the terminal?

---

### Post by halligan46 on 2007-10-21
Thanks for your response.
 When I enter   sudo apt-get install -f  the response is as follows

E: typ'<!DOCTYPE' is not known on line 1 in sourcelist /etc/apt/sources.list.d/medibuntu.list

E: the list of sources could not be read

I admit I'm stumped because I don't know to correct the problems that a causing the message.  I am unable to use synaptic or add/remove since there is a window with a red stop sign.

Thanks again

Jimthomas

---

### Post by barkej on 2007-10-22
Can you post the contents of  /etc/apt/sources.list.d/medibuntu.list ?

---

### Post by halligan46 on 2007-10-22
Thanks for your response

 When I enter /etc/apt/sources.list.d/medibuntu.list the following message shows up.

bash:/etc/apt/sources.list.d/medibuntu.list : permission denied.

Apparently I have no other issues until I try to enter add/remove or synaptic when a warning window appears.
Please forgive me if I am repeating previous posts

I am considering removing and reinstalling feisty or would that do more harm than good?

Thanks again for your patience

Jimthomas

---

### Post by barkej on 2007-10-22
Reinstalling will not hurt anything.
Try this in the terminal
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and post back what you have there.

---

### Post by halligan46 on 2007-10-22
Hello  again  As you suggested I found the following

A new window called medibuntu.list(/etc/apt/sources.list.d) gedit
  This seems to state that this is not supported and my be illegal software to use in certain countries.

To be honest I think I am in way over my head, I think I might be better off to remove and reinstall feisty.  That should give me a clean start hopefully.

I appreciate your patience and your advice

Thanks again

Jimthomas

---

### Post by halligan46 on 2007-10-29
BARKEJ

     Thanks for your help with my error messages.  I finally just reinstalled feisty and all is working well.  I was also able to take the opportunity to fine tune a few other things as well.
    Again you all on the forum make this experience much easier

Thanks again  

Jimthomas

---

