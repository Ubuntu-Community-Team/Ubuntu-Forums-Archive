---
title: "Some Questions"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Starcraftmazter on 2006-12-14
Ahai.

I'm coming from 7 or 8 years experience on various microsoft platforms, switching to linux for reason obvious to anyone who knows anything about computers.

As such, you will see me asking many questions :D

Here are some to get me started:

1. On my current windows install, there is me with thunderbird, and 2 other users using 2 identities on outlook.

I wanted to switch everyone to thunderbird, but the profile manager just doesn't run on windows, does it work properly on ubuntu, and is it convenient?

If not, please suggest other solutions to this problem - numerous users needing one email program.

Also, can thunderbird import mail from outlook?

2. I have some logitech mice, atm I use mx 410 laser, and it has very nice forward and back buttons on the side, will ubuntu recognise and make use of these?


Thats probably the most important stuff for now.

Thanks.

---

### Post by md5 on 2006-12-14
For the first question, I don't know the answer. For the second Yes it will, but you will have to configure it.

---

### Post by Starcraftmazter on 2006-12-14
Configure it how?

---

### Post by md5 on 2006-12-14
1. By yourself in console 2. To look for software in the internet which would make it for you 3. Drivers could be enough

---

### Post by Starcraftmazter on 2006-12-14
Ok.

I also need to set up a pppoe connection, where about do I do that?

---

### Post by md5 on 2006-12-14
There will be a nice configuration tool in ubuntu menu.

---

### Post by ciscosurfer on 2006-12-14
> **Starcraftmazter said:**
> Ahai.

I'm coming from 7 or 8 years experience on various microsoft platforms, switching to linux for reason obvious to anyone who knows anything about computers.

As such, you will see me asking many questions :D

Here are some to get me started:

1. On my current windows install, there is me with thunderbird, and 2 other users using 2 identities on outlook.

I wanted to switch everyone to thunderbird, but the profile manager just doesn't run on windows, does it work properly on ubuntu, and is it convenient?

If not, please suggest other solutions to this problem - numerous users needing one email program.

Also, can thunderbird import mail from outlook?

2. I have some logitech mice, atm I use mx 410 laser, and it has very nice forward and back buttons on the side, will ubuntu recognise and make use of these?


Thats probably the most important stuff for now.

Thanks.Hello!

To answer your first question: the Thunderbird profile manager works quite well on my end (you can setup a testing scenario for yourself, creating multiple profiles, to prove to yourself that it works)

To grab Thunderbird, you can use the Apt GUI front-end **Synaptic **which can be found on your menu under **System > Administration > Synaptic Package Manager**.  Click Search and type in: **Thunderbird**.  Right-click **Mozilla-thunderbird** (as well as **Mozilla-thunderbird-enigmail**, if you want GPG support) and choose **Mark for installation**.  Now click **Apply**, then in the dialog that pops up, click **Apply** again.  Synaptic will install Thunderbird Mail to your **Applications > Internet** menu.

You can either use the Terminal or the Menu Icon to start a Thunderbird session.  In a terminal you can use```
mozilla-thunderbird
```Or, Alternatively, you can select **Thunderbird Mail** from the **Applications > Internet menu**.

On your first-run, you'll want to set up all necessary networking setting (incoming and outgoing servers, usernames/passwords, etc.)

On subsequent runs, you can either use the following syntax in a Terminal or create a Laucher to open up the Profile Manager for you```
mozilla-thunderbird -profilemanager
```To create a Laucher for your Desktop or Panel, right-click the Desktop, choose Create new launcher and fill out the necessary details, using **mozilla-thunderbird -profilemanager **as the command to execute in the command field.  You can then use this Launcher to start up the Profile Manager.

Once the Profile Manager has opened, you can fill out the necessary details that I'm sure you're aware of already (they are similar, if not identical, to the choices given in the Windows version).  Some interesting things to point out would be: If you uncheck the box that says "Don't ask at Startup", then you merely have to start mozilla-thunderbird (either from terminal or through the graphical menu) and the profile manager will appear each time (before) you open Thunderbird, to allow users to choose their profile.  This option may be the more ideal option to use.  In the end, it's up to you.

The following link (discussing Thunderbird for Windows--the methods and options are the exact same on Ubuntu) will describe how to import your mail (and setting, if you like) from Outlook: [http://support.real-time.com/tbird/outlook_import.html](http://support.real-time.com/tbird/outlook_import.html)

To answer your second question: if you do an Advanced Search on Ubuntu Forums, and throw in keywords like mouse mice customization, etc., it will return a plethora of results that will help guide you in your quest to make full use of your logitech mx410 mouse.

If you have any further questions, please don't hesitate to ask! :-)

---

### Post by ciscosurfer on 2006-12-14
> **Starcraftmazter said:**
> Ok.

I also need to set up a pppoe connection, where about do I do that?Begin a new thread and title it **Questions Regarding PPPoE** :KS

---

