---
title: "Cross-system users and permissions?"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by WanderingOak on 2010-10-24
I just finished installing Lucid Lynx on an iMac7,1. I would like to still be able to access my Mac Documents directory from within Ubuntu, so I can have a common directory that both systems can access. Right now, however, I am unable to do that. It looks like it might be a permissions issue- ie I am a different 'user' on both systems, so I don't have access to my Mac files. Is there a way to have the same 'user' account for both systems? If not, could a common 'group' be created in both systems that both of my 'user' accounts have access to?

---

### Post by srs5694 on 2010-10-24
Yes. Change your UID value in Linux with the usermod command. You'll also need to change the ownership on all your existing files:

```

sudo usermod -u 501 yourusername
sudo chown -R 501 /home/yourusername

```

Be sure to shut down as many programs as possible before issuing these commands. When you're done, log out and back in again. (You might need to log out and back in between these two commands, in fact.) This sort of thing is actually best done via a direct root login or at least a login to a second administrative account; but given Ubuntu's security model, doing is as I've described is simpler and can be made to work.

The specific example uses a target UID value of 501, which is what my own OS X installation uses; but you should check the UID values used on your system. Also, obviously, you should change "yourusername" to your actual username.

You can change the group ID with the -g option, too; however, IIRC, the default group ID in OS X maps to something or other unrelated that actually exists in Ubuntu, so you'd need to juggle your group IDs. It's probably OK to let that slide, unless you've got multiple users and use the group ownership for real security purposes.

Alternatively, you could do all this on the OS X side. I'm less familiar with OS X's account management tools, though, so I can't provide specific instructions.

---

### Post by WanderingOak on 2010-10-24
That did the trick. I did have to create another Admin account, and after I performed the usermod command, my original account vanished. It was no longer a login option, and it was no longer listed in 'Users and Groups', and I couldn't attach any other accounts to my Mac UID. Fortunately, I was able to login with that account as a 'guest'. I think perhaps an easier way of doing it would have been to modify my UID from within 'Users and Groups' using my second admin account. 

Anyhow, thanks for the help!

---

### Post by WanderingOak on 2010-10-24
I still have a minor issue. My regular user account is still not an option at login. I have to login as 'other' and enter my username and password. The 'login screen' utility does not allow me to log into my regular account automatically. My regular account is listed under 'users and groups' now, as an administrator. How do I get my primary account on the login screen?

---

### Post by WanderingOak on 2010-10-26
Still trying to figure this out. Under my 'alternate' admin accounts, my main account is not visible under 'users and groups'. Where does Ubuntu keep track of such things? I've tried to add my Mac UID to other users, only to be told that it is in use by my main user (even though I can not see him). I've added my alternate admin accounts to my main account's group, but they still don't have access to my Mac directories. To top it off, nobody has write access to my firewire drive, or my Mac partition, even though 'ls -l' says that they should (edit- I've figured out why it's doing that). 
 
I used to know how to manage user accounts from the command line, but I'm a bit rusty, and I've loaned out my copy of 'Running Linux'.
 
Any assistance would be appreciated.

---

### Post by el_heffe on 2010-10-26
I too am having the same problem you are describing, but my user is no longer listed in the Users & Groups control panel.  I am looking for a way to fix this issue, but I have nothing invested in the user I created so I may just delete it and recreate it with the UID of 501(my OS X install gave me the same number).  

As for WHY this is happening, IIRC users below 1000 are not displayed in the Ubuntu users menu.  It may be just Ubuntu, or Linux, not quite sure.  Just something I vaguely recall.

---

### Post by el_heffe on 2010-10-26
OK, so I followed this page:

[http://ubuntuforums.org/showthread.php?t=575537]("http://ubuntuforums.org/showthread.php?t=575537")

Which, at the end says to do this:

```
edit /etc/login.defs change UID_MIN 1000 to UID_MIN 500

edit /etc/gnome-system-tools/users/profiles changing each uid-min=1000 to uid-min=500

edit /etc/adduser.conf LAST_SYSTEM_UID=999 to 499 and FIRST_UID=1000 to 500
```

BUT- it does not work.:(

I tried deleting and re-creating the user, rebooting, logging in/out, jumping up and down while yelling at it, and nothing.  SO I am going to just revert my user back to 1001 and call it a day.

---

### Post by WanderingOak on 2010-10-26
> **el_heffe said:**
> I too am having the same problem you are describing, but my user is no longer listed in the Users & Groups control panel. I am looking for a way to fix this issue, but I have nothing invested in the user I created so I may just delete it and recreate it with the UID of 501(my OS X install gave me the same number). 
 
As for WHY this is happening, IIRC users below 1000 are not displayed in the Ubuntu users menu. It may be just Ubuntu, or Linux, not quite sure. Just something I vaguely recall.
 
That would definitely explain the problem. Perhaps UIDs below 1000 are considered to be 'system' users, or something like that. So, is there a way to change the UID of my Mac account, without causing any damage? Would a common Group ID in both systems be a solution? Since Ubuntu can't write to my Mac partition anyway (without turning off journaling, at least), I am probably just going to use an external drive as a common storage area, and use it routinely with both systems.
 
Otherwise, this seems to be one of those "can't get there from here" type of situations...

---

### Post by el_heffe on 2010-10-27
Just noticed you are from Watertown, I went to Clarkson University for a couple years... nothing up there except cold wind & trees.  And thats when there is snow!  Anyways, a quick google turns up this:

[http://osxdaily.com/2009/02/19/mac-os-x-change-your-user-id/](http://osxdaily.com/2009/02/19/mac-os-x-change-your-user-id/)

Which basically tells you to do:

```
dscl . -change /Users/will UniqueID 501 1000
chown -R 1000 /Users/will

```

Where you replace the username will with whatever your username is and the 1000 to match your UID in ubuntu.  I'll give it a go when I turn my powerbook on, right now I am playing with my Mini10v.

---

