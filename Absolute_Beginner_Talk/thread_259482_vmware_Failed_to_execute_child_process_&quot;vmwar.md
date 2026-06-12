---
title: "vmware: Failed to execute child process &quot;vmware&quot; (permission denied)"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by braheem on 2006-09-17
> could not launch menu item

vmware: Failed to execute child process "vmware" (permission denied)

i get this error when i click on the vmware server icon

please help:(

---

### Post by bulldog on 2006-09-17
Try

sudo /usr/bin/vmware-config.pl

---

### Post by AndreasHegedusIsMyDadYo on 2006-09-17
Ohk.

---

### Post by bulldog on 2006-09-17
> **AndreasHegedusIsMyDadYo said:**
> I LOVE MAH DADDY YOIZZLES! Andreas Hegedus is a gangsta gg word monkey tonkey time! TRUE DAT YALL DONT MESS WIT DIS YALL DONT MESS WIT MY MONKEY TONKEY WURD!

My Dad can beat up yo dad! But he wouldn't WHOAAAA my dad can beat up yo dad but he wouldnt!

Frustration??
I know a good psych..............want his fonenumber?

---

### Post by braheem on 2006-09-17
> **bulldog said:**
> Try

sudo /usr/bin/vmware-config.pl

sudo: /usr/bin/vmware-config.pl: command not found

---

### Post by bulldog on 2006-09-17
Try this howto.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Just install it again and vmware will uninstall the broken one.

I used this one and works like a charm.

---

### Post by braheem on 2006-09-17
> ibrahim@700M:~$ sudo /usr/bin/vmware/vmware-config.pl

> The configuration of VMware Server 1.0.1 build-29996 for Linux for this running
kernel completed successfully.


went through a few things, i dont know what it was doing but it worked however, still gave me the same error in the end.

> vmware: Failed to execute child process "vmware" (permission denied)

what does my error mean?

---

### Post by bulldog on 2006-09-17
It's a permission issue.
Did you alter some dir's which vmware suggested?

It could be you placed files where you haven't the rights to to use.
Install goes with sudo and you use vmware as a user I mean.

The only thing I altered whas the place where my virtual machines where put.
/home/bulldog/vmware

The rest was determined by vnware install and you only have to enter the options it gives.

---

### Post by bulldog on 2006-09-17
ibrahim@700M:~$ sudo /usr/bin/vmware/vmware-config.pl

This is not right it should be in /usr/bin/vmware-config.pl
You made a vmware dir.
Don't know if that's the issue though.

I should simply reinstall and let vmware do the uninstalling.

Just accept all vmware suggested exept where to put your virtual machines.
I think you should have them in your /home but that's personal.

---

### Post by jsglazer on 2007-03-11
It's simply an issue of file permission.  Open a console as root and grant 'chmod a=rwx [filename]' permission to the following files:

/usr/bin/vmware
/usr/lib/vmware/lib/wrapper-gtk24.sh
/usr/lib/vmware/bin/vmware

Also, verify you've installed: libc6-dev (via Synaptics) and synchronized your clock with NTP support (right-click the clock on your menu bar, choose 'Adjust Date and Time', and click 'keep clock synchronized...'

However, I imagine there is a security issue with this approach.

---

### Post by SaltyCrak on 2007-11-27
> **braheem said:**
> i get this error when i click on the vmware server icon

please help:(

go to system > preferences > main menu
then selec system tools on the left. double click on the vmware player icon then add "sudo " in front of the command. ie. "/usr/bin/vmplayer" becomes "sudo /usr/bin/vmplayer"

that worked for me :)

---

### Post by i5sfe on 2008-01-28
jsglazer I want to thank you for your response, I also had the same problems but did not know what files needed permission. Now vmware works!!!

---

### Post by nic.no1 on 2008-04-20
I had the same issue. I could not start vmware.
[FONT="Courier New"]$ /usr/local/bin/vmware results in Permission denied[/FONT]
I extracted the VMWare workstation tar file under my regular user account and I run the installation script using sudo. The issue was, that the files got extracted with the permissions set from my user account (umask 007) and the files have been installed with those permissions. After extracting the tar file with root permissions (sudo) and re-install VMware everything worked fine.

---

