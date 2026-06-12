---
title: "sudo...what is it and how do you use it?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-11
Ive been having trouble updating my older version of ubuntu because of password issues.  I try to use the GUI update manager but is asks for a root password, and i dont know what it is. I have tried my user password, defined during install, but this does not work.

I have heard of a way to temporarily use root permissions by entering "sudo" in the command prompt (not sure what its called in ubuntu) but i am the type that if i dont know what it is and how it works, i will not understand.   I just converted to Helldows XP, and are really enjoying ubuntu.Can someone help me with this issue?

---

### Post by Nythain on 2007-06-11
sudo stands for "super user do" i believe, could be wrong though

basically its a command you throw in front of other commands in your terminal (or menu entries or just about anythign really) that will run the command with temporary root privelages.

it will ask you for a password, wich should be your user account password ( at least the password for the first user created when you installed ubuntu... there are ways to add other user accounts to the sudoers list but im not familiar since i have a single user desktop pc)... as you type it, it wont show you typing it for security reasons, but its inputing it none the less.

example use in terminal - sudo apt-get (option)(update, upgrade, install, etc)

it has a couple variants for running graphical apps from the cli
gksudo - gnome
kdesu - kde
you use those variations when you want to run a graphical app with root access from the command line
example- gksudo gedit /path/to/file
will open up a file with gedit, after it asks you for the password, with root access... usefull for editing system conf files

---

### Post by johnny4north on 2007-06-11
here is a site howto sudo - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ITdrummer on 2007-06-11
I am running a single user ubuntu install.  As i said, the primary user password i entered during the install, works when i log into the gui, but will not work as the root password?  Any ideas on why this is?

---

### Post by LollYouSuckZor on 2007-06-11
> **ITdrummer said:**
> I am running a single user ubuntu install.  As i said, the primary user password i entered during the install, works when i log into the gui, but will not work as the root password?  Any ideas on why this is?

When you have to be root, type

```

sudo su

```

it will ask for your password, type it in and you'll be root :)

---

### Post by Bachstelze on 2007-06-11
This is what most users are confused by.

[center]**sudo is *not* su.**[/center]

Got it ? :p The fact that the user can use sudo has nothing to do with root. When you run a command with sudo, you are temporarily becoming root but without logging in. This is *very* important ! And this is precisely why your password is not working if you want to login as root. It would pretty much ruin all the security improvements behind sudo if any user who has sudo rights could login as root.


Long story short : the sudo password doesn't work for logging in as root. You don't need to, anyway.

---

### Post by LollYouSuckZor on 2007-06-11
> **HymnToLife said:**
> This is what most users are confused by.

[center]**sudo is *not* root.**[/center]

Got it ? :p The fact that the user can use sudo has nothing to do with root. When you run a command with sudo, you are not temporarily becoming root. You stay yourself, but sudo grants you the administrative permissions. This is *very* important ! And this is precisely why your password is not working if you want to login as root. It would pretty much ruin all the security improvements behind sudo if any user who has sudo rights could login as root.


Long story short : the sudo password doesn't work for logging in as root. You don't need to, anyway.

Dont confuse him.


Sudo Su

Enter password

Your Root, you'll only be root while in terminal, so when you close it, and need to be root again, just type Sudo Su

---

### Post by nsleiman on 2007-06-11
> **ITdrummer said:**
> I am running a single user ubuntu install.  As i said, the primary user password i entered during the install, works when i log into the gui, but will not work as the root password?  Any ideas on why this is?

Its the password you use to log in :)

---

### Post by ITdrummer on 2007-06-11
when i try inserting my user password it does not accept.  It says "wrong password"

---

### Post by Nythain on 2007-06-11
ok, you are running ubuntu and not kubuntu i take it right?? lets hope so... do me a favor... open up a terminal and type this
```

gksudo synaptic

```
it should pop up a window that says something along the lines of "Please Enter Your Password"
at this window type the password of your user account
if that works and it lets you in, yay, do me a favor and forget anything anyone ever told you about SU... bad mojo unless you know what you are doing, and always use the sudo (or gksudo) commands when you need root access.

if the password doesnt work, then i fear you might have somehow removed yourself from sudoers, or removed yourself from the admin group.

im not to familiar with how to make a user be able to use sudo, but im willing to look it up and help you if i you need, as long as you promise to forget about that su command :)

---

### Post by Nythain on 2007-06-11
ps, linux is VERY case sensitive, so make sure your caps lock isnt on (you have no idea how many times i've done that, specially since i dont have leds on my keyboard)

---

### Post by Catsworth on 2007-06-11
Sounds like you're having the same problem that I have with every fresh Ubuntu install.

In order for you to be able to use the sudo command you need to be correctly set up in the /etc/sudoers file.

Check out Psychocat's information here: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ITdrummer on 2007-06-11
I am currently at work and will try your advice as soon as i get home.  

thanks for everyones help.  I am a student pursuing a Computer Information Systems degree and im just trying to teach myself all the stuff i wont learn in school(pretty much every thing i will actually use in the real world)  Linux and C programming are high on my list.  So thank every one for their help. This place is great. Microsoft could learn a few things from linux users!

---

### Post by Catsworth on 2007-06-11
> **ITdrummer said:**
> [...]Microsoft could learn a few things from linux users!

Learning's a busy two way street, just a shame that one lane is full of pot holes :)

---

### Post by warcriminal on 2007-06-11
There is an article at;

[http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO](http://www.goitexpert.com/entry.cfm?entry=SUDO-and-GKSUDO)

That explains what sudo is and what gksudo is and how you can use them.

---

