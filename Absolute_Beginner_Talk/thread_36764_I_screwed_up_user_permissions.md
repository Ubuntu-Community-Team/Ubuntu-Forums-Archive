---
title: "I screwed up user permissions"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by avatar_58 on 2005-05-24
I seem to have accidently taken away my user accounts right to do administrative tasks (I thought I should have done it at the time) and now it won't let me use root to do things in gnome? I'm confused, when I select "root terminal" why can't I put in my root password and gain access? I need my user password? Thats wierd to me.... :neutral: 

How do I get the permission back? I can't get back into "Users and groups" anymore and it won't let me login via gdm as root to change the setting back for my account....since I wouldn't know where to begin to fix it via the console.

Can someone help me?  :|

---

### Post by JonahRowley on 2005-05-24
[QUOTE=avatar_58]I'm confused, when I select "root terminal" why can't I put in my root password and gain access? I need my user password? Thats wierd to me.... :neutral:[/QUOTE]

It seems like this question is asked about once a day..  There is no root user, you do everything through sudo.  Sudo takes your password, not the root password (there is no root password).  That's why you're having so many "root problems", there is no root.

---

### Post by avatar_58 on 2005-05-24
Yes, I realize that...NOW  :???: 

Unfortunately how do I restore my user account's admin tasks access? I can't do anything via gnome anymore....my password not longer works.

---

### Post by avatar_58 on 2005-05-24
Thank the lord I'm learning!  :) Heres what I did to fix it:

I copied the "users and groups" icon to my desktop and looked at its name "users-admin" and then put that into 'run as' so that I could run it as root (obviously there must be a root account since this worked) and from there I was able to set the administrative tasks permission back on for my account.

I guess now is as good a time as ever to ask: is sudo safe? Couldn't I just use "su" instead like other distros? It's convienent yes, but doesn't the fact that it uses my regular password pose the same issues that are present in windows? Perhaps the security of it is lost on me since I'm new to ubuntu.

---

### Post by DW5 on 2005-06-27
I did the same thing Avatar_58 did, and as so I followed Avatar_58s fix.  All's well until I find myself confronted by the request for root's password, what do I put in? I tried mine, and every other pw for the users I have created on the machine.  I tried leaving it blank--still nothing works--"incorrect password for root."

For a fuller explanation of what I did (wrong):

The last time I used linux was the corel version in the late 90s.  So, after a friend told me about unbutu, I thought I would redeem an old machine as a student kiosk by installing unbutu, and in the process decide if I wanted to really switch to linux this time.  I installed unbutu, and, since this was going to be a kiosk machine, set up the kiosk user account first.  Later, I decided that having that user have admin rights was a bad idea.  So, I set up another account (using user-admin utility from within the kiosk account), which had admin rights.  I then logged in to the second account and used user-admin in gnome to remove the admin rights from the kiosk account.  The result was successful, the kiosk account no longer had admin rights, but neither did my second account. 

I later read that the first account should always have admin rights for sudo to work. Oh well....  

The question is how to fix it.  I think sudo is great, but when I try to use it or the user-admin process I get a terminated with child-1 error.  I don't have any other passwords to use.  

I'd prefer not to do a reinstall, though there's nothing on the machine that would need keeping if I had to.

Any help for a renewbie?

---

### Post by DW5 on 2005-06-28
I found the fix to this problem today in the desktop application fourm.  The thread entitled "lock out permission hell!!" :grin: 

boot into recovery mode

type nano /etc/sudoers at the prompt add username to the list under the %admin entry in the format

<username> ALL=(ALL) ALL

this restores sudo rights to the screwed up user permissions. \\:D/

---

### Post by crashtest on 2005-06-28
[QUOTE=DW5]I found the fix to this problem today in the desktop application fourm.  The thread entitled "lock out permission hell!!" :grin: 

boot into recovery mode

type nano /etc/sudoers at the prompt add username to the list under the %admin entry in the format

<username> ALL=(ALL) ALL

this restores sudo rights to the screwed up user permissions. \\:D/[/QUOTE]

Now that you're back in, if you'd like to avoid typing your password everytime you use sudo, change that entry to: <username> ALL=(ALL) NOPASSWD:ALL

---

### Post by DW5 on 2005-06-29
Thanks, that's a good tip.  I appreciate it.

DW

---

