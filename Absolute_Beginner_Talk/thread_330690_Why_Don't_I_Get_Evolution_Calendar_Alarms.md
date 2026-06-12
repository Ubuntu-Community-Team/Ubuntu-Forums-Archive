---
title: "Why Don't I Get Evolution Calendar Alarms?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by linux4me on 2007-01-03
I'm using Dapper 6.06 LTS and Evolution 2.6.1. 

I have set some alarms in my calendar, but I don't ever get any notifications. On the Alarms tab in Edit->Preferences I have my personal calendar checked and birthdays checked. On the General tab the option to set an alarm 15 minutes before each meeting by default is checked. I have set alarms manually and using this default, but haven't recieved any notices.

I have verified that evolution-alarm-notify is running. I am just using POP3 servers, and not any exchange servers, which appears to have been the source of this problem in the past. I haven't found a solution in the forums that applies to Dapper without the Exchange server issue. I also checked the bug list on Bugzilla.org and couldn't find any reported bugs, making it look like this was fixed for Dapper...

Can anyone tell me what I'm doing wrong or how to fix this? I really like Evolution and would like to use it, but I need the reminders to work.

---

### Post by tc101 on 2007-01-14
Alarms don't work for me either.  Maybe I don't understand how it is supposed to work.  If it is working properly is it like outlook where there is a little pop up screen telling you all the things that are due on the calendar?  If so, I never have gotten that to work.

---

### Post by linux4me on 2007-01-14
When the reminders are working, they do display a pop-up sort of like Outlook that lets you dismiss or snooze a reminder. I never got it working consistently in Dapper, but I found a solution that worked for me most of the time in you might try.

[LIST=1]
[*]Open System -> Preferences -> Sessions and click on the Startup Programs Tab.
[*]Click on the Add Button and enter the following:> /usr/lib/evolution/2.6/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Calendar_AlarmNotify_Factory:2.6 --oaf-ior-fd=51
[/LIST]

I'm not sure what all of that means--maybe someone with more experience can tell us--but I tried it in Dapper and it seemed to work. If you look below at the entry I have for Edgy, it's possible that all the flags in the line above are unnecessary, but I don't know.

I have since upgraded to Edgy, which has version 2.8 of Evolution, and noticed a couple of things. After the upgrade, the line above was still in my startup programs and the Delete option was grayed out. I discovered the way to get rid of it was to:

[LIST=1]
[*]Click Places -> Home Folder
[*]Press Ctrl+H to show hidden files.
[*]Open the .config folder.
[*]Open the autostart folder.
[*]If there are any files in the autostart folder--I had just one--right-click and choose properties to see what the path for the file is. If it corresponds to the line you added up above, you can safely delete it and will find that removes the entry from your Startup Programs Tab in Sessions.
[/LIST]

After deleting the file in the autostart folder, I suddenly had an entry in my Startup Programs that looks like this:

> /usr/lib/evolution/2.8/evolution-alarm-notify

Now I have alarms for reminders in Edgy sometimes. They consist of both a pop-up and a little balloon down in the lower panel. They don't appear consistently, though, and I haven't figured out yet what the pattern is...

---

### Post by tc101 on 2007-01-15
So it sounds like there are problems with the program no matter how you set it up.  I wonder if there is some better calendar/scheduler program?

---

### Post by linux4me on 2007-01-15
Thunderbird/Lightning are a possibility. I used them in Windows and didn't have any problems, but you'd have to search the forums to see if they work well in Linux. I'm hoping the developers of Evolution will eventually get this worked out and I can stick with Evolution. I really like it otherwise.

---

