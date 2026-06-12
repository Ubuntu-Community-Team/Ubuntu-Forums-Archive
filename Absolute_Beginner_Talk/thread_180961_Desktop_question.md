---
title: "Desktop question"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-23
Hi ppl,
 
Just a quick question - is the Kde-destop package available for download someway other than by updating.

I dont have a net connection in my ubuntu box. 
:KS

---

### Post by Sef on 2006-05-23
In Packages, you could download and burn the files.

[http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by hotbrainz on 2006-05-23
Cheers dude, one another thing - is there someway i can roll back to the normal UBUNTU when i have a KDE desktop ! :)

---

### Post by hotbrainz on 2006-05-23
Once i download this packages, how will i be able to add them to the other repositories?

---

### Post by nalmeth on 2006-05-23
When you have the packages, copy them onto a directory on the PC, and open up a terminal:
```
Applications / Accessories / Terminal
cd /directory_you_saved_packages
sudo dpkg -i *
```
This should install all the .deb packages in the directory.

In your last question, did you mean how to switch back to the default GUI (gnome)?
If so, just log out, and when logging back in with GDM, change the Session to Gnome.

---

### Post by hotbrainz on 2006-05-23
Thanks for the reply Nalmeth but at the moment the GDM shows no options, that i assume is because i have only gnome. Is that rite?

It just loads up without asking anything. So, if i load KDE it will ask be an option as to what i want?

---

### Post by aysiu on 2006-05-23
Download the Kubuntu installer CD. 
Burn it.
Pop it into your Ubuntu box.
Go to System > Administration > Synaptic Package Manager
Go to Edit > Add CD-ROM
Add it as a source.
Go to Settings > Repositories
Uncheck every box except the one you just added
Click Reload
Search for *kubuntu-desktop*
Mark it for installation.
Apply Changes.
Log out.
Click Session.
Select KDE.
Log in.

If you're not familiar with Synaptic, go here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by hotbrainz on 2006-05-23
thats great Aysiu, i have Kubuntu.... nice, that sound easy

Hats off to u

---

### Post by nalmeth on 2006-05-23
> Thanks for the reply Nalmeth but at the moment the GDM shows no options, that i assume is because i have only gnome. Is that rite?

It just loads up without asking anything. So, if i load KDE it will ask be an option as to what i want? Weird. Even though you might only have gnome, there should still be a Session tab/button with which you can log into Gnome, as well as Gnome Failsafe, and Gnome-Terminal Failsafe sessions. 
You have to choose the session before you enter your username and password.
Sorry, I misunderstood your question in the first place too.. I though you had KDE and wanted to upgrade to newer packages. Asyiu's way is what you want.

---

### Post by hotbrainz on 2006-05-23
hey Nalmeth, i just start my system up and then it just goes on to login. I choose nothing else. Am i missing something?

---

### Post by nalmeth on 2006-05-23
Do you get a login screen, or are you automatically logged in?
GDM is the display manager where you pick your user and the session (Gnome, KDE, XFCE, etc)
When you choose a new session, you're prompted, and asked whether to make it the default session.

You can configure GDM in System - Administration - Login Manager

You may have it configured to log you in automatically.

[Here's a picture of GDM (in French)]("http://blog.eax.fr/images/blog/installation-ubuntu/20-ecran-login-gdm-ubuntu.jpg") see where it say's session below the text-field? There's your ticket.

---

