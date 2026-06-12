---
title: "Login as Root/Change Folder Permissions"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Gibran on 2007-03-30
Hello. I accidentally changed the permissions on my Home folder and now it belongs to Root. Every time I log in I get a message saying some settings will not be saved because of this and I got to press OK for the system to load fully. Since I'm no longer the owner of the folder, I cannot change the permissions, so is there a way to change this back to how it was from my user or how can I login as root?

---

### Post by haricharan on 2007-03-30
you have to use sudo command like
```
sudo chown <username> <filename>
```

---

### Post by cowlip on 2007-03-30
You can login to a console to change permissions (CTRL + ALT + F1 )

sudo chown -r yourusername:users /home/yourusername
sudo chmod -r 755 /home/yourusername

If you want a graphical way, you can start up up Nautilus with root permissions: 'gksudo nautilus'

Or you can use the livecd.

---

### Post by imasickboy on 2007-03-30
If you've removed the execute permission on your home folder for everyone but root, you shouldn't be able to launch any applications, or really do anything at all. Difficult situation if you've not enabled root login prior to now.

I can't say whether or not this is your situation, but if it is, here's a solution that allows you to change permissions via nautilus, even though it seems you can't launch it:

Restart, at the login screen, choose to start in a terminal.

Then, 

sudo xinit -- :2

When it starts up,

sudo nautilus

Go to your home folder, change those permissions back to what they were.

Restart, log in as normal, and all is well. 

For easier fixes of similar mistakes, allow the root user at login, and set a password for it. I'm sure we will all suggest NOT using that login for any other purpose than to fix critical mistakes, so don't log in that way for any other reason. But it does allow for a good failsafe entry when you have a problem like this.

---

### Post by Gibran on 2007-03-30
> **haricharan said:**
> you have to use sudo command like
```
sudo chown <username> <filename>
```

Thank you for the prompt reply. I did that but I still get the dialog. I just realized it said my "$HOME" folder and it refers to the .DMRC file not belonging to the user...What can it be?

---

### Post by STREETURCHINE on 2007-03-30
have a read of this link 

[http://www.ubuntuforums.org/showthread.php?t=371052&highlight=home+dmrc+folder](http://www.ubuntuforums.org/showthread.php?t=371052&highlight=home+dmrc+folder)

there is a solution there .

the search option is a good utensil type in your error and it will take you to posts from outher users

also google your error ,it is your friend

---

### Post by Gibran on 2007-03-30
Thank you! I have already solved it with those instructions. Thanks everyone!

---

