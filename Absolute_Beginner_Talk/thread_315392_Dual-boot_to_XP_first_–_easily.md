---
title: "Dual-boot to XP first – easily"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-09
I just installed ubuntu 6.10 Edgy to dual-boot with XP.

My first priority was to get the family PC to boot automatically & fairly transparently to XP, so other users could carry on as usual.
I imagine this is a fairly common situation.

I Googled extensively & found plenty of Geeky threads which, as a so-far total noobie, I found either incomprehensible or, at best, daunting.

I needed a way to do it with my still-XP mindset – without command-line stuff, just clicks.

Actually, it is easy & so I list below what I did (hope I remembered it right!) in case this can be helpful for other noobies.
No doubt regulars will shout if there are any errors or no-no’s in here.  :)

There are 2 stages:
1. Getting yourself to where you can change the settings (as ‘root’)
2. Changing the settings

Start here:

1. Getting yourself to where you can change the settings (as ‘root’)

Login with your usual username & p/w
Go to: System > Administration > Users and Groups
Double-click on 'root' to open Account 'root' properties.
Select 'Set password by hand'
Choose a password for ‘root’ & enter in 'user password' & 'confirmation'.
Check OK & close that window & users settings window.

Go to: System > Administration > Login Window
Enter your usual username password (not new root password) & OK
Click on tab 'Security'
Select 'Allow local system administrator login'
Close that window.

2. Changing the settings

Click on 'Log off' button
Select 'Switch user'
Login as 'root' with new root password
Go to: Places > Computer > File system > boot > grub
Right-click on 'menu.lst' & select 'Open with text editor'
You will find (hidden in a long page of ## ##s) something like this:

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
.
.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
.
.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
.
.
.

title		Ubuntu, kernel 2.6.17-10-generic
.
.

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
.
.

title		Ubuntu, memtest86+
.
.
title		Other operating systems:
.
.
title		Microsoft Windows XP 
.
.
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

You simply need to change two digits:

Change: ‘default........0’  to  ‘default……..4’ 
    to select XP as default (priority) boot.
    (4 because XP is the 5th option, but starting from 0 not 1)

Change: ‘timeout……..10’  to  ‘timeout……..3’
   to reduce the boot-select screen time from a long 10 seconds to a shortish 3 seconds 
   (or choose any other value you prefer)

Click 'save'
Close that window
Click 'Log off' button
Select ‘Log off’ option
If screen stays black – move mouse to wake it up…
Enter usual username password to get into your usual ubuntu desk

Should be all done – try it...(at your own risk!).

---

### Post by bulldog on 2006-12-09
Now the easy methode :D 
Open your menu.lst ```
gksudo gedit /boot/grub/menu.lst
```
Enter your password.
It will open in a text editor,change what ever you want and save the file.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Done :D

It's also a good habit to make a copy of every file before changing it,just in case...

---

