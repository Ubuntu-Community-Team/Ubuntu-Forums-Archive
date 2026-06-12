---
title: "[SOLVED] Ubuntu permisions problems"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by ocean223 on 2007-08-17
Im on my second Ubuntu install.  I think what I've managed to do this time is install software un  der several different method and under different permissions.  Anything I've installed from the repositories works fine and is not a problem.  I've installed tor and vidalia form the console however and have problems. when I run vidalia it says tor has just exited aand the error log says maybe it is already running. when I run tor from the terminal it says that the config files are not owned by me.

I have used the command sudo su to become root before installing these programs. Then tying to run them as my regular user account.  As I peruse my files i notice A lot of folders with a lock icon attached.
I cannot change permissions on some of them. I'm thinking I might trash this install but I'd not like to make the same mistake in the future.  How might I uninstall programs that were installed via terminal? 

I had a similiar problem whith my external usb drive but fixed it by aping some commands I found in a thread here.

Ideas?:confused:

---

### Post by diatribe on 2007-08-17
if you installed it with the root account then you will probably have to run the pgrogram as root also, or change the permissions of the files

---

