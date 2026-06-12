---
title: "rhythmbox - how to minimize to the system tray"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2006-03-04
Can I minimize the rhythm box application so that it appears only as a item in the system tray ( like gaim).

---

### Post by Qrk on 2006-03-04
Sure. On the file menu select "Close" instead of quit.

---

### Post by bored2k on 2006-03-04
[QUOTE=Qrk]Sure. On the file menu select "Close" instead of quit.[/QUOTE]
Or click on the tray icon for it to iconify.

---

### Post by bytewolf on 2006-08-14
Try "Control+W" :-)

---

### Post by NovaAesa on 2007-11-14
I know this is an old thread, but I have the same kind of problem. Sure I can minimise to tray by doing what the above posters have said, but is there a setting somewhere to minimise to tray when clicking on the close box in the upper right of the window?

I've looked everywhere but I can't find any settings for it!

---

### Post by NovaAesa on 2007-11-14
Even just a setting to minimise to tray normally (when the minimise button is clicked).

Maybe someone knows of a plugin?

---

### Post by Mogul345 on 2007-11-14
I am looking for the exact same thing as well. I'm used to Winamp where I could minimize to the system tray.

---

### Post by Inxsible on 2007-11-14
I am not sure if Rhythmbox has that, but Amarok sure does. Its been a long time since I last used Rhythmbox.

---

### Post by Ripfox on 2008-05-11
Remove Rhythmbox and reinstall it after adding these lines to /etc/apt/sources.list

> deb [http://ppa.launchpad.net/ubuntu-quickfix/ubuntu](http://ppa.launchpad.net/ubuntu-quickfix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-quickfix/ubuntu](http://ppa.launchpad.net/ubuntu-quickfix/ubuntu) hardy main

It will give a version that closes to systray upon hitting the close button.

:)

---

### Post by rabspd on 2008-05-12
Install another flexible audio player similar to KDE's Amarok, but for GTK+. It is very good and has feature you are seeking.
:guitar:

Rabi
[rabspd.co.cc]("http://www.rabspd.co.cc")

---

### Post by Ripfox on 2008-05-15
Er...the only feature he searches for was to close to the systray when he hit the "close" button. That repo has the quick fix. And you didn't even name the app of which you spoke. Do you mean Exaile? :confused:

---

### Post by kholsheimer on 2008-06-01
> **Ripfox said:**
> Er...the only feature he searches for was to close to the systray when he hit the "close" button. That repo has the quick fix. And you didn't even name the app of which you spoke. Do you mean Exaile? :confused:

I think what he meant was to update rhythmbox using this repo. Here's what I did: Added the repo within synaptic, only marked rhythmbox for update. And then I unchecked this repo again (I didn't need the other updates, I think).

Indeed, after the update, rhythmbox gets sent to tray on clicking the "close window" button.

---

### Post by olskar on 2008-06-09
I cant get this to work? Is the version in fixrepo older then the one in main perhaps?

---

### Post by WildOscar on 2008-06-20
Well thanks people!!! Never realy posted anything in the forums.. but been using them for couple of years now! :D this beats Wierdos XP help!!! hand down!

But in my honest opinion.. to have an superior OS its important the way the user interacts with the OS is different. No point having another wierdos clone! less clicks the better!

---

### Post by sgardne on 2008-06-20
This did not work for me. I did apt-get remove rhythmbox, updated sources.list, did apt-get update, apt-get install rhythmbox. No love. It still quits with the close button. Am I missing a step?

---

### Post by Ripfox on 2008-06-24
> **kholsheimer said:**
> I think what he meant was to update rhythmbox using this repo. Here's what I did: Added the repo within synaptic, only marked rhythmbox for update. And then I unchecked this repo again (I didn't need the other updates, I think).

Indeed, after the update, rhythmbox gets sent to tray on clicking the "close window" button.

Yes, if you read the thread I was the one who brought that solution to the table :)

---

### Post by Ripfox on 2008-06-24
> **sgardne said:**
> This did not work for me. I did apt-get remove rhythmbox, updated sources.list, did apt-get update, apt-get install rhythmbox. No love. It still quits with the close button. Am I missing a step?

You don't even have to remove RB. Just add the repos and sudo apt-get update then sudo apt-get upgrade and it will update RB to close to tray on exit. Then just remove the repos.

---

### Post by Ripfox on 2008-06-28
This doesn't work anymore

---

