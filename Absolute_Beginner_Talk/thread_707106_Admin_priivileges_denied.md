---
title: "Admin priivileges denied?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by peter1608 on 2008-02-25
I have been using Ubuntu 7.10 for a couple of weeks, on a Gateway laptop with a dual boot setup alogside Vista.  By clicking on the 'Places | Computer ' menu option I was able to enter my password and access my Windows user files.  But yesterday it failed to recognise my password.  I tried many times, so I know it was not a simple keyboard error, and I also checked the caps lock was off.

I then tried the administration menu, to see if my user had somehow been denied access, but of course the system rejected this as I couldn't enter my password to get admin privileges!

So I'm stuck.  I have a small amount of Linux experience (via Fedora), enough to know that I need to log in as root to cure such problems.  But it seems Ubuntu doesn't have a root account, or at least not one that's accessible.

I am the only user on the system, so it's not the case that someone else has disabled my account. Any ideas how I can reclaim my admin privileges?

Thanks for any help

Peter

---

### Post by Arkenzor on 2008-02-25
First, since you can still log in I'll assume your password is still the same and the problem is elsewhere.

Anyway, here are a few things you should check:

- Try running a command as root in the command line with "sudo command". If this works then it will mean your graphical sudo program is the source of the problem, which would definitely baffle me. But it's still better to try... Anyway, if it fails you may be able to get some information from the error message.

- Assuming the command-line sudo didn't work either, you should take a look at your /etc/sudoers file (it's the file that determines who is able to use sudo, and in what conditions). Unfortunately, it's locked for reading and editing by normal users, so you'll have to boot from a live CD to check it.

If you can't see anything obviously wrong with your sudoers file (like it's empty or whatever), then you should post its contents here so we can try and find the problem.




As for the standard "su -" root login method, yeah it's disabled by default because the sudo model is considerably safer (like you can restrict some users to only using sudo with some specific commands, and a cracker can't simply try to guess your root password and break in).

---

### Post by peter1608 on 2008-02-26
Thank you for this response

It seems I can run sudo commands from the command line. I was able to copy the contents of my sudoers file by using:-

sudo less /etc/sudoers

and subsequently to load my Windows files by typing:-

sudo mount /dev/sda2 /media/disk

So whatever the problem is seems to be confined to the graphical interface.

But another weird problem surfaced last night.  When typing in the GUI some of the keys are corrupted.  For example, typing 'qwertyuiop' returns 'qwerty456*'.  There are many such errors, to the point where the whole GUI is unusable.  This could, of course, explain why I am unable to enter my password correctly, although it accepts the password at logon.

I also recall that a few days ago it stopped the quick burst of sound it previously gave out when loading.

When I boot from the live CD all these problems disappear.  Something on my system  seems to be hopelessly corrupt, and I wonder if the only solution is to reinstall the operating system. Or have I unwittingly installed a different keyboard layout? Am I being too pessimistic?  If so, how do I recover the situation?  If not, is it just a matter of backing up my data then reinserting the live CD and repeating every step?
 

Probably not relevant now, but the contens of my /etc/sudoers file:-

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Peter

---

### Post by bbqsandwich on 2008-02-26
> **peter1608 said:**
> But another weird problem surfaced last night.  When typing in the GUI some of the keys are corrupted.  For example, typing 'qwertyuiop' returns 'qwerty456*'.  There are many such errors, to the point where the whole GUI is unusable.  This could, of course, explain why I am unable to enter my password correctly, although it accepts the password at logon.

That sounds like it could be a function-lock/num-lock problem on your keyboard. The uiop might keys have been switched to a numpad configuration, which would explain why you're getting 456* instead. There should be a Fn-lock key on your keyboard, or maybe Fn-F11 or Fn-F12 or something will fix it.

See here for more info:

[http://sillydog.org/forum/sdt_6574.php](http://sillydog.org/forum/sdt_6574.php)

[http://hardware.mcse.ms/archive43-2007-7-232933.html](http://hardware.mcse.ms/archive43-2007-7-232933.html)

& try Googling "fn lock" & things like that... hope that helps.

---

### Post by peter1608 on 2008-02-27
[QUOTE=bbqsandwich;4407961]That sounds like it could be a function-lock/num-lock problem on your keyboard. The uiop might keys have been switched to a numpad configuration, which would explain why you're getting 456* instead. There should be a Fn-lock key on your keyboard, or maybe Fn-F11 or Fn-F12 or something will fix it.

Quite right.  I feel a little ashamed that the solution turned out to be so obvious, but then hindsight is a wonderful thing.

I had indeed inadvertently turned the function lock on (Fn-Scroll lock).  I am not used to laptops, and so was not aware of the role of the function lock.  Indeed, having such a key at the bottom left of the keyboard where I expect to find the Control key is a major irritant, and has lead to many typing errors!  

The surprising aspect to me is that the function lock survives reboot.  It must be saved somewhere in the GUI configuration, as it was not a problem when using the command line, nor when using Windows.  Neither was it apparent during logon, presumably before the GUI was fully loaded.

Thanks for all the help.

Peter

---

