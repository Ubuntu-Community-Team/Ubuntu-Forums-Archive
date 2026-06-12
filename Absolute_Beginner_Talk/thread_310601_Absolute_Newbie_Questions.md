---
title: "Absolute Newbie Questions"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by pnh on 2006-12-01
Hi! I am an absolute newbie to Ubuntu.
I ordered a computer from [www.swt.com](www.swt.com) with
Ubintu 6.06 installed and I have a few simple
tasks I want to do to get up and running.
I already have some Unix/Linux experience,
but I am hitting some snags along the way.

1. When I reboot I get the gui with desktop and
this seems to be an automatic login as user1. I
assume this was setup at installation. I want to
have it log me in as myself instead of the generic
user1. Do I need to create a new account in my name
as su and then set something to load the new user on
startup? Or can I take over as su and simply edit
the name for the generic account?

2. I just want to set the correct time and date
on the machine. This should be very simple to do.

System>Administration>Time and Date

Password:password (given by the installer) 

Error
Failed to run time-admin
Wrong password.

What gives? This was the password that swt gave
me for su privledges. It should get me in as su
since it is the root password, right?

-Paul.

---

### Post by styracosaurus on 2006-12-01
You should contact them about that. If the password that you think is the correct one for superuser actions, you won't be able to solve your first problem either!

Hope they can help you, when you get the password, post back!

---

### Post by pnh on 2006-12-01
Can you tell me how to set up a new user account
or direct me to a how-to posting, assuming that
I have the correct su password?

-Paul.

---

### Post by CatKiller on 2006-12-01
**sudo** (that Ubuntu uses by default) is different that using **su root**. [This page]("https://help.ubuntu.com/community/RootSudo") explains some of the differences. So it could well be your login password that you need to use rather than the su password you've been given.

A default Ubuntu install doesn't log you in automatically. This is obviously something that the people who configured it for you have done. You could either ask them how they did it, or look for how to make that happen and do the opposite. I think ubuntuguide.org has instructions for that, but I could be mistaken.

You can create a new user from the System -> Administration -> Users & Groups tool. Unless they've moved it :)

Welcome to the community!

---

### Post by steve.horsley on 2006-12-01
Firstly you should know who to log in as. Two clues - your home directory is probably /home/username. This name should match your username given as the outhput of the command **id** at a command prompt (Accessories->Terminal), which also lists the groups you belong to. Check while looking at this list that you belong to the **admin** group.

You can check that you can log in using this user name and password by presing Ctrl-Alt-F2. This gives you a text screen with a login prompt. Give your user name and password and check that you can log in. Use the command exit to log out again, and use Ctrl-Alt-F7 to return to the GUI.

You can change your password by bringing up a command prompt and entering the command **passwd**.

Once you know you can log in using your username and password, you can change whether you are auto-logged-in from the menu System->Administration->Login Window. Go to the Security tab and uncheck the Enable Automatic Login box.

---

