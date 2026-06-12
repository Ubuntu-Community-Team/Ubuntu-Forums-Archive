---
title: "User Privileges and Security?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by nwkegan on 2007-08-06
After reading a bit, I've seen many places mention having complete administrator access is dangerous, and that for security reasons, having multiple user accounts, one for accessing and changing data, and another for browsing is the best option. Now I know how to create user accounts, but could someone explain the best way to keep ME from screwing things up, and keep my system secure as well. What privileges should I give an "every day" browsing user account?

I'm sorry if you get asked this type of question a lot, I'm very new and trying to learn, and while there are many resources out there, the forums seem to be the best source of information for specifics.

In all honesty I'm just really confused with all the terms such as "root" and "bash", etc. I've been using windows FOREVER and was very familiar with it and it seems using linux turns my entire world upside down.

Thanks to anyone who helps.

---

### Post by Jimmyfj on 2007-08-06
I can't see the need for a user for each task you do on the system - As long as your every day user isn't granted Administrator rights, or member of the root group, I see no danger in the default user made during install. As long as you only do the administrative tasks from a terminal window, and remember to close that window after finishing your work there should not be any need for more than your ever day user.

---

### Post by milosz.galazka on 2007-08-06
Hello, If you create regular account for yourself and use root account via sudo only when necessary it will be ok.

I will explain this in that way:
On my computer two accounts are used for peoples:
one is for me and second one is for my sister

Now if I want to install something or change system configuration I am using sudo to gain root privileges. That's all

---

### Post by nwkegan on 2007-08-06
I see. How do I turn off all administration rights from this account? Also, how do I "logout" once I gain administration privileges. I used the gksudo command and closed out of the terminal, and it didn't ask me for a password when I reopened and used it again. Or am I missing something?

also, is there a hotkey to close a window? like in windows there's ctrl W.

forgot to say thanks for your help!

---

### Post by NRW2001 on 2007-08-06
a standard user account is fine and gives you global usability, but restricts you from damadeing your system.  you must provide a root password to edit/configure system files from a root login or "sudo" command.  your other users you might want to lock down but that is a completely different question in itself. your standard install is just like a standard admin install in windows cept if you need to install any progs... (the password for the account you created initaly upon install is your root password unless you change it later with "sudo passwd ######" at a terminal)

---

### Post by bodhi.zazen on 2007-08-06
If you are new to Ubuntu I suggest you read this : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by nwkegan on 2007-08-06
thank you all for your replies, bodhi: I will definitely check that out, thanks.

just one question, I was editing my grub entries because I wanted to change the order in which they appear, and I got this error when I ran the command "gksudo gedit /boot/grub/menu.lst"
> 
GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

it worked, and I was able to edit the file, but I was wondering if I should be concerned about this error? A quick google search revealed other people having a similar message, but I was unable to find a solution

thanks.

---

### Post by bodhi.zazen on 2007-08-06
that message is a reported bug , no need to worry.

---

