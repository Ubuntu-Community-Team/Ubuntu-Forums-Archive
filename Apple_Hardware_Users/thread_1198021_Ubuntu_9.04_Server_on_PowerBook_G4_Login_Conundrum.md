---
title: "Ubuntu 9.04 Server on PowerBook G4 Login Conundrum"
date: 2009-06-26
forum: Apple Hardware Users
---

### Post by teamofemus on 2009-06-26
Hi there,

I've installed Ubuntu before, but never Ubuntu Server. For some reason, once I've completely completed the installation and am at the login line (ubuntu login:), I cannot login. I enter my username ("adam", as assigned in the install wizard), press enter, and type in my password (as I also assigned) and I get a "Login incorrect" error.

I've reinstalled three times, trying different username and password combination in setup and again upon bootup, but no dice. 

If you have ideas about what fatal mistake I'm making, please let me know before I throw this afternoon project at a solid brick wall. :D

---

### Post by tgalati4 on 2009-06-27
Plug into the network and try to log in from another machine on the network.  You may have to guess the IP if it's automatically assigned.

Perhaps you created a typo in your password and repeated it.  So now you have a user with a difficult password.

You could boot with a live CD, mount the internal disk drive, go to /etc and edit *shadow* and wipe the existing key.

Next time you boot you should just hit return for the password.

If you are able to login then reset the password:

sudo passwd adam

---

### Post by johntoups on 2009-07-07
I'm experiencing the same issue. Fresh 9.04 server install on a G5 (3 times, using both 'acceptable' complexity passwords and a simple four-letter test, i.e. john/john as uname/pass).  I am unable to login at the console as either john or root with that password.

A live CD installation worked fine.

---

### Post by johntoups on 2009-07-07
FYI - ssh to that boxen does not happen either.  So, no console, no ssh.  No love.

I am confused.  I will attempt to wipe the shadow password file for this account, but I don't expect that to be the problem.  I will also attempt to create a password for root, and see if the admin user created through the install process is simply not allowed console access by default.  Unless there is a better way to check that directly?

---

### Post by johntoups on 2009-07-07
Found this: [http://ubuntuforums.org/archive/index.php/t-1126463.html](http://ubuntuforums.org/archive/index.php/t-1126463.html).  

Will update this thread if it works.

---

### Post by johntoups on 2009-07-07
All bettah!  See my notes on the other thread (listed above).

---

### Post by ibookg4_user on 2009-07-21
Hi, I am having the exact same problem, re-installed 4 times. I have tried the fixes but I cant get it working.

I get into rescue mode with Linux rw init=/bin/bash.

Now at: root@(none):

Then I type adduser john, when it comes to entering the password it says, passwd: Authentication token manipulation error, passwd: password unchanged, try again y/n ?

I try many times, but doesnt work, so this means the user wasnt added properly? or the user is added but the password is blank?

I want to go into visudo and  duplicated the root user sudo permission line for my new user.(As suggested by "johntoups" (thnx)) Once in VI I cant figure out how to save the file? and I dont know now if the user John exists?

I even downloaded version 8 and thought I'd give it an install, but during the installation it said that the cd-rom wasnt detected and it needed drivers from a floppy. So I gave up, and went back to 9.

I am using a iBookG4 with cd-rom, 30gb hdd.
I am using the Powerpc releases.

If anyone has some ideas, I would be very gratefull!:D

---

### Post by ibookg4_user on 2009-07-21
UPDATE:

just typed in visudo and see that the changes of the user john has been saved.

So now I tried logging in with john, but when I added john I couldnt type in a password, it wouldnt accept it. So i type in john and leave pass blank...login incorrect.

Any ideas?

---

### Post by johntoups on 2009-07-21
ibookg4_user:

Verify, please, that you ran 'pwconv' after booting in to rescue mode, and before trying to add the user?

---

