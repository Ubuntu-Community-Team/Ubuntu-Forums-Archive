---
title: "Root Permissions"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by dr_dirk on 2007-04-25
I have looked around trying to find out how to apply root permissions to my user account, but have not found information that refers to what exactly I want to do.  What I want:

I want to be able to operate under my regular account as you would under the root account.  This is because I really don't want to constantly fight permissions problems.  I want to be able to open terminal and not have to always type sudo (I know there is a simple way around that, but it is still an extra step), and I would like to be able to navigate nautilus and work with files without having to worry.  Again, I know that you can use gksudo nautilus, but I don't want to have to worry about that whenever I want to work with my files.  It's not hard, just an annoyance.  Most of all I don't want to put in my password every time I want to do something with add/remove programs, synaptic, update, or any other system change major or minor.

I don't mind working in the root account, but I would like to be able to use the auto login for my account.

As I read up on this the most common thing I read what that it's not safe or that it's not secure.  I understand the risks involved, but I'm the only person messing with my computer and if I were to screw up my system, no data will be lost.  All data is stored on another partition and backed up on another drive as well.

I know Ubuntu was designed that way to be safer etc., but after a while typing and retyping my password and such gets pretty tiring.  

One method I tried didn't work for me... I read that changing the UID and GID for my account to those of the root account then I would be able to log into my account with a root-like atmosphere.  However, I was not able to change the UID appropriately.

Any suggestions on how to accomplish my goals would be greatly appreciated.  Thanks

---

### Post by 007Bond on 2007-04-25
Go System --> Admin --> Users and Groups --> click on user --> properties --> advanced --> main group = root.

---

### Post by taurus on 2007-04-25
Perhaps you need to read this, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by ALIENDUDE5300 on 2007-04-25
You don't really want root permissions just use "sudo"
If you want to be able to login as root use "Sudo Passwd" and then do "su" on a terminal.

---

### Post by dr_dirk on 2007-04-25
Thanks taurus.  I read through the link you posted but I'm not sure it quite addresses what I'm trying to accomplish.  I've learned some of the ways to get around entering passwords repeatedly, but I'm trying to avoid them entirely once I've logged in, like you would once logged into root.

Maybe I missed something in the link that would help me.  If so, please let me know.  Thanks

---

### Post by taurus on 2007-04-25
Why would you want to log in as root?  One wrong command and you could trash your whole machine beyond repair, except reinstall.  Log in with your regular account and if you need to modify something outside your $HOME directory, use the sudo command.

---

### Post by dr_dirk on 2007-04-25
The reason is that I don't even have a use for my my home directory.  Anything I do under Filesystem is outside of that directory.  So I could use gksudo nautilus every time I want to change or copy a file somewhere in Filesystem, but it's kind of a PIA.

As far as trashing the system is concerned, A: how likely is it that irreversible damage could be done with a wrong command?  B: If I were to do such damage and a re-install was necessary, It wouldn't really do much harm except for the hassle of re-installing.  As I mentioned before, I understand that working that way creates more potential to harm my system, but I think I would rather be able to work without the password police always checking in on me.

---

### Post by taurus on 2007-04-25
```
sudo passwd root
```
And good luck.

---

### Post by dr_dirk on 2007-04-25
Thanks for tip, but logging into root isn't what I'm trying to do.  I'm trying to give my regular account root abilities.  By that I mean once I log in, I don't want to need to run gksudo nautilus if I want to copy a file to Filesystem or enter my password to download the updates.  Maybe this isn't possible and I have to work using the root account.

I'm confused, though, about the difference between being logged into root and entering a wrong command and using sudo and the same wrong command.

"sudo make me a sandwich" and "make me a sandwich" (logged into root) should yield the same result.  If you mistype that command so it reads "sudo make me liver and onions" and "make me liver and onions" (logged into root) you still execute a harmful command, right?  If that is the case, then the potential to harm your computer is still there whether you are in root or not.

If there is a functional difference between the two circumstances I would love to know because as it stands they seem like the same thing to me.

I'm going to reiterate, though, that my goal is not to have to log into root in order to have the conveniences of the root account.  I am trying to find a way to make my user account behave in the same fashion as the root account.

Thanks

---

### Post by aysiu on 2007-04-25
I don't think what you want is possible.

Barring user error, Linux is designed to have layers of security.

---

### Post by bobplano on 2007-04-25
sudo requires you to have a password if a session is not open so it is more protective because you have time to think, if only subconciously about the command. if you don't want to log in as root here are some commands i'm making up but sound like they should work because of how the commands work. 
```
gksu
```
if that comes up with an error about authentication just put
```
gksudo gksu
```

or for kde
```
kdesu
kdesudo(?) kdesu
```

---

### Post by aysiu on 2007-04-25
To the Linux gurus out there, would it be possible to change the username of root to something else?

Doesn't the system function based on user id instead of the text appearance of the username?

Or are there sometimes it's looking specifically for the name *root*?

---

### Post by dr_dirk on 2007-04-25
Ok, if what I'm looking for isn't possible, then it's not possible.  Could you say if there is functional difference between the two scenarios of entering "sudo command" and simply "command" while logged into root?  I'm curious because I have seen the argument many times now saying that it is more dangerous to work logged into root because you can mess up your system with a wrong command.  It doesn't seem to me that the system is in any more danger from the user in root or not.

---

### Post by aysiu on 2007-04-25
> **dr_dirk said:**
> Ok, if what I'm looking for isn't possible, then it's not possible.  Could you say if there is functional difference between the two scenarios of entering "sudo command" and simply "command" while logged into root?  I'm curious because I have seen the argument many times now saying that it is more dangerous to work logged into root because you can mess up your system with a wrong command.  It doesn't seem to me that the system is in any more danger from the user in root or not.
Well, the word *sudo* reminds you you're executing a command as root. If you're just logged in as root, you might forget after a while that you are root.

Also, *sudo* (at least as implemented in Ubuntu) will prompt for your password again after fifteen minutes. With a traditional root account, you can stay logged in as long as you want with no reminder you're right.

---

### Post by dr_dirk on 2007-04-25
If it does look only for the UID instead of the actual name "root", perhaps instead of making my account's UID the same as root's, (0) perhaps I should make my account 0 and change root's to say 1000.  Any thoughts on that?

---

### Post by dr_dirk on 2007-04-26
I tried changing my account's UID to 0 and root's account to 1000, but it was not possible, at least in the GUI.  I could change my account's UID to 0 but after closing the windows they would revert back to 1000.  It would not let me change root's UID at all.

Is there a way to change the UIDs from terminal?  If so, it may allow the changes I'm trying to make.

Also, I understand this could be a potentially very unhealthy move to make, but I would like to try.  If I have to re-install, then I have to re-install.  Given that, does anyone know how to change UIDs from the command line?

---

### Post by aysiu on 2007-04-26
Okay, considering you're willing to reinstall, try this: ```
sudo usermod -l kirkbackup kirk
sudo usermod -l kirk root
```

---

### Post by dubrict on 2007-04-26
My computer at home is a single-user machine, so I have no problem disabling password requirements for sudo access.  Just go in a terminal and type in

  visudo

and at the bottom of that file put:

  your_username ALL=NOPASSWD:ALL

You'll still have to put "sudo" before administrative commands, but I like it like this much better.  It never asks for the password.

---

### Post by dubrict on 2007-04-26
sorry, should be "sudo visudo"

---

### Post by aysiu on 2007-04-26
I thought about suggesting something like that, but dr_dirk didn't even want to have to launch *gksudo nautilus*.

---

### Post by dr_dirk on 2007-04-26
Thanks aysiu for helping out.  I tried what you said but it didn't turn out well.  I logged out and logged back in with my account (there was no more root) and gnome didn't act right at all.  The background was black, the titlebars for windows were super-sized.  alt-F2 didn't work and there were no menus for applications, places or system.  So, nice try but it didn't pan out.

I'll try what dubrict suggested.  While you're right, aysiu, I would prefer to not have to bother with gksudo nautilus, I can live with it.  The most irritating thing to me was seemingly constant battle against password popups.  I'll let you know how that goes.

---

### Post by dr_dirk on 2007-04-26
That method worked to get rid of the password problem.  Thank you dubrict and aysiu.

I just had an idea that would save me the annoyance of having to alt-F2 gksudo nautilus.  I created a launcher that will open that and put it in the place of File System on the desktop.  That works fine, but I have another, hopefully simpler, question.  Is there a way to have the launcher run gksudo nautilus and already be open on File System?  As it it when I launch it and it automatically opens to Desktop.  Of course it's a simple click to get to File System, but it would be nice if it opened there directly.

I should have thought of the launcher sooner, but I have not tried making launchers before.  It's strait forward, but I don't know if there is more that I can do with it.

---

### Post by aysiu on 2007-04-26
You can do one better than a launcher.

You can [create a keyboard shortcut for *gksudo nautilus*](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

If you want it to open to filesystem instead of desktop, try this: ```
gksudo nautilus /
```

---

### Post by dr_dirk on 2007-04-26
Great, thank you!  For the time being the launcher will do well enough for me but I'll check out the keyboard shortcuts very soon.  This setup is the kind of thing I was looking for.  I just didn't know about some of the possibilities you suggested.  I am a very happy camper :)  Thanks again

---

### Post by sailor2001 on 2007-04-26
auto login is system/administration/login window/security

---

### Post by Courtland on 2008-01-18
Hey I am listed as the owner and the admin. and yet when I try and modify the file system in anyway I am told I don't have the permissions to edit the folders(properties wont let me in) I tired it in terminal too but I just don't know any more. Can anyone help me out please?

---

### Post by aysiu on 2008-01-18
> **Courtland said:**
> Hey I am listed as the owner and the admin. and yet when I try and modify the file system in anyway I am told I don't have the permissions to edit the folders(properties wont let me in) I tired it in terminal too but I just don't know any more. Can anyone help me out please?
[This](http://www.psychocats.net/ubuntu/permissions) will help you.

---

### Post by Frogbarf on 2008-01-18
I just wonder if dr_dirk needs to take an altogether different approach.

Unless I grossly misunderstand his postings, what he's said is "I want to keep working the way I always have and Ubuntu is being too fussy about security."

My own experience in adapting to different systems over the years (and trust me, I've used a lot more than you might think!) is that, every last time, I've had to get inside the  system designers' heads and understand how they viewed the world -- and then adapt my methods to fit that model.

It would be helpful if dr_dirk gave us a few _specific_ examples of things he's trying to do that cause him grief, including how he's trying to do them under Ubuntu.

For example, maybe he's putting private data directories under / instead of under /home/userid. Or maybe he has permissions and groups mis-set so they are speed bumps instead of helpful.

For others coming to Ubuntu from Windows, one thing that's important to understand is that the root directory / is NOT the equivalent to your C: drive. A better equivalent would be your /home/userid directory, at least where data is concerned.

Sorry everyone for being so long winded, but perhaps my philosophizing will help us all get more comfortable with Linux, the security model in particular.

---

### Post by Courtland on 2008-01-19
> **aysiu said:**
> [This](http://www.psychocats.net/ubuntu/permissions) will help you.

Hey thanks for the tip. I figured out how to get the file to install into the file system perfectly. and that's when I went and broke it.
I changed my user name to the owner in permissions and now I've been locked out of synaptic and terminal because "root doesn't exist."
Any Advice on how to get back root permissions so I can fix this?

---

### Post by aysiu on 2008-01-19
> **Courtland said:**
> Hey thanks for the tip. I figured out how to get the file to install into the file system perfectly. and that's when I went and broke it.
I changed my user name to the owner in permissions and now I've been locked out of synaptic and terminal because "root doesn't exist."
Any Advice on how to get back root permissions so I can fix this?
Root doesn't exist? That was the *exact* error? If that's the case, you may be in trouble. As far as I know, nothing should be working if the root account has been deleted.

If you have somehow got yourself out of the *admin* group, however, then [this](http://www.psychocats.net/ubuntu/sudo) might help you get that back.

---

### Post by Courtland on 2008-01-20
> **aysiu said:**
> Root doesn't exist? That was the *exact* error? If that's the case, you may be in trouble. As far as I know, nothing should be working if the root account has been deleted.

If you have somehow got yourself out of the *admin* group, however, then [this](http://www.psychocats.net/ubuntu/sudo) might help you get that back.

"user root doesnt not exisist" thats what I got everytime I tried to open nautuliss or synaptic.  the computer down and now it won't even reboot. it begins to load and cant get past the "Hardware abstraction layer hald" I went tried the method you gave me before  and my name was already listed in the admin group. and it still wont boot...

---

### Post by Courtland on 2008-01-20
Ok ive totally broken this thing now...
I used nautilus to open my file system in root. then i went and changed the permissions and made my user name the owner. after that, synaptic, nautilus, and terminal would no longer work. I recieved the message that "user root does not exsist. so upon reboot it would load my hal and so i rean the system in recovery and ran :startx". I tried to change the permissions back, rebooted and no effect. then for some reason (call me stupid if I am) but I ran "fsck" which did not complete before my battery died...now it wont even give me the option for the boot menu, it just says:
Grub loading, please wait...
Error 17
and it doesnt go anyfurther than that...I reall messed this thing up pretty good and Im wondering if a fresh install would be in my best interest? Can someone please help me before I break it anymore? that is if there is anything left to break....
__________________

---

