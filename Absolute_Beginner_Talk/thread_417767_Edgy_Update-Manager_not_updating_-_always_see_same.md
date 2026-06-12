---
title: "Edgy: Update-Manager not updating - always see same updates - never install"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by flameproof on 2007-04-21
My problem in short:

Edgy: Update-Manager not updating - always see same updates - never install

I get the "updates waiting" notice after power up, I can see 5 (or so) updates waiting. I open update manager. Click update, get asked for password (have none), update proceeds, still can see the same updates waiting with no error message.

Same happens when I use the upgrade button for Feisty.

PS: seems I also can't start synaptic and some other programs. add programs also does not work.

Is there a general repair function?

Or will it all be fixed when I CD install Feisty? (Or will all my settings, and desktop then be gone?)

---

### Post by Happy_Man on 2007-04-21
Uh.... you have no password? You were definitely asked to set one when you installed, right?

---

### Post by bobplano on 2007-04-21
i don't know about your problem, the updates should install. were you able to install updates before? also:
> **flameproof said:**
> 

get asked for password (have none)

even though this is linux and it is more secure this is almost like inviting hackers onto your computer. you should have always have a password on computers that can connect to the internet. besides you were required to enter a password when you installed
> **flameproof said:**
> 
Or will it all be fixed when I CD install Feisty? (Or will all my settings, and desktop then be gone?)

if you use the alternate cd, i think you can "readopt" your home partition if you made one, allowing you to keep all your personal files in place (this doesn't mean it is foolproof, back up important info before doing anything like this .

---

### Post by flameproof on 2007-04-21
Password: I am not 100% sure. How do I set a root password (or re-set if forgotten?) How to set a user password?

>you can "readopt" your home partition

I have no partition, or just one partition. Will Feisty overwrite all data? I do have the data backed up. However, I prefer not to re-install all what I need.

Still, there is obviously a bug in my Update-Manager, is there any general repair routine?

---

### Post by robtg on 2007-04-21
When update-manager or Synaptic asks you for a password, type the password you use to log on to Ubuntu.

---

### Post by Happy_Man on 2007-04-21
When you first installed, it asked you to set up a username and password. What were they? That password is the only thing that can unlock Synaptic and Add/Remove..., etc. There is no root password in ubuntu for security reasons.

---

### Post by flameproof on 2007-04-21
There is no password set for the user. That PC is having only one user. When I switch on the PC the desktop opens with that user.

---

### Post by Happy_Man on 2007-04-21
Uh, yeah, same with me. But it still asks me for a password anyway...

---

### Post by bobplano on 2007-04-21
> **flameproof said:**
> There is no password set for the user. That PC is having only one user. When I switch on the PC the desktop opens with that user.

i assume that just means you did something to change the settings so you don't have to put in your password on booting up. that doesn't mean you don't have one. if you don't remember it you can make a new user but that uses sudo so it might not work

---

### Post by flameproof on 2007-04-22
OK, coming back to my initial question:  Is there a "repair" function?

Alternately: when I CD install Feisty - will my Thunderbird emails survive?

---

### Post by wirelessmonkey on 2007-04-22
Any "repair function" would require a password.  So, not per-se.  

If you reinstall from scratch, I don't think anything will survive, though it's technically possible, if you don't reformat. 

Open up a terminal.  Type passwd.  I think*** you can change it that way, though it may require you to enter your old password, which you don't seem to have.

It's always a good idea to keep track of your passwords, anytime one is asked for during the install/creation process.

---

