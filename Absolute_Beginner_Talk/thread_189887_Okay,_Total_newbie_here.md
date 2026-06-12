---
title: "Okay, Total newbie here"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by jaccav on 2006-06-05
I loaded Breezy onto my secondary computer, a Dell Laptop.  I was able to partition the hard drive to leave Windows intact (no cracks).  

How do I log in as root?  How do I get to the command line?  Is this the same thing as terminal?  

I have used the command prompt in windows before.   I'd like to tinker with Ubuntu and see how well my needs are met by it. If I can duplicate everything I do in Windows, I can save myself some money on my next computer.  Besides, I like having a new toy to play with.

---

### Post by kb3hkg on 2006-06-05
with ubuntu root privelages are granted through sudo on the command line, this will use the same password as your user account. It is possible to setup a seperate root account if you so desire. to get to the command line you can use Terminal or any other console program you would ike.

---

### Post by sweeper on 2006-06-05
[QUOTE=jaccav]I loaded Breezy onto my secondary computer, a Dell Laptop.  I was able to partition the hard drive to leave Windows intact (no cracks).  

How do I log in as root?  How do I get to the command line?  Is this the same thing as terminal?  

I have used the command prompt in windows before.   I'd like to tinker with Ubuntu and see how well my needs are met by it. If I can duplicate everything I do in Windows, I can save myself some money on my next computer.  Besides, I like having a new toy to play with.[/QUOTE]


I am a total noob too but you don't need to log on as root usually using the command sudo takes care of that. Command line is using the terminal yes.

---

### Post by Donshyoku on 2006-06-05
By default, you cannot login as root in Ubunut.  You can create a root password (the account exists without this), then you have to set it to be able to login from GDM (the Gnome login screen).

However, most people reccomend using the "sudo" command for anything you would do as root.  Applying "sudo" before the command allows the user to have temporary root privileges.

The command line and Terminal is the same thing.  Technically, I guess you could use the command line without the X graphical system started, but Terminal is basically a visual representation of that.  The Terminal is where you enter commands, and where you would add "sudo" to the front of a command where you to need root privileges to access it.

If you still need to login as root from GDM, post back and I'll give you all of that info.  For now, "sudo" should suit you fine and it is always good to stay out of the root account as much as possible.

---

### Post by jaccav on 2006-06-05
Thanks folks.  I'll check into it.  I wasn't sure, because I was entering commands to have my Windows partition show up, but I couldn't get it to work.  I thought I was in the wrong place.  I have some pretty intense spreadsheets in excel, and i wanted to open thim in open office and take a peek.

I'm thinking I'm going to like it in here.

---

### Post by kb3hkg on 2006-06-05
good luck, and welcome to the community.

---

### Post by Ptero-4 on 2006-06-05
And if you want to get temporary root access to a GUI app use gksudo.

---

### Post by kb3hkg on 2006-06-05
and if you use kde then it is kdesu

---

