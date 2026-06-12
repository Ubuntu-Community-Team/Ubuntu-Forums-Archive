---
title: "desktop doesn't load"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by milt49 on 2007-10-29
I have Ubuntu 7.04 (Feisty) on my PC. Yesterday I was deleting some files for Gstreamer from the bad collection (terminology?) because I was having trouble controlling whether my speakers or headphones were active. Actually I was troubleshooting that and perhaps got distracted into thinking the problem was with the audio software I was using. After deleting a fairly large number of files from the bad collection of Gstreamer (apparently there were a lot of related files) (I thought I was cleaning up my installation of Gstreamer.) I had also loaded a new media player called Mplayer. I rebooted to see if I could control the speaker/headphones controls any better. My desktop disappeared! I get the proper boot sequence through my logon screen and I can enter my user name and password. But then when I press the Enter key,  the machine loads to a blank peach colored screen with my cursor sitting in the middle of the screen as an arrow. No movement at all. Tonight I thought I would give it 10 minutes or so to see if it would make whatever connection it needs, but no go. I of course have some work on the hard drive that I really want to have that I did not back up. I booted to a new desktop with my installation CD and took a peak at my partitions. They seem to be in tact. I just need a GUI to get to the information.  I am new to Unix and do not know terminal lingo. If someone would help spelling out each instruction I would appreciate it. Thanks.

---

### Post by Denn1s on 2007-10-29
ok, try to log in in one of the real terminals, pres

CTRL + ALT + F2

enter your username and password

then try:

sudo adduser something

so we created a new user to see if its just a configuration issue

CTRL + ALT + F7

back to graphical interface, try to log in with the user you created and tell me the results

---

### Post by Crafty Kisses on 2007-10-29
Try booting into verbose mode and see where the error occurs.

---

### Post by joeycbulk on 2007-10-29
Try to login in failsafe gnome. To do this, on login screen click options then sessions. If it worked, it means that some configuration file in your home folder is invalid. You have to delete the configuration files to be able to login in default sessions. The configuration files are hidden so press ctrl + h to show hidden files and folders.

---

### Post by milt49 on 2007-10-29
> **Denn1s said:**
> ok, try to log in in one of the real terminals, pres

CTRL + ALT + F2

enter your username and password

then try:

sudo adduser something

so we created a new user to see if its just a configuration issue

CTRL + ALT + F7

back to graphical interface, try to log in with the user you created and tell me the results
After Ctrl + Alt + F2, I can enter my user name but after I enter that, at the prompt for my password, the cursor does not move. I have an alpha numeric password and I make sure my Num Lock is on. Even so, the cursor does not move even for the letters. I get a message that the password is no good. The problem is, the cursor is not moving. I am sure I am using the correct password.

---

### Post by Crafty Kisses on 2007-10-29
> **milt49 said:**
> After Ctrl + Alt + F2, I can enter my user name but after I enter that, at the prompt for my password, the cursor does not move. I have an alpha numeric password and I make sure my Num Lock is on. Even so, the cursor does not move even for the letters. I get a message that the password is no good. The problem is, the cursor is not moving. I am sure I am using the correct password.

Try doing that when it's actually booting.

---

### Post by milt49 on 2007-10-30
When I entered Ctrl Alt F2 during boot the prompt for my user name went by really fast. I tried this several times. I managed to get my user name in there a couple of times but every time the system would immediately go to the normal GUI page requesting my user name. I never did get a chance to enter my password into the start up sequence. After entering my username on the GUI page and then my password on the next screen I get the blank peach screen with my cursor shaped like an arrow. Here are a couple of messages I get during the boot sequence: 3.789927 usb1-1 device not accepting address 2 error -71; FWH not detected. I guess the first is about one of my USB devises-maybe the headphone set that is giving me problems? I don't know if the second one is helpful.Now what? Thanks for any help you can give.

---

### Post by Denn1s on 2007-11-01
enter failsafe as joeycbulk sujested by selecting sessions at the graphical login screen, if its successfull you will get a terminal, from that terminal we can find out and repair wath is whrong

---

### Post by milt49 on 2007-11-01
OK-I do get a terminal entry screen by choosing Failsafe Gnome and signing in. Now what now I do? I appreciate your help.

---

### Post by Denn1s on 2007-11-02
try

sudo adduser something

and then try to log in with the new user, if it works you can backup from there and reinstall

---

### Post by milt49 on 2007-11-02
At the sign on screen I clicked on the "Sessions" button. After I key in a new user name the  terminal window prompts for a password, When I enter a new password the terminal window gives a prompt after the name of my computer (in other words, the default prompt I got at the beginning of the terminal session.) When I restart my computer and use the new user name and password, I still get the same blank peach colored screen with my cursor shaped like an arrow. I get the same result if I use the failsafe gnome or failsafe terminal options. When I soft boot and enter the new user name and password, I get this message: "Could not find the Gnome installation. Running the "Failsafe Xterm" session instead." When I push the "Enter" key, I get the terminal window with an active cursor. Is there code I could enter into this terminal window to access my data rather than trying to go in through the GUI? Thanks.

---

### Post by milt49 on 2007-11-03
I tried startup using the recovery mode after reading in a forum how to hit ESC during boot. It went into a boot sequence. The last two lines before the prompt were: Configuring network interface OK/Setting up console font and keymap OK. The prompt shows:root@(my login name)-(computer name):~#
How can I get in this way to either fix my system or backup and scrub? Thanks.

---

### Post by milt49 on 2007-11-03
I am able to add a user using the Recovery Mode. However after that I get a prompt using the new user name:my name and I don't know what to do with that. I typed in exit and my system booted into graphical gnome mode. However at the sign in screen when I entered the new name and password that I had just set up I got a message saying: Incorrect user name or password. Letters must by typed in the correct case. All of the new info was in lower case. I tried again and got the same message. Can someone tell me how to log in from the Recovery Mode? Thanks.

---

### Post by Denn1s on 2007-11-04
hwnever you are in a real terminal and you dont have a graphical interface, you can type
```

startx

```
to enter graphical, i think you inded have a real problem since even with another user you cannot login, maybe we can help you bacup in terminal? how do you need to bacup? you can do about anything you can in graphical in that terminal. Also, if you have the live cd, you can access your files from there

---

