---
title: "gettin nowhere fast"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-29
Something unusual has happened to my computer. The xubuntu startup screen comes up when I boot up. It starts the services and goes to the edubuntu login prompt. Then, I type in the username/password combination and it acts like it is loading, But it doesn't load, it goes back to the edubuntu login screen. I had to start in terminal mode and type startx, otherwise I wouldn't be able to use my web browser or anything...

How can I fix this and what causes it?

---

### Post by taurus on 2006-10-29
Maybe ~/.xsessions-error would tell you what's wrong with it?

```
more ~/.xsessions-error
```

---

### Post by saintj0n on 2006-10-29
I do not know what repercussions there are to a crash in linux (undeleted temp files maybe?) but I think I knopw what happened. I powered the system on and it said that the pc got too hot and powered off. I think the fan  went bad and triggered a shutdown response on the laptop. I have never replaced a fan in a laptop, I wonder how hard it would be....

---

### Post by saintj0n on 2006-10-30
The other possibility is that I simply ran out of disk space. I only have 5% of my original 20 Gigabytes left to use. I couldn't find that error file on the drive, it must be buried somewhere. How can I find it? Btw, how do you free up redundant files and temp files? Is there a disk cleaner program?

---

### Post by slimdog360 on 2006-10-30
sudo apt-get autoclean

Someone correct me if Im wrong.

---

### Post by saintj0n on 2006-10-30
The autoclean did delete some files....but still the problem of not being able to log in without going through recovery mode.:-k

---

### Post by doobit on 2006-10-30
> **saintj0n said:**
> The autoclean did delete some files....but still the problem of not being able to log in without going through recovery mode.:-k

Recovery mode is a root loggin. If you can't login at the regular screen, then you have misspelled your username or password, or possiblly deleted or changed your home user folder.

The solution is to enter in recovery, navigate to /home (cd /home) and find out what files and folders are contained there (ls -a). If there is a directory there with your old username, then you know that is still OK. Next change the password for that username (passwd <username>) and then reboot into the normal screen. Now your username and password should work.
If there is no user folder in /home then you will need to create a new one. Here is a pretty good tutorial:

[http://sayspy.blogspot.com/2006/08/ignorant-newbie-adding-new-user-under.html](http://sayspy.blogspot.com/2006/08/ignorant-newbie-adding-new-user-under.html)

---

### Post by saintj0n on 2006-10-30
I assume that the method for altering user profiles is done in terminal mode. The user administration aren't in my system menu anywhere. I have tried using adduser and I will  see if it will let me in that way. If it sheds any light, I get a weird error that says 'unable to load devfsd'. Then I put in my username when the login screen comes up. I put in my password and it loads for a second and the screen blinks and goes back to the login (maybe it can't find the software to run, I dunno.

---

### Post by saintj0n on 2006-10-30
Ok... No luck using the GUI login with the new user or any other user. At this point, I can only login as root and therefore I have no graphical package manager or user management interface. If anyone has any ideas as to how this happened or anything I can do to fix my GUI, please say so. At this point, I only know to burn the data on the drive and start completely over from scratch....:(

---

