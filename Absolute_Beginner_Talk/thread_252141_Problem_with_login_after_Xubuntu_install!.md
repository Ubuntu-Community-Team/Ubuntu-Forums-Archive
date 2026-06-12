---
title: "Problem with login after Xubuntu install!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Elvenfoot on 2006-09-06
Hello

I'm a completly noob on linux, this is my first time using it! I downloaded the alternate xubuntu install disc and installed it on my 64ram pc.

The instalation was ok.

After the install when i choose the "linux normal mode" on Grub it gets on a login thing. But on the instalation i didnt chosen any login, just chosen my pass for adm things.

What should i do?

---

### Post by fransk on 2006-11-08
Hi,

in Linux systems you have always to login in.
There is no way doing like windows, when your system is open for everyone who start it up.

That seems a little anoying at first, but after while you'll see that is safer than other ways.

(I'm not Linux expert, but a new entusiast)

By.

---

### Post by redpants on 2006-12-11
I'm having the same issue.  I installed from the xubuntu 6.10 alt install disc and chose OEM setup.  Everything seemed to work fine, but I don't remember specifying a username, just an admin password.  But after the install completed, it brings me to a login screen.

I thought that maybe whatever I typed in first would take as the new login name, but it gave me an error (incorrect user name or password, and it tells me to make sure I type in the right case).  So I tried admin and administrator with the admin password I used.  I also tried root as the password just to see what would happen.  I even tried the password I specified earlier as my login name and password.  Nothing works.  Did I miss something?

---

### Post by RockoTDF on 2006-12-11
Log in as root and create yourself a regular user.

---

### Post by redpants on 2006-12-11
How do I login as root?  I tried root for the login name, but don't know what to use for the password.  The admin password I specified during installation did not work.

---

### Post by nickburns on 2006-12-11
You stated that you...

> but I don't remember specifying a username, just an admin password

to login as root use root as user and the password you set during install.

---

### Post by redpants on 2006-12-11
That's what I meant by the admin password didn't work...I tried root as the username and the password I specified at installation time and it didn't work.  I even tried root with an uppercase R just to see and it didn't matter

---

### Post by redpants on 2006-12-12
Any ideas, or do you think I should try reinstalling?

---

### Post by tudawggz on 2006-12-12
Try No username and your password and see what happens.  It may have a password for a zero length username.

---

### Post by cday on 2006-12-12
Okay, there is a couple of things you have to do.

1st you must enable root by going into terminal and type 
         **sudo passwd root**
then give root a password

2nd while logged in as your regular user goto system, administration, Login Window.  Then click on security tab and check "Allow local system administrator login"

You can now login as root

---

### Post by nickburns on 2006-12-12
thanks for the post cday, but the problem these users are having means that they cannot login, and therefore cannot get to a terminal.

---

