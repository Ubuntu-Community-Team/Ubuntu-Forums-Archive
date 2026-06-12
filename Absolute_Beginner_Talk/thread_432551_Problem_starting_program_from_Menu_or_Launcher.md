---
title: "Problem starting program from Menu or Launcher"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-05-04
_Using Ubuntu6.06_

I have loaded a program - firstly I installed it from Synaptic.

The program is GnuCash.

The installation didn't place an item in the menus (particularly Office menu).

So I thought I would be clever (I am pretty new to all this) and try typing gnucash in a terminal.  I got an error The error I got was 
```
~$ gnucash

Gnome-ERROR **: Could not set mode 0700 on private per-user Gnome directory </home/david/.gnome_private> - aborting

aborting...
Aborted
~$
```.  
I then typed sudo gnucash - and it loaded and worked OK.

I then thought I would create a launcher, but putting in the command gnucash either with or without sudo does not work - simply, nothng happens!.

I thought I would try another approach, so I did a complete removal of gnucash from Synaptic Package Manager, and then follwed the instructions [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Accounting_Application_.28GnuCash.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Accounting_Application_.28GnuCash.29") 
This did give me a menu item, but it still did not work (nothing happens on clicking the menu item).

It **does** work if I type sudo gnucash in a terminal - what an I doing wrong ??  :(

Thanks for any help.
David

---

### Post by felicity on 2007-05-04
I'm not familiar with Gnucash, but here's some general ideas that may help:

I don't think sudo will work from a launcher because you would need to enter a password afterwards.

Try 'man gnucash' from a terminal or 'gnucash --help' to get more information about the commands you can use with Gnucash.  Maybe it needs another command to start correctly without being root.

Maybe you need to add your user name to the Gnucash group in System>Administration>Users and Groups>Manage Groups? I know virtualbox requires this step to run.

It sounds like you don't have the correct privileges to run it.  Maybe you installed the database on a drive that doesn't have read/write privileges?

Sorry I can't be of more help! ):P

---

### Post by David Floyd on 2007-05-04
> **felicity said:**
> I'm not familiar with Gnucash, but here's some general ideas that may help:

I don't think sudo will work from a launcher because you would need to enter a password afterwards.

Try 'man gnucash' from a terminal or 'gnucash --help' to get more information about the commands you can use with Gnucash.  Maybe it needs another command to start correctly without being root.

Maybe you need to add your user name to the Gnucash group in System>Administration>Users and Groups>Manage Groups? I know virtualbox requires this step to run.

It sounds like you don't have the correct privileges to run it.  Maybe you installed the database on a drive that doesn't have read/write privileges?

Sorry I can't be of more help! ):P

Thanks for your help.

The 'man' and 'help' entries didn't help me to understand a solution to this problem.

There is no entry in Groups for GnuCash.

Perhaps your last comment is the reason why I can only run it from a terminal with sudo, but I don't know how to get round this.

David

---

### Post by use a name on 2007-05-04
You could try to chmod it yourself:

```

chmod 700 ~/.gnome_private

```

sudo from a launcher does not work indeed. Use gksu instead (or kdesu if you're in kde). That's the one that invokes the password window instead of the password line in the terminal.

But, you won't need it. The application is to be ran by a normal user. You can use the above for launchers for synaptic and the like. The ones that require root privileges. The fact that it ran with sudo is because it then alters the privileges in the /root folder, which it has the rights for because of the sudo. Any work you have done in the program is now saved in the root folder, instead of your own home folder.

Hope it helps. ;)

---

### Post by David Floyd on 2007-05-04
> **use a name said:**
> You could try to chmod it yourself:

```

chmod 700 ~/.gnome_private

```

sudo from a launcher does not work indeed. Use gksu instead (or kdesu if you're in kde). That's the one that invokes the password window instead of the password line in the terminal.

But, you won't need it. The application is to be ran by a normal user. You can use the above for launchers for synaptic and the like. The ones that require root privileges. The fact that it ran with sudo is because it then alters the privileges in the /root folder, which it has the rights for because of the sudo. Any work you have done in the program is now saved in the root folder, instead of your own home folder.

Hope it helps. ;)

Thank you for your help.

Thing is .gnome_private is already set 700 (drwx------)

The menu item still does nothing, but now I've added gksu to the command in the desktop launcher it now runs from the launcher, but, of course, asks for a password, which I rather it wouldn't.

Do you know if I can change it to start without asking for password?

Thanks
David

---

### Post by use a name on 2007-05-04
Not with gksu...

Do you have your /home on a separate partition? In that case, maybe there are configuration files around from a previous install. I do not have a .gnome_private folder, but I do have .gnome2_private. I have .gnome and .gnome2, but as root, I only have .gnome2 (is on the same partition as the rest of the system).

Might be something, might be nothing.

---

### Post by David Floyd on 2007-05-04
> **use a name said:**
> Not with gksu...

Do you have your /home on a separate partition? In that case, maybe there are configuration files around from a previous install. I do not have a .gnome_private folder, but I do have .gnome2_private. I have .gnome and .gnome2, but as root, I only have .gnome2 (is on the same partition as the rest of the system).

Might be something, might be nothing.

Only one partition.

David

---

### Post by use a name on 2007-05-04
So, it *is* looking for the right folder, but it does not work with the normal user, only with root...
Which of the two does root have? .gnome_private or .gnome2_private? (Just asking, I'm out of ideas already...)

---

### Post by David Floyd on 2007-05-04
> **use a name said:**
> So, it *is* looking for the right folder, but it does not work with the normal user, only with root...
Which of the two does root have? .gnome_private or .gnome2_private? (Just asking, I'm out of ideas already...)

Thank you for your patience.

As you can guess I am fairly new to Linux.

The relevant part of my home directory looks like this:
```
drwxr-xr-x  6 david david   4096 2007-05-04 13:33 .gnome
drwx------ 16 david david   4096 2007-05-04 14:34 .gnome2
drwx------  2 david david   4096 2007-02-04 14:33 .gnome2_private
drwxrwx---  2 root  root    4096 2007-05-01 14:29 .gnome_private
drwx------  3 root  root    4096 2007-05-02 16:34 .gnucash

```

Does this mean anything to you.

Thanks
David

---

### Post by use a name on 2007-05-04
Yes... We're getting there.

the folders gnucash wants to use are owned by root. You can change that with:
```

sudo chown -hR david ~/.gnome_private
sudo chown -hR david ~/.gnucash

```
That'll make the two folders and their contents yours. It's strange that they are owned by root anyway... Didn't expect that. :confused:

After that, the program can be launched without gksu.

---

### Post by David Floyd on 2007-05-04
> **use a name said:**
> Yes... We're getting there.

the folders gnucash wants to use are owned by root. You can change that with:
```

sudo chown -hR david ~/.gnome_private
sudo chown -hR david ~/.gnucash

```
That'll make the two folders and their contents yours. It's strange that they are owned by root anyway... Didn't expect that. :confused:

After that, the program can be launched without gksu.

Thank you my friend.  :)  It now works as expected.

I'm keeping a little note book of all these oddities - it's a steep lurning curve compared with Windows, but I'm determined to persevere and not go to Vista.

David

---

### Post by use a name on 2007-05-04
Ah, great.

I just ran into an hint to how it might have happened: [http://ubuntuforums.org/showthread.php?t=432218](http://ubuntuforums.org/showthread.php?t=432218), post #6. Maybe your first run was from sudo. Or maybe you ran synaptic with sudo (would explain the missing menu-entry).

---

### Post by David Floyd on 2007-05-04
> **use a name said:**
> Ah, great.

I just ran into an hint to how it might have happened: [http://ubuntuforums.org/showthread.php?t=432218](http://ubuntuforums.org/showthread.php?t=432218), post #6. Maybe your first run was from sudo. Or maybe you ran synaptic with sudo (would explain the missing menu-entry).

Thanks for that, I'll remember that for the future.

David

---

