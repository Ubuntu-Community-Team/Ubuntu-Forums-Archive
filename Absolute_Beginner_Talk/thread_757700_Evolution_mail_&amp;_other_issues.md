---
title: "Evolution mail &amp; other issues"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by ddvanrooy on 2008-04-17
Hi All!

I'm totally new to this Linux thing, just busy transplanting from WinXP (running dual booting at the momnet), and there are a few snags, and an interesting learning curve:

1.) Evolution mail: I was used in MS Outlook to be able to set pop-up reminders for appointments as well as tasks due. In Evolution there seem to be an "alarm" function only with scheduled appointments, and not for tasks, but even so I seem not to be getting any of these pop-ups? Am I missing something somewhere ???

2)   Under WinXP I used to keep all my personal stuff on another partition, separate from the normal c:\ - drive. After installing the dual booting system Ubuntu/XP I found that Ubuntu saw this partition, but there seem to be some security issue - when I look at "properties" for the files in this folder is says the owner is "root" and I cannot change anything. How do I change this ownersship?

3) on the same terms, I was used to be able (under XP) to place links (shortcuts) on the desktop to several files and folders. I find that the only files I can do this with now seems to be stuff in my home folder, and nothing else? Any ideas how to solve this ?

4) Wifi: I tried to install an application called Kismet * Iwas used to use Netstumbler). Anyway, it seemed like everything downloaded & installed, but then it seemed to dissapear. I'm not sure how to actually run this app. I'm having similar mysteries with other apps I tried to install.


Thanks so long
D

---

### Post by alexforcefive on 2008-04-17
> **ddvanrooy said:**
> 2)   Under WinXP I used to keep all my personal stuff on another partition, separate from the normal c:\ - drive. After installing the dual booting system Ubuntu/XP I found that Ubuntu saw this partition, but there seem to be some security issue - when I look at "properties" for the files in this folder is says the owner is "root" and I cannot change anything. How do I change this ownersship?

Is it an ntfs drive? You should install ntfs-3g and ntfs-config to enable write support. You'll probably find this fixes problem #3 too 

> **ddvanrooy said:**
> 4) Wifi: I tried to install an application called Kismet * Iwas used to use Netstumbler). Anyway, it seemed like everything downloaded & installed, but then it seemed to dissapear. I'm not sure how to actually run this app. I'm having similar mysteries with other apps I tried to install.

If you hit alt+F2, the app launcher panel will come up. Just type the application name in there, but remember it's case sensitive. It should auto-complete the name if you're typing it properly. Once you've figured that part out, you can add it to your applications menu by right-clicking on the menu and selecting "edit menus". Or you could right click anywhere on the desktop and select "create launcher"

---

### Post by unutbu on 2008-04-17
Hello ddvanrooy, welcome to ubuntu!

Regarding 2: Let's say your personal stuff is in a partition mounted at /stuff.
Try
```

sudo chown -R ddvanrooy:ddvanrooy /stuff 
```

This will change the owner and group ownership of each and every file in /stuff. 
If you have more than one user who needs access to /stuff, then there are other ways to fine tune this -- group memberships, or more permissive read/write/execute attributes... But you'll have to describe what you want.

Also, change ddvanrooy to whatever your username is on the machine.

Now regarding 3: This is also an ownership issue. You can't create files inside of directories that you don't have write permission. Maybe the easiest way to make a symbolic link in such a case is to use the command line:

```
sudo ln -s [target-file-or-dir] [symbolic-link-name]
```

Also, for any command you see that someone suggests you type into a terminal (such as the ones above) it is highly advisable you understand what the command does before you type it. 

One way to find out what a command does is to type into a terminal
```

man <command>
```

where <command> is replaced with sudo, ln, chown, (or even man), or whatever.

---

### Post by woaiwojia on 2008-04-17
Do you use ubuntu 7.04?
if you install ubuntu 7.10 or later, it maybe OK

---

### Post by perfecttao on 2008-04-17
> If you hit alt+F2, the app launcher panel will come up. Just type the application name in there, but remember it's case sensitive. It should auto-complete the name if you're typing it properly. Once you've figured that part out, you can add it to your applications menu by right-clicking on the menu and selecting "edit menus". Or you could right click anywhere on the desktop and select "create launcher"

Or you could install Gnome-Do - then use the windows key and the space bar and it will "find" the appropriate application....

---

### Post by alecz20 on 2008-04-17
> **woaiwojia said:**
> Do you use ubuntu 7.04?
if you install ubuntu 7.10 or later, it maybe OK

I also think so... I have full write support on the windows partition from Ubuntu 7.10... uTorrent writes there for now:)

---

### Post by ddvanrooy on 2008-04-17
Ok thanx so far; It seems I have a few things to go on. 
Just to reply on some replies: I'm using Gutsy 7.10 & the partition I'm using to share my personal stuff between XP & Ubuntu is in Fat 32 format.

Hey, any takers for my question #1 re Evolution, hahaha ?


Ok thanx again
D

---

### Post by avtolle on 2008-04-17
I've not fiddled with Evolution for quite some time, but IIRC, to get the popups for the appointments, one must select the calendar to set the alarm. HTH.

---

### Post by rune0077 on 2008-04-17
For question number 1:

When you create the event, and set the alarm, remember to hit save. If the alarm is set correctly, a small bell-icon should be visible in front of the event in the calendar. If you're still not getting the reminder, try going to Edit > Preferences > Calendars > Alarms and make sure that the calendar in question is checked here.

---

### Post by ddvanrooy on 2008-04-18
Hi there !

I tried this:

Regarding 2: Let's say your personal stuff is in a partition mounted at /stuff.
Try
```

sudo chown -R ddvanrooy:ddvanrooy /stuff 
```


and it seems to find all the files good and well and tries to change the ownership. However I get a reply "Operation not permitted"

Any ideas ?


D

---

### Post by ddvanrooy on 2008-04-18
Hi and thanx for the reply:

>>When you create the event, and set the alarm, remember to hit save. If the alarm is set correctly, a small bell-icon should be visible in front of the event in the calendar. If you're still not getting the reminder, try going to Edit > Preferences > Calendars > Alarms and make sure that the calendar in question is checked here.[/QUOTE]



I do get the little bell icon and everthing on the calendar, but no reminders / alarms are coming. 
Since this function is quite important to me ( I suffer from that disorder....hmmm.. what was  it called again ???), if I cant get Evolution mail to do this, is there any other application which would do the trick ? How about Kmail - can I run it in the Gnome desktop. I checked Thunderbird and it doesnt seem to have a calender...


Cheers
D

---

### Post by rune0077 on 2008-04-18
> **ddvanrooy said:**
> Hi and thanx for the reply:
I do get the little bell icon and everthing on the calendar, but no reminders / alarms are coming. 
Since this function is quite important to me ( I suffer from that disorder....hmmm.. what was  it called again ???), if I cant get Evolution mail to do this, is there any other application which would do the trick ? How about Kmail - can I run it in the Gnome desktop. I checked Thunderbird and it doesnt seem to have a calender...


Cheers
D

The reminder should pop-up in your panel, so you also need to make sure that you have the notification-area in your panel (but if you got the network-manager and such visible, it is already there).

You can always use Kontact (which include Kmail and a calendar program) if you don't mind having all the KDE libraries installed. It's a really neat program too. The only reason I don't prefer it to Evolution, is that it looks a little out of place on the Gnome desktop.

---

### Post by unutbu on 2008-04-18
cron is a flexible, general purpose scheduler that can run arbitrary programs at arbitrary times or dates. It can be set to flash an image on your screen, play a sound, send an email, or all three...

---

### Post by ddvanrooy on 2008-04-18
Does anyone have an idea where Evolution store the mailbox / contacts etc ??? I'm  contemplating to use another mailer, but will have to export of course

D

---

### Post by rune0077 on 2008-04-18
> **ddvanrooy said:**
> Does anyone have an idea where Evolution store the mailbox / contacts etc ??? I'm  contemplating to use another mailer, but will have to export of course

D

Yeah, it's just a hidden folder in your home directory: /home/<nameofyourhomefolder>/.evolution

(remember the . in front of evolution)

It's all in there, neatly arranged into the appropriately named folders (like mail, adressbook, etc).

---

### Post by unutbu on 2008-04-18
/stuff is a FAT32 partition. There is no concept of file ownership in FAT32.
(Sorry, I had assumed /stuff was ext3 at the time of my first post.)

---

### Post by unutbu on 2008-04-18
Regard 2: /stuff might have been mounted as read-only. You can tell by issuing the command
```

mount
cat /etc/fstab
```

Post the results.

---

