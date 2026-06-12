---
title: "Cannot log into administrative account"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by cyanidearsenic on 2007-12-23
Ubuntu 7.10

Whenever I try to log into my (only) administrative account I get this message:

```
GNOME session manager cannot lock the file /home/user/.ICEauthority.
```

(The user part is actually a name)
It also says to try logging into the failsafe session but it will not allow me to log in there either.

All of my stuff and all administrative stuff can only be accessed (without logging to root) from that account, so I kind of need to be able to log in there.

If I can't get into that on account is it possible to create a new administrative account from a non-administrative account? (and possibly, hopefully get that one .odt I NEED from that account.)

---

### Post by ChaosParser on 2007-12-23
What window managers besides GNOME do you have installed?

/home/user/.ICEauthority has a habit of changing ownership when some programs are run as root instead of sudo.

---

### Post by cyanidearsenic on 2007-12-23
I am a total ubuntu/linux beginner.

I'm not exactly sure, I didn't know I had more than one.  How would I know which one I have?

(Don't know if it will help any but the error message is a Gnome one.)

---

### Post by ChaosParser on 2007-12-23
You have other accounts that are none admin, right? 

They should be able to install programs.  Desktop users can by default. 

Open a terminal, type in sudo apt-get install kubuntu-desktop

Reboot. 

At the login screen where it says sessions, click on that, it should list the window managers you have installed.  Try logging in with kde.

---

### Post by cyanidearsenic on 2007-12-23
I installed the Kubuntu-desktop and it just finished but now I'm being asked to select a default desktop manager.  Options are gdm and kdm.

---

### Post by ChaosParser on 2007-12-23
Select GDM, gdm is Gnome.  We're just going to use KDE to change the permission of the file that's hanging gnome.

---

### Post by cyanidearsenic on 2007-12-23
Okay, good news and bad news.

Good news: I'm not getting the **.ICEauthority** message any more.

Bad news: Whenever I try to log in I get:

**Users $HOME/.dmrc file is being ignored. This prevents the default session and   language from being saved. File should be owned by user and have 644 permissions.                     User's $HOME directory must be owned by user and not writable by others.**

Then, when I hit okay, I get a blank blue screen and a message that says there is something wrong with my** kstartupconfig** and to check my installation.

---

### Post by ChaosParser on 2007-12-23
Okay, somehow you've managed to completely fubar your permissions... >.< 

can you get into a terminal? 

If so... 

chmod 644 /home/user/.dmrc

is what you need to do.

---

### Post by cyanidearsenic on 2007-12-23
More likely my sisters-who-don't-know-how-to-leave-things-alone managed to completely fubar my permissions.

Did that, I had to sudo it because it kept giving me a permission denied output.  Should I try to relog with kde now?

---

### Post by ChaosParser on 2007-12-23
Time to give the sisters limited desktop user accounts. ;) lol 

You should be able to login with either Gnome or KDE now.

---

### Post by cyanidearsenic on 2007-12-23
I'm still getting the last two error messages whenever I try to log on.  The .dmrc one and the kstartupconfig one.

---

### Post by cyanidearsenic on 2007-12-23
Well, I only get the kstartupconfig one when I try to log in with kde but I get the .dmrc one whenever I try to log into any of the sessions.

---

### Post by ChaosParser on 2007-12-23
sudo chmod 644 /home/user/.ICEauthority

Login with Gnome, click okay to the .dmrc one, it should let you login anyway. 

Check and make sure that no other user or user group has write permissions to your home folder.

---

### Post by cyanidearsenic on 2007-12-23
I swear this O.S. hates me...

Okay, now (no matter whether I use a GNOME session or a KDE session) I get the following error message.  (This one kind of scares me...)

**Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.**

and when I tried logging into a failsafe session, it hung on a blank screen and I had to restart the computer.

---

### Post by ChaosParser on 2007-12-23
You might have to use a LiveCD to recover the data and then reinstall.  >.<

---

### Post by cyanidearsenic on 2007-12-23
By recover the data do you mean that I won't loose a particular document (that is on the account I can't access) that I REALLY need?

---

### Post by ChaosParser on 2007-12-23
Any possibility that you really are out of disk space?  If so... 

sudo apt-get clean

---

### Post by cyanidearsenic on 2007-12-23
I really have no idea.  I'm not even sure I understand what it means by 'diskspace'.  If i'm not will trying that mess anything up?

---

### Post by ChaosParser on 2007-12-23
Well, your permissions are messed up in that your home directory doesn't seem to be owned by you.  Which means another account should be able to access that home folder.

---

### Post by cyanidearsenic on 2007-12-23
The only other account is the guest one of my sister's that I'm on right now.

---

### Post by ChaosParser on 2007-12-23
Can you get to the home folder?

---

### Post by ChaosParser on 2007-12-23
gksudo nautilus from a terminal on your sister's profile, and you should be able to access your home directory to access that file and save it, but as soon as you have it, I'd reinstall.

---

### Post by cyanidearsenic on 2007-12-23
The /home/guest/?  Yeah.

---

### Post by ChaosParser on 2007-12-23
Go back to the main home folder, you should see your name there.

---

### Post by blueridgedog on 2007-12-23
If you boot on the live CD you should be able to access your file.  Do you have a usb drive or some way to email it to someplace?

---

### Post by cyanidearsenic on 2007-12-23
Yeah, it's there but whenever I try to click on the documents folder (where the file I need is) I get this message:

**Couldn't Display "/home/*user*/Documents" The attempt to log in failed.**

---

### Post by jaybombalous on 2007-12-23
boot livecd. save file u need and re-install.

First thing u do is stop your sister from having sudo or root permissions in anyway shape or form. Then u will be surprised to learn it wasn't them after all. :)

I find it hard to believe u don't even know what diskspace is but yet u blame this problem on your sister. :) wanna confess on what u really was trying to do?

---

### Post by cyanidearsenic on 2007-12-23
If I boot the liveCD will I be able to log into my normal account or will I be able to access it from this guest account?  

I don't see how it couldn't have been them.  The computer was fine when I left, I came back three days later and I can't get on my normal account.

---

