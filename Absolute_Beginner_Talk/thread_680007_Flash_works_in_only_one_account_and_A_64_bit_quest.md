---
title: "Flash works in only one account? and A 64 bit question too."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Tallisman on 2008-01-27
Greetings ubu-fans!

I have 2 questions, both quite noobish I am afraid!

I am having problems with Flash in Firefox: it seems to work fine under my main account (the one created during the installation), but not any any other account... ie for the wife and kids. Why is that? Also, do I have to install Firefox extensions on a a per user-profile basis? Or is it possible to get Firefox working just right, and have that installation propagate to all new user profiles?

Question #2:
On my main machine/DAW I have installed ubuntu-studio 64 bit. I get the message that there are many new system updates available. If I click yes to install these, will it ubuntu studio search for and install only the 64bit versions of these updates? Or must I do some recompiling, etc?

thanks in advance for your assistance. 

please don't be shy about sharing terminal commands, and I won't be shy about adding them to my terminal commands sticky!

:D

rock and roll!
:guitar:
.Tallis

---

### Post by taurus on 2008-01-27
Did you install the plugins to your own $HOME account, ~/.mozilla/plugins, or did you install them to /usr/lib/firefox/plugins?

If you want everyone to use the plugins, you need to install them to /usr/lib/firefox/plugins (or even /usr/lib/mozilla/plugins).

---

### Post by Tallisman on 2008-01-27
wow quick delivery around here!

thanks for the tip I'll try that now.

thank you kindly.


....hmmm. is there something I need to add to the sudu install command to put the installation in a particular place?

cheers
.t

---

### Post by taurus on 2008-01-27
How did you install flash anyway?

---

### Post by Tallisman on 2008-01-27
I downloaded the .tar to the desktop.
navigated to the extracted folder and used ./flash-installer in the terminal.

:D

.t

---

### Post by taurus on 2008-01-27
If you ran that command without the sudo in front, then you installed it to your own $HOME directory, ~/.mozilla/plugins.  However, you can still copy the plugin to /usr/lib/firefox/plugins so everybody on the system can have flash if you wish.

Post the output of this command from a terminal.

```
ls -la ~/.mozilla/plugins
```

---

### Post by Tallisman on 2008-01-27
brilliant!

worked a treat, and I learned something too. of course this has lead to more questions:
is it possible to install something from a non-admin/ non root type account? For instance, if my son ask for me to install a game... can I do it from his account or *must* I log in to a root account?


also I have been met with this error message many times when using the *User Switcher* to switch between profiles:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

any idea on why and how to fix that?

thanks

.tallis

---

### Post by taurus on 2008-01-27
If you need to write anywhere outside your own $HOME directory, you need to be root and sudo would allow you to do that.  Therefore, if your son wants to install a game, you have to install it from your account using sudo which I assume you are the only one on your machine that can use sudo, the first original user that you created when you installed Ubuntu.  Once you've installed it, usually in /usr/games, everybody on your machine can run it.

---

### Post by Tallisman on 2008-01-27
Ok that is what I figured. and that it cool, I can do that.

so I am trying to wrap my head around the file/directory structure. Please correct me if I am missing the boat here:

in windows we have Program Files... all (or most) apps go there. Unless I configure it such, all user profiles can access these applications.

In linux:
/usr/ ____folder___ is like the universal program files, where the folder is an extra level of organization  (games, grafix, audio appz, etc)

users with sudo capabilities have the option of installing stuff to their own profile somewhere near their *Home* directory, or universally by using the sudo / gksudo commands in terminal.

is this right?

I appreciate your time. Please feel free to point me to where a noob should look for this. :D

.tallis

---

### Post by taurus on 2008-01-27
Actually, the last one is a little off.  User can install or do whatever he/she wants to his/her own $HOME.  For instance, if I want to install a program for myself, then I would just install it in my $HOME, usually ~/bin.  ~ stands for /home/*username* where *username* is my login name.  Therefore, I don't need root privilege to do that since I can write to my own $HOME.

On the other hand, if I want to install something so that everyone can use it, it would be more logical to install it to someplace like /usr/bin.  And to do that, I need root privilege since I am intending to write to /usr/bin, outside of my own $HOME.

However, I can still allow people on the system to run that program even if I install it in my own $HOME/bin with permission settings.

I bet your head is spinning right now.

---

### Post by Tallisman on 2008-01-27
yes... my head is spinning, but in an oddly fun and happy way.

I am loving this ubuntu thang in both flavors I have installed. 

perhaps you can advise here: I am looking for a replacement for alcohol120%
to mount iso of windows educational games for the Kids to be run through Wine... the disks are long destroyed, and I have been running them as virtual disks under windows...

I have found *Gmount ISO* and *AcetoneISO2* I understand that I can do this via terminal... using mount commands... that is a future endeavor. Today, I'd like to mount several .iso under various user profiles and have them be mounted upon each logon. is that possible? will either of the above offerings do that (do you know?). Would it be best accomplished with a logon script?

:D
is your head spinning now?

.tallis

---

### Post by quaystone on 2008-02-12
Thanks for the answer about where to put the plugin (it WAS installed only in my home directory, not in /usr/lib/firefox/plugins).  However, when I try to copy it (using sudo) It looks like the command is executed, but it doesn't show up in the directory listing.  I've tried moving it several times.

Thanks!

Sharon

---

