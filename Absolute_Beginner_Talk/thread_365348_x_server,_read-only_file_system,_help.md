---
title: "x server, read-only file system, help?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by faedrake on 2007-02-19
I have Ubuntu desktop installed on top of Unbuntu 6.06 server.  I want to use it as a php development platform at some point, but for now I'd just like the gui to be stable.

Occasionally when booting up I get the "Failed to start the X server (your graphical interface)." error.  I have searched the forums thoroughly.

I try sudo dpkg-reconfigure xserver-xorg and chose all standard options (nv for my nvidia card).

Then I try sudo /etc/init.d/gdm restart and that doesn't work

I have also tried startx, which gives me errors in locking authority file, cannot create temp file for here document: Read-only file system

If I cold/hard reboot, sometimes I will get to the login screen with a message in a gui window saying gdm could not start because it could not write to a file (or some such).

If I cold/hard reboot again, I actually get to the desktop and everything seems to be just fine.  Peachy even.

So, why can I only get the desktop to load every ~3rd boot?  Why does my file system keep locking down into read-only?

I have completely reinstalled Ubuntu server and desktop once before, only to end up with the same results.  Can anyone help?  Vista frightens me and I'd rather never install a micro$oft product ever again. 

Thanks!

---

### Post by m94mni on 2007-02-20
Read-only file system is usually a signal that your disk is going bad.

Check the contents of /var/log/messages, /var/log/syslog and /var/log/dmesg for hints.

I think it's a bad drive.

---

### Post by faedrake on 2007-04-15
HD scans found and fixed some errors, but the X server errors persisted.  Since I am not worried about stability, I just wanted to avoid having to reboot twice every time I turned the computer on, I deleted the option in fstab to mount the filesystem as Read Only on errors.  Yet, the X server errors persisted.

I finally figured it out that if I go through the shutdown by gui or shut down by command line, the system ALWAYS has errors when it boots back up.  If I just hit the power button (rude, I know) the system starts back up beautifully.

Everything about the system runs great.  I've been using it as a server on the lan to test and play with PHP, using it to play mp3s, using it to play my midi keyboard, using it to browse the net.  I've run into zero problems with stability or errors.   I'll keep the possibility in my mind that something bad may pop up, but this solution is currently serving my purposes.

---

