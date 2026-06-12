---
title: "[SOLVED] I broke my sudo - need help!"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by hornetcoach on 2007-12-30
sudo is broken - won't run anywhere.  Anytime I try to sudo in terminal I get:  "sudoers file: syntax error, line 25"

I have read a bunch of "sudo broke" threads and thought I would ask for help before reinstalling.  I was trying to write a script that would run as sudo and found this thread...

[http://ubuntuforums.org/showthread.php?t=140696](http://ubuntuforums.org/showthread.php?t=140696)

Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------
and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: scriptpath

Since I did this (I guess I did it wrong)  I can no longer perform any sudo function anywhere in the OS. Any ideas how I can get back into this file and undo my damage? ...I should have known better...there were at least two popup warnings telling me I might break my Ubuntu if I did this.

I have tried the following:
-I don't have root enabled, and can't...anything I click in Gnome that needs sudo won't open...so login as root is out
-I loaded the live CD and can get to the /disk/etc/sudoers file, but can't edit it - I think visudo is used to edit sudoers - is there a way to invoke visudo on that file?
...it seemed like it was working - I used terminal to do

sudo visudo -f /media/disk/etc/sudoers

visudo worked, seemed to let me repair my damage, but then exited with:
visudo: sodoers file unchanged

-I tried to edit from recovery console with no luck either.

Thanks...at least I am learning a lot - right?

---

### Post by taurus on 2007-12-30
You mean you can not even edit /etc/sudoers from the recovery mode?

---

### Post by hornetcoach on 2007-12-30
Thanks for the quick response - this is what I get from the recovery console: 
I type in:
edit /etc/sudoers

I get:
 Warning: unknown mime-type for "etc/sudoers" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

I also tried: visudo -f /etc/sudoers 
and again it lets me edit the file but exits with "sudoers file syntax error, line 24"

---

### Post by taurus on 2007-12-30
Can you post your /etc/sudoers?  There is something wrong with line 24 in there.

---

### Post by hornetcoach on 2007-12-30
HEY!!!  I fixed it!

When I did: visudo -f /etc/sudoers from the console and I edited the file 
the recovery console said: 
"/etc/sudoers remains unchanged"

but...it did change!  I was rooting around and I did visudo -c to check the file and noticed  the file no longer had the lines that were gacked up and after a reboot it works great!

wow - sort of felt like loosing control of a car then getting it back.  I think I'll do a system backup now.

Thanks for the help taurus - you got me thinking about this some more.

---

