---
title: "L10 laptop - power status incorrect"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by davidU on 2006-04-04
```
L10 laptop - power status incorrect
```
Sorry if this is cross posting, please excuse my wanderings as I do tend to get lost in the forums.  I posted this originally in Laptop Support but no one posted a reply, so I removed the post and brought it here. Hope this is the right place.
 
I have just installed Ubuntu on my Toshiba L10 laptop.

The power status information/icons indicate that I am running on battery when I am running on mains.
If I unplug the mains cable - the power status information remains the same, indicating that the battery is flat when it is fully charged. Even if I boot on battery it's still the same.

I have read a solution to this problem under another post, but I cannot understand the Linux speak used by the poster.

I posted to the thread and asked for help, but no-one has replied in 24 hours so I'm making this a fresh thread.

Below - the solution posted by Crayoneater - that I cannot understand:

Originally Posted by Crayoneater
i had this same problem, and i fixed it by using the kernel boot option:

acpi_os_name=Microsoft Windows 2000

you have to fiddle around with different windows version such as:
Microsoft Windows 2000
Microsoft Windows 2000.1
Microsoft Windows XP

that fixed my problem...i tried Microsoft Windows XP and the battery sort of worked, but when i used 2000 it works perfectly.

EDIT: I have an Acer Aspire 5002WLMi by the way, and i spent a long time messing around with those dsdt files, and finally came across this solution that didn't require any messing with files or anything....just a simple boot option...make sure to try all of the os names, because some might work better than others....

My questions here are:

What is the kernel boot option and how does one access it ?
What am I supposed to do once I have access to it, to see what the acpi_os is ?
And then how do I change it to one of the others ?

On another issue, when I type su at the terminal I get asked for the password. The only password I have set is my user password, but this doen't work.  I get the message "Authentication failure".  What am I doing wrong ?
](*,) 
regards DavidU

---

