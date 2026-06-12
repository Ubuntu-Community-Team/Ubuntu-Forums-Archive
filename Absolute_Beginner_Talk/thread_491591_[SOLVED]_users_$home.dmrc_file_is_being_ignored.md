---
title: "[SOLVED] users $home/.dmrc file is being ignored"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by MacDuff on 2007-07-03
After battling with Wine today my machine ground to a halt and I had to use the three finger salute (Ctrl Alt Del) to re-boot.

Now when I log in I get a message:
Users $HOME/.dmrd file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others.

I am very new to Ubuntu and am using the GUI, not being familiar with terminal commands so if someone can gently walk me through fixing this without having to do yet another re-install, I would appreciate it.
Thanks

Mac

---

### Post by spyheart on 2007-07-03
Hey Mac,

Please check the following link...hope this mayt solve your problem..

[https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296)

Gud Luck

Pavan

---

### Post by MacDuff on 2007-07-03
Thanks Pavan

Your direction led me to a posting by : 
Ralph Janke  said on 2007-06-03:

Enter
chmod 644 .dmrc
chmod 700 ~

That seems to have done the trick.  It seemed too easy. I was looking for a response to the terminal entry but did not see one so did not know if the settings were changed or not but on re-boot no error message appeared.
I did not even have to log in as a super user or whatever it is called in Ubuntu.

Thanks again
Mac

---

### Post by Refresh_61 on 2007-07-07
Thanks Pavan

That solved my problem     :D

---

### Post by Sweet Spot on 2007-07-17
Can someone tell me, essentially what that (initial message which OP stated) actually means and why it happened ?  I just input the chmod fix listed by the OP, hoping it will work but would really like to know what it fixes exactly ?  I'm also assuming it has something to do with the installation of WINE or a program running under it ? (Since I only first got the message when I reboot just now, and the last thing I installed was DVD Shrink via WINE)

Doug

---

### Post by az on 2007-07-17
> **Sweet Spot said:**
> Can someone tell me, essentially what that (initial message which OP stated) actually means and why it happened ?  I just input the chmod fix listed by the OP, hoping it will work but would really like to know what it fixes exactly ?  I'm also assuming it has something to do with the installation of WINE or a program running under it ? (Since I only first got the message when I reboot just now, and the last thing I installed was DVD Shrink via WINE)

Doug

It has nothing to do with wine.  It has to do with either the permissions of the .dmrc file or the permissions of your entire home directory.  It's a two-for-one message and that's confusing.


[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/28387](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/28387)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/33132](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/33132)

Plus there are many others...
[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=.dmrc&orderby=-importance&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Invalid&field.status%3Alist=Won%27t+Fix&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.status%3Alist=Fix+Released&field.importance%3Alist=Undecided&field.importance%3Alist=Wishlist&field.importance%3Alist=Low&field.importance%3Alist=Medium&field.importance%3Alist=High&field.importance%3Alist=Critical&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_contact=&field.component-empty-marker=1&field.status_upstream=pending_bugwatch&field.status_upstream=hide_upstream&field.status_upstream=resolved_upstream&field.status_upstream=open_upstream&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.tag=&field.has_cve.used=&field.has_no_package.used=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=.dmrc&orderby=-importance&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Invalid&field.status%3Alist=Won%27t+Fix&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.status%3Alist=Fix+Released&field.importance%3Alist=Undecided&field.importance%3Alist=Wishlist&field.importance%3Alist=Low&field.importance%3Alist=Medium&field.importance%3Alist=High&field.importance%3Alist=Critical&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_contact=&field.component-empty-marker=1&field.status_upstream=pending_bugwatch&field.status_upstream=hide_upstream&field.status_upstream=resolved_upstream&field.status_upstream=open_upstream&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.tag=&field.has_cve.used=&field.has_no_package.used=)

---

### Post by dondad on 2007-07-17
> **Sweet Spot said:**
> Can someone tell me, essentially what that (initial message which OP stated) actually means and why it happened ?  I just input the chmod fix listed by the OP, hoping it will work but would really like to know what it fixes exactly ?  I'm also assuming it has something to do with the installation of WINE or a program running under it ? (Since I only first got the message when I reboot just now, and the last thing I installed was DVD Shrink via WINE)

Doug

One thing that I have seen that can cause it is to use sudo with a graphical app like gedit rather than gksudo. This can sometimes mess up your permissions.

---

### Post by starfleetcaptainrob on 2007-07-21
i'm having the same issues here, but when i type in chmod 644 .dmrc I get:

chmod:  cannot acces '.dmrc': No such file or directory.   

Any help would be appreciated.  It's preventing me from logging in, I have to go to a failsafe terminal.

---

### Post by Old Pink on 2007-07-21
How can you use Ctrl Alt Delete to reboot? DId you seriously manually set that up to sudo reboot now? :lol:

---

### Post by starfleetcaptainrob on 2007-07-21
Nevermind.  I had to create the file by doing:

```
touch .dmrc
```

and then I did this sequence:

```
sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
```

and it let me back in.  thanks anyhow!

---

