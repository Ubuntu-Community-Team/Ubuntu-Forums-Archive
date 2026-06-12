---
title: "Auto Login issue with &quot;nm-applet&quot;.  Autologin stops for a password?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-11-05
Hi,

I am trying to get my 7.10 install finished.  I selected the auto login so I dont need to enter a password.  The login seems to work fine, but once it starts to load my wifi settings, the autologin stops & I get this message:

Unlock Keyring

Enter Password for default keyring to unlock

the application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked.

I then need to enter my password & everything is smooth sailing.

Is there a way to bypass that login?  From my reading, I might not be added to one of the user groups, but i dont see any group that says wifi, or nm-applet.

Any ideas would be great!

Thanks,
Rich

---

### Post by RichTJ99 on 2007-11-05
btt

---

### Post by RichTJ99 on 2007-11-18
I think it has something to do with my wireless.  The wireless doesnt connect until that password is entered.

---

### Post by ronmarley1 on 2007-11-18
If you go to System -->Administration -->Keyring Manager.  It should ask you to allow the keyring manager to always allow access.  That should make the prompt go away on future boot ups.

---

### Post by RichTJ99 on 2007-11-19
Unfortunately that didnt work.  I did give it access always, but on each boot up, it asks for the password for the NM-Applet.

Any other ideas?

Thanks,
Rich

---

### Post by anewguy on 2007-11-19
I thought it was integrated with 7.10, but I could be wrong - look for the "PAM" package.  Basically it says if your logon password and the keyring password are the same, don't ask for the keyring password.  I was wondering, since I've never used the auto logon, did you have to enter a password when you were setting up Ubuntu?  Perhaps it sees your password as null because of auto logon, and therefore PAM can't match a password?:)

BTW - check to see if you have a group of "netdev" (I think the group number is something like 112).  If so, be sure you are a checked user in that group, as I believe it has something to do with network manager from what I have read.

---

### Post by ronmarley1 on 2007-11-20
> **RichTJ99 said:**
> Unfortunately that didnt work.  I did give it access always, but on each boot up, it asks for the password for the NM-Applet.

Any other ideas?

Thanks,
Rich

Hmmm.  I guessing here, but maybe it won't go away since you have the auto-login?
Here's what I would try, but I'm not sure it will work.  What I would do is to go back and turn off auto-login.  Then, delete the default keyring in your /home directory.  You'll need to hit Ctrl+H once in your /home directory to show hidden files.go into the .gnome2 directory, then into keyrings and delete the default keyring.  Logout, and then log back in.  When you try to connect to your wireless, it should ask if you want to save the password in the keyring manager.  When you set the keyring manager password, make it the same as your login password.  Turn auto-login back on, reboot, and see what happens.
Good luck, and sorry for the "guess" answer.

---

### Post by BluJai on 2007-11-28
The key is the "libpam-gnome-keyring" package. After installing that package you'll want to reboot (or otherwise have to re-authenticate). You'll still get the keyring password window, but there will be a checkbox available to auto-login in the future. Checking that will fix the problem.

Good luck!

-**[COLOR="Blue"]Blu[/COLOR]Jai**-

---

### Post by RichTJ99 on 2007-11-28
Is there a command line to install that?  This sounds like just the ticket for me!

---

### Post by BluJai on 2007-11-28
You should be able to use:
```
sudo apt-get install libpam-gnome-keyring
```

I'm not at a linux box right now, so I can't verify. I can say that I was having the same problem and installing that package fixed me right up.

-**[COLOR="Blue"]Blu[/COLOR]Jai**-

---

### Post by RichTJ99 on 2007-11-28
Is this package something I can find in Synaptec?  (I might have butchered that word)

---

### Post by RichTJ99 on 2007-11-28
Here is my results (im still stuck sadly):

rich@rich-laptop:~$ sudo apt-get install libpam-gnome-keyring
[sudo] password for rich:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rich@rich-laptop:~$

---

### Post by BluJai on 2007-11-30
The error you received (Unable to lock the administration directory (/var/lib/dpkg/)) is commonly caused by another apt-get interface running -- such as Synaptic or software update.

Make sure you've closed any software update and Synaptic windows *prior* to running the command. Alternately, you can just search for that package name in Synaptic. I usually use Synaptic for any package additions, since its so easy to see the details/description of the package(s) you're interested in.

Sometimes you'll get the error when software update is running in the background -- such as if it is downloading updates, but hasn't notified you yet.

If all else fails, reboot.

---

### Post by RichTJ99 on 2007-11-30
Hi,

I got the command to work here:

[http://ubuntuforums.org/showthread.php?t=626580](http://ubuntuforums.org/showthread.php?t=626580)


It said I already had that update installed.  I never got to see the checkmark to save the password.  Do you have any other ideas on how I could make it all work?

Thanks,
Rich

---

### Post by dpurple77 on 2007-12-02
There is a problem with nm-applet and autologin according to this post

[http://ubuntuforums.org/showthread.php?t=187874&page=18](http://ubuntuforums.org/showthread.php?t=187874&page=18)

but you can install wicd which is an alternate network manager as posted here

[http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)

I have switched with much succes and now my freevo standalone box has wireless without password for network manager. I hope that helps. cheers.

---

### Post by homburg on 2008-03-23
I have this problem as well. Just installed Hardy, but had the problem in Gutsy as well.

Have tried installing libpam-gnome2-keyring to no avail. I do not get a checkbox on the keyring password prompt dialog.

Did anybody solve this problem?

---

### Post by RichTJ99 on 2008-03-23
Im probably going to do a reinstall at some future point (probably for Hardy).  Do we know what causes this issue?  I wouldnt mind changing my passwords to make sure that this doesnt happen again next time (its very annoying).

---

### Post by jonboy99 on 2008-04-27
Has a solution been found yet?  This minor thing is a dealbreaker for me as far as Hardy is concerned - I have a dapper machine at my mum's house which the whole family can use for the web so don't want separate accounts, but I don't want them knowing (or needing to know) any of the machine's passwords.

It works fine on dapper.  I'm using ndiswrapper so am a bit relectant to try other network managers for fear of breaking it all.

*edit* seems fixed now - I just set the login ring key to a blank password (pressed return) and it doesn't ask for a password any more.  I don't intend to use this key for any other passwords so problem seems sorted.

---

### Post by emulsion on 2008-04-30
Found this in another post here, this was way easier for me than some of the other solutions.  Only downside is I'll have to always remember to change this password when I change my ubuntu password.
[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html](http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html)

---

### Post by johnwillis on 2008-06-27
If you still get this issue with Hardy (8.04) then do the following:

System --> Preferences --> Encryption and Keyrings

Then click on the bit that says "Password Keyrings"

and then select the "login" line. Click change password. Enter your current password and then leave the rest blank and click ok.

The "login" line should now say unlocked when a user logs in.

If you get a prompt sayin unsafe storage. Don't worry proceed.

This should solve any issues.

-J

---

### Post by Enmi on 2008-06-28
I was wondering where that option went! 

I saw that in the Hardy LiveCD, and I got a little too excited. Then all that excitement popped like a baloon as soon as I turned on Autologin. XP

Thanks for pointing that out, johnwillis!

---

### Post by stich0602 on 2008-07-10
Thanks johnwillis! This worked for me :)

---

