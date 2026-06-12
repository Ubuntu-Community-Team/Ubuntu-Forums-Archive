---
title: "How do I install the &quot;libpam-gnome-keyring&quot; package?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-11-29
Hi,

I would like to try to install the "libpam-gnome-keyring" package in order to fix a problem I am having with my auto login.  I do not see this option within the Synaptic package.  

I have also tried: 

sudo apt-get install libpam-gnome-keyring

This is my result:
rich@rich-laptop:~$ sudo apt-get install libpam-gnome-keyring
[sudo] password for rich:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rich@rich-laptop:~$


Any ideas on how to proceed?

Thanks,
Rich

---

### Post by =velkyn= on 2007-11-29
it seems like you have more than one update-manager running at the same time.
close synaptic, adept, or whatever you use and run the command again in the terminal.

---

### Post by natehatewindows on 2007-11-29
this happens when you have say "add and remove programs" and synaptic running at the same time (or a terminal that you tired to apt-get in). quit all of these apps and try to do the apt-get again. if it does not work then reboot, then try.

---

### Post by RichTJ99 on 2007-11-29
Well, it worked:

rich@rich-laptop:~$ sudo apt-get install libpam-gnome-keyring
[sudo] password for rich:
Sorry, try again.
[sudo] password for rich:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpam-gnome-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
rich@rich-laptop:~$ 


Sort of, I was installing this because someone mentioned that after installing this, when you boot up, you wouldnt have to enter the password in ubuntu each time you reboot (7.10 here).

Someone here:

[http://ubuntuforums.org/showthread.php?t=603265](http://ubuntuforums.org/showthread.php?t=603265)

suggested that installing that keyring software would work.  Im still stuck at the moment.

Thanks,
Rich

---

### Post by Juninho1 on 2008-01-14
Hi Rich - did you resolve this?

Iam getting the same.

I have tried various ocmbinations on Gutsy to disable the asking of the nm-applet keyring password.

I've seen suggestions to disable roaming but then I am unable to connect to my wifi (it just sits tehre and does nothing!).


Hmmm

---

### Post by RichTJ99 on 2008-01-15
Hi,

I never found an answer & it is still pretty annoying.  i am guessing the next version of Ubuntu will fix that issue.  Please let me know if you end up solving the mystery!

Thanks,
Rich

---

### Post by Juninho1 on 2008-02-11
I've just found this ->

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html](http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html)

haven't tried it yet but it looks liek the answer!

---

### Post by corney91 on 2008-02-11
> **Juninho1 said:**
> I've just found this ->

[http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html](http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html)

haven't tried it yet but it looks liek the answer!
Just to let you know - Seahorse is included by default in the upcoming Hardy Heron release.

---

### Post by stchman on 2008-02-11
> **RichTJ99 said:**
> Hi,

I would like to try to install the "libpam-gnome-keyring" package in order to fix a problem I am having with my auto login.  I do not see this option within the Synaptic package.  

I have also tried: 

sudo apt-get install libpam-gnome-keyring

This is my result:
rich@rich-laptop:~$ sudo apt-get install libpam-gnome-keyring
[sudo] password for rich:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rich@rich-laptop:~$


Any ideas on how to proceed?

Thanks,
Rich

I am assuming that you want this as to not have to unlock the keyring with a wireless connection.  I have a tutorial on this.

[http://www.stchman.com/keyring_password.html](http://www.stchman.com/keyring_password.html)

Hope this helps.

---

### Post by RichTJ99 on 2008-02-12
Unfortunately this didnt seem to work for me.

My root password is different than my user password.  My user password is the same password as my keyring password.  

I tried to install:

rich@rich-laptop:~$ sudo apt-get -y install libpam-keyring
[sudo] password for rich:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libpam-gnome-keyring instead of libpam-keyring
libpam-gnome-keyring is already the newest version.
0 upgraded, 0 newly installed, 

Nothing was installed & then I added the code ;  @include common-pamkeyring & saved, rebooted but I still get the prompt.

---

