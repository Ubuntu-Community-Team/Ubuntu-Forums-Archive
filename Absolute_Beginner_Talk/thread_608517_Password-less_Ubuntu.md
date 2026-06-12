---
title: "Password-less Ubuntu"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by bigstoo on 2007-11-10
Is it possible to run Ubuntu without a password?

I have changed the settings so that my user is automatically logged on at startup. However, once I am logged in, I still get asked for a password to unlock my keyring as I am using wireless networking.

The laptop is shared by the whole family, and it is a bit annoying for everybody to have to keep typing in passwords.

I have installed libpam-keyring in an attempt to remove the request for a keyring password, but it doesn't work. I assume that's because I have it set not to ask for a password at login.

It would be great to be able to remove most of the passwords altogether (except, of course, for root access).

---

### Post by IamAcoconut on 2007-11-10
> It would be great to be able to remove most of the passwords altogether (except, of course, for root access).Well, that's what they're for! You're asked for a password, when a program needs to be run by root user in order to perform it's tasks correctly (or at all).

Root account is disabled by default in Ubuntu meaning that you cannot log in as root, but you use 'sudo' instead. Installing programs and altering advanced system settings can only be done by root. _Only way to disable password prompts is to become root yourself._ Which is a really bad idea.

PS. Why don't you use accounts for different users? They're not difficult to set up, and each account can be personalized to mach the needs of a particular user.
PPS. I am not quite competent to explain the detail right now - I'm sure somebody else will - yet 'passwordless linux' is an oxymoron. Linux is not MS Windows. It is for people who are aware of the need for security, as you will soon be. Even Windows XP encourages user not to grant administrative priviliges to ordinary user accounts, but it's a commercial product for the masses, so it cannot force it's users to think.

---

### Post by matthewcraig on 2007-11-10
I do not think you want to do what you are asking to do.  Your password is both for the graphical login and the network login.  A weak password -- or no password -- will allow anyone on the Internet or your WiFi network to log into your machine.  There are scripts on the Internet run that try to break into your computer 24 hours a day, 7 days a week.

In regards to your multiple users, you should take a look at the new fast user switching in the new Gutsy Gibbon release.  I think that may help out your family.  ...Just let them know the imporatance of passwords when they set up their accounts.

---

### Post by TheWizzard on 2007-11-10
> **bigstoo said:**
> Is it possible to run Ubuntu without a password?

I have changed the settings so that my user is automatically logged on at startup. However, once I am logged in, I still get asked for a password to unlock my keyring as I am using wireless networking.

The laptop is shared by the whole family, and it is a bit annoying for everybody to have to keep typing in passwords.

I have installed libpam-keyring in an attempt to remove the request for a keyring password, but it doesn't work. I assume that's because I have it set not to ask for a password at login.

It would be great to be able to remove most of the passwords altogether (except, of course, for root access).

please set up your computer with different user accounts and passwords.

---

### Post by keyboardashtray on 2007-11-11
> **matthewcraig said:**
>  There are scripts on the Internet run that try to break into your computer 24 hours a day, 7 days a week.


What??! Are you being dramatic? If not please elaborate :)

OP: Expect a lot of "just don't do it"s instead of an answer on how. It's because you are breaking two of the cardinal rules that make it so you can run without Antivirus/Spybot, etc - #1 The passwords for root #2 Not as stressed but highly recommended, separate users. Really the separate users, I never used to run it like that too, but its better that way, you can have your own themes, customize your menu to your liking. It's really the way to go, and security issues aside you'll like it just for the customization and convenience that far outweighs the hassle of a password on login.

---

### Post by K.Mandla on 2007-11-11
There's a file called /etc/[sudoers]("http://linux.die.net/man/5/sudoers") that you can edit to handle permissions as you like. One of those settings will allow certain groups (you could add the whole family to such a group ... you could even call it 'family'! :p ) to run commands without passwords. I've never set up a machine like that, and if security is any concern *at all* you shouldn't, but it can be done.

---

### Post by aonegodman on 2007-12-13
Is there not a default password placed by Ubuntu upon install?

If so, what is it?

How do you change it?

Thanks for any reply.

---

### Post by mcduck on 2007-12-13
> **bigstoo said:**
> Is it possible to run Ubuntu without a password?

I have changed the settings so that my user is automatically logged on at startup. However, once I am logged in, I still get asked for a password to unlock my keyring as I am using wireless networking.

The laptop is shared by the whole family, and it is a bit annoying for everybody to have to keep typing in passwords.

I have installed libpam-keyring in an attempt to remove the request for a keyring password, but it doesn't work. I assume that's because I have it set not to ask for a password at login.

It would be great to be able to remove most of the passwords altogether (except, of course, for root access).

It should be possible to unlock the gnome keyring at the same time when you type the password to log in. At least that's how it works for me. So I suppose it should work with automatic login as well.

In Feisty I had to install some modified package to get this working, but it seems to work for me out-of-the-box in Gutsy. I think the only rule is that the keyring password must be the same as the login password.

I'll test it it works for me if I enable automatic login.

But I really wouldn't recommend removing passwords completely, that's is _very_ insecure if the machine has any internet connection.

edit: I just tested it, and indeed if I enable automatic login I have to type the keyring password for network manager. But if your machine is not a laptop I think you could just stop using Network Manager and configure the wireless connection in System/Preferences/Networking instead. That would solve the problem with Network Manager asking for keyring password..

---

### Post by seventhc on 2007-12-13
> **aonegodman said:**
> Is there not a default password placed by Ubuntu upon install?

If so, what is it?

How do you change it?

Thanks for any reply.

maybe this is what your looking for, but not sure..

go to 'system>administration>users and groups'
you will be asked for your password then you will see users and root, here you can change the root default password and change user passwords. not sure if you can set it to no password though.

highlight the user or root then click on edit

---

### Post by Aathos on 2007-12-13
It sounds to me like all you want to do is to remove the need to enter a password to access the default keyring.  You can do what mcduck said, and stop using network manager.  Network manager can be replaced with WICD, that will allow you to connect to wireless networks without having to do all the configuring manually.  WICD is easy to install, you just have to remove Network Manager first.  You can download the deb [here.]("https://sourceforge.net/project/showfiles.php?group_id=194573")

---

