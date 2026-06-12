---
title: "LAMP + Desktop - how to access Desktop?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Winterdream on 2007-04-02
I installed the Ubuntu Server 6.06 and then, following instructions I found in these forums, I entered this:
sudo apt-get install ubuntu-desktop
to add the Ubuntu Desktop 6.06.

It finished that but all I get is the prompt to login to the server.  How can I boot into the GUI desktop?
 
As you can guess, I am completely new to this!  Please give me some specific instructions, I've searched in vain for the answer.

Many thanks for any help.

---

### Post by airtonix on 2007-04-02
type this : 

> sudo /etc/init.d/gdm restart

then goto administration -> login window

and choose Gnome from the drop-down-menu labeled "default session"

then logout. or even try ctrl+alt+backspace to restart the gui.

hope this helps post back with results.....

---

### Post by Winterdream on 2007-04-02
I entered:
sudo /etc/init.d/gdm restart

And it replied with this:
sudo: /etc/init.d/gdm: command not found

What now?
Thanks for your help!

---

### Post by airtonix on 2007-04-02
odd... mmm

ok maybe you dont have all the packages.

maybe if you install something like..... nautilus or firefox which depends on the dekstop environment it will grab the other stuuf i think you have missing...

>  sudo apt-get install firefoxor 
>  sudo apt-get install nautilusor even
>  sudo apt-get install glomthis should grab what is required to get these gui only prgs to work....

---

### Post by cyberdork33 on 2007-04-02
you probably want to still figure out the gdm problem... but you can test for gnome, etc, by logging in with your username and password, then run

```
startx
```

That should at least get X running.

---

### Post by dca on 2007-04-02
Correct, I believe after 'startx' is entered from then on when you restart, shutdown, etc it will default to gdm....

---

### Post by Winterdream on 2007-04-02
I did sudo apt-get install firefox and sudo apt-get install nautilus - those worked.

I did sudo apt-get install glom - that was not found.

Then I tried:
sudo /etc/init.d/gdm restart
with the same "command not found" as before.

BEFORE I did the two apt-gets above, I did dir /etc/init.d/ and got this list (I had to type this but I think I got it all right):
alsa-utils
apache2
atd
bootclean.sh
bootlogd
bootmisc.sh
checkfs.sh
checkroot.sh
console-screen.sh
crom
dns-clean
evms
glibc.sh
halt
hdparm
hostname.sh
hwclock.sh
keymap.sh
klogd
loopback
lvm
makedev
mdadm
mdadm-raid
module-init-tools
mountall.sh
mountdevsubfs
mountvirtfs
mtab
mysql
mysql-ndb
mysql-ndb-mgm
networking
pcmciautils
ppp
pppd-dns
procps.sh
rc
rc-local
rcS
README
reboot
rmnologin
rsync
sendsigs
single
skeleton
stop-bootlogd
sysklogd
udev
umountfs
umountnfs.sh
umountroot
urandom
waitnfs.sh

AFTER the FireFox & Nautilus, this has been added to the list:
x11-common

I also tried entering startx and the reply is:
-bash: startx: command not found
Should there have been something before "startx" ?

Thank you, I *really* want to make this work!!!

---

### Post by Bachstelze on 2007-04-02
ubuntu-desktop does not install gdm.

```
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by Winterdream on 2007-04-02
I did this:
sudo apt-get install gdm
and then I rebooted by entering this:
sudo /etc/init.d/reboot stop

There was a message that the GUI failed and it offered to display it, so I agreed.  Now I have a screen with strange characters around the edges and this message:
"X:  cannot stat /etc/X11/X (no such file or directory), aborting.

Now what should I do, please??

Addition:
I hit ENTER and now it has this:
"The X Server is now disabled.  Restart GDM when it is configured correctly."

Please help, I am lost....

---

### Post by Winterdream on 2007-04-02
Maybe I should start over and install the Ubuntu Desktop first, then add Apache and MySQL???  Is that a better way to go??

---

### Post by Bachstelze on 2007-04-02
ubuntu-desktop does not install X either ;)

```
sudo apt-get install xorg
```

(no need to reboot, by the way)

---

### Post by Winterdream on 2007-04-02
sudo apt-get install xorg

Results in:
E: Couldn't find package xorg.

Thank you for trying to help me, what else can I do?

---

### Post by Bachstelze on 2007-04-02
Sorry, my mistake. What I told you was for Edgy. In Dapper, it's :

```
sudo apt-get install x-window-system-core
```

---

### Post by Winterdream on 2007-04-02
OK, maybe this is some progress !!  Or maybe not...

I did the sudo apt-get install x-window-system-core and that worked.

Then I did 
sudo /etc/init.d/gdm restart

Result:
"There was an error opening the theme Human
Can't open file /usr/share/gdm/themes/Human/Human.xml"

I clicked OK, got the login prompts and entered login

Gnome screen - clicked in the middle of it, and it disappeared. 

Now I have a blank screen.

Do I need to download some themes?  Or something else?

Many thanks for helping me!  I really, really want to make this work.  I bought a nice little refurbished IBM ThinkCentre for it and I have my dreams...

---

### Post by Bachstelze on 2007-04-02
```
sudo apt-get install ubuntu-artwork
```

---

### Post by Winterdream on 2007-04-02
sudo apt-get install ubuntu-artwork

I've tried, but it goes into the login screen, then the Gnome screen, then the blank screen.  Then I hit CTRL-ALT-Backspace and I'm prompted for my login again, then I get the prompt and I try to enter the sudo apt-get command... but it asks for my password again.. and then back to the login screen, Gnome, blank screen.

Round and round and round it goes, how do I get back to the prompt where I can enter sudo apt-get install ubuntu-artwork??

---

### Post by Bachstelze on 2007-04-02
When at the login screen, do Ctrl+Alt+F2 to get a command line, then you can apt-get instal ubuntu-artwork.

---

### Post by Winterdream on 2007-04-02
OK, I got the command line and successfully did the ubuntu-artwork thing.

Now I get a yellow screen that says "ubuntu" and asks for my username then password.  I haven't seen this screen before!

I enter my username and password and that brings up another new screen - it has a small thing in the middle, says "Window Manager" at the bottom, "ubuntu" at the right.  I click on it and - guess what - I'm back at a blank screen!

What next, please?  Many thanks in advance!

---

### Post by Bachstelze on 2007-04-02
Then I don't know :p Hold on a sec, I'll fire up a vmware and do the same thing so I can see if I get the same problem.

---

### Post by Winterdream on 2007-04-02
> **HymnToLife said:**
> Then I don't know :p Hold on a sec, I'll fire up a vmware and do the same thing so I can see if I get the same problem.

I've had my back to the Ubuntu computer while reading the forums and waiting for help.  I turned back to it and now there's a golden swirl pattern on the screen!  It doesn't do anything and there's no options available but it's prettier than the blank screen.

:rolleyes: 

I'm not going anywhere, please come back when you have any ideas!
Thanks.

---

### Post by Bachstelze on 2007-04-02
hmm, that's weird. Here, ubuntu desktop installed both gdm and ubuntu-artwork... Make sure your system is up-to-date :

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop
```

---

### Post by Winterdream on 2007-04-02
Thanks but I already tried that - I finally decided that I wasn't really learning anything so I ought to step back and try again.  I've installed Ubuntu Desktop **alone** and that seems to be working.  Tomorrow, I'll try to install Apache - that should only require this:
sudo apt-get apache2
Is that right?

Then I'll try to get Apache to work, if I can do that much, that will be good.

I tried to do too much too quickly without understanding enough!

Thanks for trying, I appreciate it!

---

### Post by Bachstelze on 2007-04-02
Yep, installing a desktop and then installing apache/PHP/MySQL will definitely be easier ;)

---

