---
title: "Less passwords?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by TheOnlyMerlin on 2007-12-16
I have been using ubuntu for a little while, and I generally am really happy.  Altho0ugh one of the setbacks I have been having is the constant need to ask me for the same password over and over and over.  
So far it seems a good deal more annoying than even vista's "are you sure?" "Are you really sure?"  "are you really really sure" thing.  Because then I can just hit y / click yes.
Granted, i understand the need for it, it makes it so that certain important operations cannot run (IE through a hacker or virus etc) without my knowledge.  However so far it seems excessive.  
Is there perhaps a manager that would allow me to control what it requires the password for and what it doesn't?  (which it would seem natural for changing these settings to require a password.)

I know I probably sound like a noob and i'm sorry, because I am a noob.  Trying to change that though. And if the answer is easy, I apologize.

Thanks,
-TheOnlyMerlin

---

### Post by LaRoza on 2007-12-16
What are you doing that requires you to be root all the time?

If you want to do a lot as root, you can log on as root, if you enable it.

The password isn't asked for random actions. You have a user account, you can do anything in your home directory and everything you own. However, outside of that, the root user owns it. You can change the ownership of certain files, but that is rarely a good idea.

This is not Windows, where you are the admin by default, and the slightest action is done with full privileges, you are just a user, and if you want to act as another use, in this case root, you have to authenticate.

---

### Post by kelvin spratt on 2007-12-16
I came from windows and after a year I now understand why Linux uses passwords using a American Fraze. Its to save you from yourself. That explains it all!.

---

### Post by Sef on 2007-12-16
> I came from windows and after a year I now understand why Linux uses passwords using a American Fraze. Its to save you from yourself. That explains it all!.

:lolflag: That is very true.

Unless I am updating, uninstalling or installing an application, I rarely need to use my password.

---

### Post by asbesto on 2008-01-05
> **LaRoza said:**
> What are you doing that requires you to be root all the time?


Installing some programs?

Configuring network?

Changing some settings about running services?

Configuring restricted drivers?

changing every single thing into "System -> Administration" menu? 

I agree that is very, VERY annoying to ask for that damn password every single time I have to change something.

It's my laptop, I'm in my own home, in my LAN; I'm the ONLY user here; why it has to broke my balls like that? :confused:

My solution is:

1. sudo apt-get install libpam-keyring

2. edit /etc/pam.d/gdm adding this line at the bottom of the file:

   @include common-pamkeyring

3. restart the whole X damn thing :)

4. add yourself in the "wheel" group

5. add this in /etc/sudoers using "visudo":

    yourusername ALL = NOPASSWD: ALL

6. add those things in /etc/pam.d/sudo :

   auth       sufficient pam_rootok.so
   auth       required   pam_wheel.so
   auth       sufficient pam_wheel.so trust



AND LIVE IN HAPPINESS
===============

---

### Post by barbedsaber on 2008-01-05
so ur going to be super user all the time, I thought that was a baaaaaaaaaaaaaaaaaaaaad thing.
also, please mark this thread as solved.

---

### Post by nhandler on 2008-01-05
Ubuntu wasn't designed for the user to be logged in with root privileges all the time. This can result in many negative things. For example, all of the file permissions of any new files will be owned by root. This means that if you decide to stop using the root account all of the time, you will be required to use sudo (and enter your password) to edit these files. There also won't be any confirmation when you try to remove an important system file.

---

### Post by insane_alien on 2008-01-05
asbesto, those are all things you would do only rarely.

---

### Post by asbesto on 2008-01-05
With my solution you work just as a normal users. But, no annoying password are requested anymore to do NORMAL THINGS like installing software or configuring stuff.

Obviously I can't recommend this for a server or a shared machine, but only for a personal computer used by only a person, without important data and stuff on it (and with regular backups, first of all).

:lolflag:

---

### Post by thelatinist on 2008-01-05
This would defeat much of what makes Linux a safer and better OS, would it not?  The reason we can run without antivirus is not just because there are fewer viruses for Linux, but because accounts prevent viruses from making changes to the system.  If the user account can make changes without a password...

---

### Post by Dr Small on 2008-01-05
Just remember, when running everything as root, you have a bigger chance of deleteing system files and wrecking your system, moreso than if the system required sudo for each operation that was root.

Dr Small

---

### Post by Chayak on 2008-01-05
Keep up with your backups too.  There's a reason for not doing everything as root.  You loose a good deal of security.

---

