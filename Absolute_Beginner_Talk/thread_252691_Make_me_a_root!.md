---
title: "Make me a root!"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Anthraxx on 2006-09-07
I recently migrated to Ubuntu from XP, but one of the things thats bugging me is that my account can't do anything! How can I make my account 'root' or whatever will alow me to edit all the files on my system?

---

### Post by ZennouRyuu on 2006-09-07
Well the 'root' account is disabled for logins by default. The idea is to use 'sudo [command that needs privileges]' this is a  safer way to administer your system.

For example:

If you need to edit /etc/resolv.conf which is only writable by root, you could use 'sudo vim /etc/resolv.conf'

it will ask for your password (for you user account) and then you will be off.

---

### Post by Lord Illidan on 2006-09-07
> **Anthraxx said:**
> I recently migrated to Ubuntu from XP, but one of the things thats bugging me is that my account can't do anything! How can I make my account 'root' or whatever will alow me to edit all the files on my system?

Your account can do many things.

Use sudo for example.

Or gksudo.

And why not tell us what you want to do exactly? Editing all the files on your system can be dangerous.

---

### Post by monktbd on 2006-09-07
for security reason you dont want to be root all the time.
please read
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
for some background about ubuntus approach to root/sudo.

---

### Post by hc2995 on 2006-09-07
lol i had the same question. You dont wont to be root couse you can break linux that way (if you type a wrong code) as for using root functions type:

sudo su

youll get a password thing (its your password) after that youll get this:

root@COMP_NAME

(Sudo su works if you are compiling and need the make install command)

usually tho you can use: 

sudo COMMAND

this will grant root privliges for a brief time

---

### Post by uDanimal on 2006-09-07
I have been wondering, and now seems as good of a time as any to ask.  What, exactly, is the difference between "sudo" and "gksudo"?

---

### Post by monktbd on 2006-09-07
> **uDanimal said:**
> I have been wondering, and now seems as good of a time as any to ask.  What, exactly, is the difference between "sudo" and "gksudo"?

gksudo is used for starting graphical programs with root privileges (e.g. gedit or nautilus).
sudo for cli programs like apt-get or vi.

there can be some problems starting graphical programs just with sudo.

often there is an error message with gksudo and the session manager. this can be ignored, the started program works withou a problem anyway.

---

### Post by jimcooncat on 2006-09-07
> **uDanimal said:**
> I have been wondering, and now seems as good of a time as any to ask.  What, exactly, is the difference between "sudo" and "gksudo"?

sudo prompts you for a password on the command line

gksudo pops up a gui dialog box for you to enter your password

If you're making a script or button that runs a command from the gui, use gksudo.

---

### Post by anaconda on 2006-09-07
gksudo is for graphical programs. (it's a GNOME thing, but I heard it works also in xubuntu)

with some programs sudo can't ask your password correctly, but gksudo can... in gksudo the password-interface is graphical..

I have noticed, that sudo works also with most graphical programs

EDIT: damn I was too slow..

---

### Post by DonS on 2006-09-07
sudo will ask for your password on the command line (hiding the result)
gksudo will pop up a nice dialog with the same.

---

### Post by jimcooncat on 2006-09-07
Now that these forums are so popular, it'd be nice that when typing a reply that it prompts, "Someone's already posted an answer! You're too slow!" :-)

---

### Post by crane on 2006-09-07
I was wondering the same thing about gksudo.
I have started a bunch of graphical programs using just sudo though. I have not had any problems.
 I like when I find it funny when I see " you don't want to run as root because you could break some thing, You should use 'sudo' instead"
Isn't this a misconception? IS there really a difference?
Yes I agree you don't need to run as root all the time because of many reasons but, 
sudo rm <whatever> can still damage a system if the wrong files are removed.

---

### Post by monktbd on 2006-09-07
> **crane said:**
>  I like when I find it funny when I see " you don't want to run as root because you could break some thing, You should use 'sudo' instead"
Isn't this a misconception? IS there really a difference?


well for the one program running there isnt one in my eyes.

but it is easier to overlook having a root shell and typing some commands that screw up the system by accident than to do it when you have to add a sudo in front.

and i guess the you dont want to run as root was meant as to not be always logged in as root.

---

### Post by aysiu on 2006-09-07
When I type in my PIN number to withdraw money from the ATM machine for my bank, my bank account is vulnerable at that time, but is that any reason to also whip out the keys to my apartment, the combination for my safe, and my social security number and birthdate, too?

*sudo* confines the root privileges to the application in question. All other applications are still being run as user.

---

### Post by nothingworks on 2006-09-07
sudo -s
will keep you logged in as root for the rest of the terminal session

---

### Post by jordanmthomas on 2006-09-07
Well, since you asked and nobody really gave you an answer to your question (not exactly anyway)...

First you need to make a root password
```
sudo passwd root
```

Then, go to System --> Administration --> Login Window
Go to Security tab
Click 'Allow local system administrator login'

Now you can log in as root



But you should never do that

---

### Post by aysiu on 2006-09-07
> **jordanmthomas said:**
> 
But you should never do that Which is why no one gave an exact answer to the original question.

---

### Post by nothingworks on 2006-09-07
sudo -s
will keep you logged in as root for the rest of the terminal session

---

### Post by OffHand on 2006-09-07
> **jordanmthomas said:**
> But you should never do that

> **aysiu said:**
> Which is why no one gave an exact answer to the original question.

:mrgreen:

---

