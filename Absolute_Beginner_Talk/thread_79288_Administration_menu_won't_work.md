---
title: "Administration menu won't work"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by moopa on 2005-10-19
Hello, new to linux, but trying to understand. Installed ubuntu 5.1 yesterday, as a dual boot system with Xp pro, install went well, but when i get up and running, under System->Administration-> any thing  in the following pull down menu will not work, such as "networking" or "login screen set up",etc. When I click on these, timer times out,then nothing. I want to get into "networking" to configure for connection to internet. Right now, no internet. Is there something I'm doing wrong, or a bad install? Thanks, Mark.

---

### Post by heimo on 2005-10-19
Hi! 

Let's try to get some more information about this problem.  Open terminal window (hit alt+F2, write gnome-terminal, hit run). On terminal, run this command:
```
gksudo network-admin
```
It should ask your password and then run the same program as menu System->Administration->Networking. Does it? Anything on the terminal window, errors / warnings?

Also you could try running:
```
sudo dpkg --configure -a
```
If there are any unconfigured packages (from the install), this should configure them, but normally this should do nothing.

BTW, are you using the username that was created during install? Only that user will be added to sudoers file automatically (get root / administration rights).

Cheers!

---

### Post by moopa on 2005-10-19
thanks for the swift reply, I have in the terminal this: mark@MARKNET:~$

 when I type in sudo dpkg --configure -a, i get: "sudo: unable to lookup MARKNET via gethostbyname() " same thing when i type in gksudo network-admin

when i installed ubuntu, it asked for my network name or hostname i put in "MARKNET" as that's the name of mt network on windows, 
thanks Mark

---

### Post by heimo on 2005-10-19
[quote=moopa]thanks for the swift reply, I have in the terminal this: mark@MARKNET:~$

 when I type in sudo dpkg --configure -a, i get: "sudo: unable to lookup MARKNET via gethostbyname() " same thing when i type in gksudo network-admin

when i installed ubuntu, it asked for my network name or hostname i put in "MARKNET" as that's the name of mt network on windows, 
thanks Mark[/quote] 
Oh! That's a perfect clue. Your sudo / gksudo - way to use superuser privileges is not working and I believe I know a solution. However you need to boot into revovery mode and edit one text file to do this. 

To boot into recovery mode you need to hit esc at the beginning of boot process to enter grub menu (that's a boot loader with different options). You choose recovery mode (or something like that) and if I'm not mistaken, you will get "root prompt", text mode interface with full privileges. From there you need to edit /etc/hosts file using text editor like nano.
```
nano /etc/hosts
``` 
At the top of that file you should have something like this:
```
127.0.0.1       localhost.localdomain   localhost       marknet
``` use tabulator between those fields. 
ctrl-x to exit (it will ask to save, answer y). Type *reboot* and boot normally. Hopefully this solves the problem.


EDIT: line->file

---

### Post by moopa on 2005-10-19
after rebooting in safemode, i get this : "root@MARKNET:~#

---

### Post by heimo on 2005-10-20
[quote=moopa]after rebooting in safemode, i get this : "root@MARKNET:~#[/quote]

Yes, that's good. root, as well as # tells us that you have superuser privileges and can now edit any files on the system. Did you try to edit /etc/hosts file? If not, do that (instructions above).

---

### Post by moopa on 2005-10-20
thanks for your time, but it still doesn't work, I can't do anything in Aministration

---

### Post by Underhill on 2005-10-20
Try:

# sudo visudo

And add the following: {replace_with_your_username_here} ALL=(ALL) ALL

---

### Post by mgould on 2005-10-21
It worked!  Updates are downloading - the trick to remember is that visudo loads a copy of sudoers as sudoers.tmp - you must rename it to sudoers when you save the changes.

A curious thing tho'...the prompt in Terminal after saving & closing sudoers says that the sudoers is unchanged - that was quickly tested by running visudo again, to find that the changes did in fact remain.

With Hoary, I did a expert install where updates would not work, and then I did a default install where they did...my guess is that if you install as expert, the first username created is not added to sudoers, because that is what happened when I installed Breezy in expert mode (I wanted partition control).

HTH

m

---

### Post by heimo on 2005-10-21
[quote=mgould]
With Hoary, I did a expert install where updates would not work, and then I did a default install where they did...my guess is that if you install as expert, the first username created is not added to sudoers, because that is what happened when I installed Breezy in expert mode (I wanted partition control).
[/quote] 
Correct. :) If I remember correctly, expert mode asks to set root password, which default install does not. So when you do expert install, you can use su to become root, which you can't do after defaul install.

Glad you got it working, thanks Underhill!

---

### Post by moopa on 2005-10-21
[QUOTE=Underhill]Try:

# sudo visudo

And add the following: {replace_with_your_username_here} ALL=(ALL) ALL[/QUOTE]

where do i type this,in terminal?

---

### Post by moopa on 2005-10-21
when bootingin recovery mode, this error is noted "Temporary failure in name resolution"

---

### Post by moopa on 2005-10-21
typed sudo visudo, and get " unable to lookup MARKNET via gethostbyname()"

---

### Post by mgould on 2005-10-21
Did you happen to do the default install when you installed Ubuntu?


Heimo - If you do a default install, I know that the root password is autogenerated, and I was able to go into user manager and change the root password, but the system itself does not tell you the root password, correct?  If so, how would you know to be able to su it?

---

### Post by moopa on 2005-10-21
i believe so

---

### Post by mgould on 2005-10-21
Puzzling - The one default install I did I had no problems logging in and making changes via the GUI, once I realized that I had to enter ***my*** password, not the root.

For this fix on this time around - all I did was su root, run visudo, made sure I saved as sudoers (***not** sudoers.tmp*).  Since I am a linux noob, I just went and reinstalled ubuntu (did not really set up house yet...), but I am sure that the more learned here would help you find another way.

---

### Post by Underhill on 2005-10-22
[QUOTE=moopa]typed sudo visudo, and get " unable to lookup MARKNET via gethostbyname()"[/QUOTE]

Issue this command: sudo hostname MARKNET

---

### Post by moopa on 2005-10-22
[QUOTE=Underhill]Issue this command: sudo hostname MARKNET[/QUOTE]

i get the same response:unable to lookup.....

---

### Post by moopa on 2005-10-22
i think maybe a reinstall is in order, after all I've got absolutely nothing to lose...since i've never been on the net or downloaded a single file...

---

### Post by moopa on 2005-10-22
reinstalled with a new hostname( the one I tried before was the name of my existing winxp network:MARKNET), now all is fine,  able to get on the net,everything seems to be working properly...now all I gotta do is read,read,read to learn this new system....thanks for all the replys. Mark

---

