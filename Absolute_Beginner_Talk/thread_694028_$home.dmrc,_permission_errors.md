---
title: "$home/.dmrc, permission errors"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by revolutionaction on 2008-02-11
I get this message when I try and log into my user account. "User's $HOME/.dmrc file is being ignored.   This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

I'm sure I know how this happened, I was fooling around trying to network mine and my friends computer so we could share files and I gave him write access to my home directory, k, good, now I just wanna figure out how to fix it!    Directly after that pop up leaves my screen, the os starts loading up and I get this message "could not look up internet adress for josh. This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding josh to the file /ect/hosts on your system"

I've looked around these forums, tryed the steps and they didn't seem to work. I tryed this command in the recovery mode prompt "chmod 644 /home/josh/.dmrc" and it didn't do anything after restart. I stumbled upon this blog post that says essentially the same thing ([http://www.itcamefromtheinternet.com/tech/archives/53-Home-.dmrc-File-Being-Ignored.html](http://www.itcamefromtheinternet.com/tech/archives/53-Home-.dmrc-File-Being-Ignored.html)) but it doesn't fix the logging in problems either. 

This problem has been giving me quite the headache for the past couple of hours, In my files its marking some folders with x's and saying I dont have permission to view their contents. any help would be greatly appreciated!

---

### Post by revolutionaction on 2008-02-11
update: I checked through my file system after putting those commands into the terminal and its made my entire home folder unreadable, giving me the same permission denied screen.

---

### Post by taurus on 2008-02-11
Boot into recovery mode from GRUB menu and run

```
chown -R josh:josh /home/josh
chmod -R 755 /home/josh
chmod 644 /home/josh/.dmrc
shutdown -r now
```

---

### Post by revolutionaction on 2008-02-11
Awesome! I've bypassed the "User's $HOME/.dmrc file is being ignored." problem,

Now I'm left with this on start-up "could not look up internet adress for josh. This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding josh to the file /ect/hosts on your system", and beyond that I'm not allowed to view alot of the folders I want to, mainly my music folder and other things that my friend had transfered over to my new installation. I've come to the conclusion that while trying to figuire out how to network our pc's, I massacred mine by doing a lot of alterations where I didn't know what I was doing and royally messed up the permissions of my system. Alot of the important folders have "x" icons in the bottom right of their folder icon, and when I try to go into these folders I get a permission denied prompt. Now, how do I go about setting my permissions back to default ??

---

### Post by revolutionaction on 2008-02-11
I'll try that, thanks taurus : D

---

