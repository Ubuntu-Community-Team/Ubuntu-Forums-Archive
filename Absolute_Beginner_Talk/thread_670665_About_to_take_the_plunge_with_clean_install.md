---
title: "About to take the plunge with clean install"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by poetmayhem43 on 2008-01-17
Hey there,

I'm about to reinstall my Ubuntu system and overwrite my XP partition.  
Before I do can you let me know if I'm about to do this incorrectly:

I've copied my ubuntu installation to an external drive using rsync.  Then I'm going to reboot with the live cd and install using the 'entire hard disk' option.  

Once installed I am going to copy the old /home folders from my external drive to the new installation.  

As far as I understand this will then put all the old users and settings back into the new one?

Let me know if I'm right / wrong  / missing steps as I don't want to make a complete sony bravia of things.  

Once reinstalled I'm then going to setup a separate home partition using:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by crjackson on 2008-01-17
> **poetmayhem43 said:**
> Hey there,

I'm about to reinstall my Ubuntu system and overwrite my XP partition.  
Before I do can you let me know if I'm about to do this incorrectly:

I've copied my ubuntu installation to an external drive using rsync.  Then I'm going to reboot with the live cd and install using the 'entire hard disk' option.  

Once installed I am going to copy the old /home folders from my external drive to the new installation.  

As far as I understand this will then put all the old users and settings back into the new one?

Let me know if I'm right / wrong  / missing steps as I don't want to make a complete sony bravia of things.  

Once reinstalled I'm then going to setup a separate home partition using:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")


Sounds like you've got it under control...  Let us know how it turns out.

---

### Post by zipperback on 2008-01-17
If you are just looking to get rid of the Window$ partition why not just delete the partition, and then resize your Ubuntu partition to use the new added space.

- zipperback
:popcorn:

---

### Post by poetmayhem43 on 2008-01-18
> **crjackson said:**
> Sounds like you've got it under control...  Let us know how it turns out.

Sadly I can't.  The Ubuntu installation was at the end of the drive so I can't resize it.  

Anyway, plunge taken & I did do something wrong I guess.  After copying the user folders back into the home directory it doesn't allow me to login as a user as /home/[user] doesn't exist.  

What have I missed?

---

### Post by vikram on 2008-01-18
you need to create the users again. if you use the same user name, when you log on then all user preferences, data etc should be available

---

### Post by poetmayhem43 on 2008-01-18
> **vikram said:**
> you need to create the users again. if you use the same user name, when you log on then all user preferences, data etc should be available

I created them again, but it still comes up with the error message.  

Where can I find the error log file?  I'll post it up and see if that can help anyone see what I've done wrong.

---

### Post by vikram on 2008-01-18
not sure where the errors land up but one place to look at is 

tail -f /var/log/messages

what error do you get . also does it allow you to create and log in as a brand new user and create a brand new /home/user dir?

---

### Post by poetmayhem43 on 2008-01-18
> **vikram said:**
> 
what error do you get . also does it allow you to create and log in as a brand new user and create a brand new /home/user dir?

Reading the error a bit more carefully (.xsession-errors) I figured out where the problem was...  
When I copied the Home folder to my external drive I seem to have set all the permissions to root access only.  :lolflag: Turning the permissions to the folders and files one by one got me a bit further into the login, but it's going to be very time consuming.  

Is there a way to change set permissions to the all files & folders within in one go?

---

### Post by GGLucas on 2008-01-18
There is, you can use the -R (recursive) option on chown or chmod for that.

sudo chmod 666 -R /home/user (or whatever you're using, 666 is not really secure, so.. might wanna use 644?)
sudo chown user -R /home/user

---

### Post by ubuntu-freak on 2008-01-18
If you wanna do almost everything you did in Windows, try my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
It's how I set my system up. Thought I'd share the info.
 
Nathan

---

### Post by poetmayhem43 on 2008-01-18
> **GGLucas said:**
> There is, you can use the -R (recursive) option on chown or chmod for that.

sudo chmod 666 -R /home/user (or whatever you're using, 666 is not really secure, so.. might wanna use 644?)
sudo chown user -R /home/user


Many thanks! 666 didn't get any further work, but 644 did get a bit nearer.  I feel that it's almost there...below is the xsession-error it throws up now.   

"(process:7807): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:7811): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Could not set mode 0700 on private per-user gnome configuration directory `/home/john/.gnome2_private/': Operation not permitted"

Any ideas?

---

### Post by GGLucas on 2008-01-18
Did you try changing the owner of the files to your new user with chown ? As long as your user owns the files, there should be no problem logging in, or at least there shouldn't be. Can you try logging into single user (recovery) mode (it will give you a root commandline terminal, no GUI), it's in the GRUB menu, and then doing:
sudo chown -R john:john /home/john

Does that fix it?

---

### Post by poetmayhem43 on 2008-01-18
No joy I'm afraid.    Any other ideas?

(Don't worry about risky suggestions because as long as I don't rewrite the external backup I can get back to this point no trouble. and hey... if I do break that I'm sure my gf doesn't need her Uni essays anyways :p)

---

### Post by GGLucas on 2008-01-19
My best guess would be that changing the permissions on all of the files screwed something up because it needed to be a different permission, if you have the files with all the original permissions, then just delete the ones you have in your home directory, (sudo rm -rf /home/john && mkdir /home/john), then copy all the files to the directory again, and chown them to john (sudo chown -R john:john /home/john), without changing the permissions (copying the files can be done from a live cd, but be sure to be in the install when you chown, or it won't know the user john (you can either boot into recovery mode, use Ctrl+Alt+F2 at the login prompt to switch to a virtual terminal, or create a different user and log in as that)

If that doesn't work (the original permissions, but owned by the new user, which basically restores it to the exact state it was in before), then it's likely not a permissions issue.

---

