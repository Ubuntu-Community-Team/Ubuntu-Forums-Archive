---
title: "unable to login"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by spandon on 2006-01-29
Hi,
Having tried the Live cd's, decided to install Kubuntu to a hd with windows XP already installed on it.
I installed Kubuntu by utilising the "expert" method, everything went well and I left the Host Name as was, entered a Domain Name, and a Shadow Passwords/Root Password noting down exactly what I had written and case during the installation.
On testing after the installation, found I had a dual boot system with Windows and Kubuntu, tested Windows from the menu - perfect, then tried Kubuntu, this time Kubuntu loaded no problem but then refused to accept a user name,  used hostname (ubuntu) then tried my domain name using my root password, but system refuses to accept any combination of above.
Can anyone help?
If it means a reload, could anyone help in how and where to enter username and password during installation?
Any assistance would be appreciated.
Thanks for looking.
Don
spandon

---

### Post by jrib on 2006-01-29
Can you login as root maybe?

---

### Post by spandon on 2006-01-29
Hi Jason,
This is my first venture into Linux, could you explain how do I log into Root?
Thanks
Don

---

### Post by jrib on 2006-01-29
Just user the username 'root' and your root password.  You say you did an expert install, does that mean that right now you are at a terminal prompt?  Is this what you wanted to do you want an environment similar to windows with a gui and stuff (called X)?

[edit]if you can login with root, you should immediately create a user account and use the user account instead.  I can explain to you how to setup sudo (this will let you do administrative stuff with your regular user account) for that user after you do that if this works. I'll go ahead and subscribe to this thread, so you can just reply here.  Good luck.

---

### Post by Iowan on 2006-01-29
When the system boots up, you should have a few seconds to choose an option from the GRUB menu.  The first one (on my system) is the standard boot, the second is a rescue/single-user/root  boot.  If you choose that option, you should be able to add a user... that user will need to be added to SUDOERS.  But first things first - see if you can get to the root boot and add the user.

---

### Post by spandon on 2006-01-30
Hi,
Many thanks for your responses.
I have reloaded kubuntu three times today, each time I have now got into the programme having added another user account during installation.
When I try to do any administrative  work, I am asked for a a password, I enter the Shadow  or the user account I am logged into password, but each time I get "login failed".
The last installation, I left the Shadow password blank, but still system would not accept my user account password.
Would appreciate any help you can give to resolve this problem, but would appreciate a non technical reply as I am a complete newbie to the command line.
Many thanks
Don

---

### Post by jrib on 2006-01-30
It would help if you are a little more specific.  

1. What `administrative work' exactly?  What did you type in or what did you click on?
2. Do you have root access? (when you tried to login with root did it work?)
3. Did you do a server install?

What do the following return  (paste error messages if they occur, otherwise just paste the output):
In a terminal (applications menu -> accessories -> terminal),

4. sudo echo hi
5. groups
6. su (this will login you in as root, so try the root password if you set one)

---

### Post by spandon on 2006-01-31
Hi Jason,
Many thanks again for your response last night.
Tried to use your sugestions, but realised that you must be using ubuntu?
To cut to the chase, got fed up messing about with kubuntu, and installed ubuntu instead, this time using the default setup instead of the expert setup.
Once installed, everything worked right from the start, had adminastrative rights straight away and able to download the 50 updates reported and install them all from the menu without any need for the terminal.
I then used the terminal to install and run Automatix by following advice given in another thread.
The only fly in the ointment so far, is that my printer (Oki C3200) has no Linux driver and manufacturers website has no alternative.
Do not know if Kubuntu would have worked any better by using the default setup route as I did with ubuntu, but have no wish to find out now everything is working.
The dual Boot also works well between XP and ubuntu, although the selections in the boot menu is a little long winded due to the kernel upgrade.
On the whole am very pleased I stuck with it and didn't give up.
Many thanks for your assistance
Don

---

### Post by jrib on 2006-01-31
You can use both gnome (ubuntu) and kde (kubuntu), just install the package ``kubuntu-desktop'' in Synaptic (system -> administration -> synaptic).  Then in the login screen just choose ``Session'' and then kde.

Personally, I prefer gnome, but you should try both and use what you like best.

As for your printer problem, I'd suggest you go to [http://www.linuxprinting.org/](http://www.linuxprinting.org/) and see what other users who own the same printer have been able to do.

---

### Post by spandon on 2006-02-01
Hi Jason
Attempted to follow your directions to switch between Gnome and Kde, but my desktop System/Admin menu is not as you described.
i.e. System/Admin/Synaptic Package Manager and when I go into Synaptic Package Manager there is no login screen.
Have I missed something, or do I have to do something within Synaptic Package Manager?
Thanks
Don

---

### Post by jrib on 2006-02-01
In Synaptic, you should search for and install the package ``kubuntu-desktop''.

After doing that you will have a choice, when you login (i.e. reboot your computer or just log out), to use kde.  You use kde by clicking on the ``session'' button at the login screen and selecting ``kde''.

---

