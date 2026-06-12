---
title: "firefox questions"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2006-09-08
I have a few questions about firefox on linux compared to firefox on windows.

1. In windows I was able to move my bookmarks around(without going into the manage bookmarks menu). Like If I wanted to move my CNN bookmark into my news folder or onto the toolbar, why is there no drag and drop?

2. Firefox seems slower on linux then windows, I dual boot XP so Im using the same computer. ( I know about swiftfox but I use an intel core duo and they have no link for that in there supported processors page yet).

3. Firefox wouldnt load the add-ons and plugins page so im not sure but is there a plugin for firefox on linux so that I can close tab's individually?
--------------------------------------------------------------------------------------------
This is probly just stupid noob questions where I just need to change a few settings but I would appreciate any help.

---

### Post by blakesmith on 2006-09-08
1.  That is what the manage bookmarks option is for? 

2.  You might not be using the kernel for your system? i686 SMP I would assume... 

Try in terminal 'uname -a'... i386 would give slower system-wide performance

3.  There are some good howto's out there...

[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

Look through this catagory and maybe try Automatix.

---

### Post by Loki57701 on 2006-09-08
I just wanted to add 2 more things.

1. The remember password option that was always prompted whenever I enered a username and password somewhere. Hasnt asked me once on linux yet.

2. And finally the saved form data, I dont see that anymore in firefox on linux.

---

### Post by Loki57701 on 2006-09-08
I know about the manage bookmarks option, it just that I never had to use it before because I had drag and drop. And yes I do have the i686-smp kernel, that was one of the first things I did

---

### Post by blakesmith on 2006-09-08
> **Loki57701 said:**
> I just wanted to add 2 more things.

1. The remember password option that was always prompted whenever I enered a username and password somewhere. Hasnt asked me once on linux yet.

2. And finally the saved form data, I dont see that anymore in firefox on linux.

Did you hit the "never ask me again" button?

---

### Post by Loki57701 on 2006-09-08
no, never hit that button, because it never asked me...lol

---

### Post by blakesmith on 2006-09-08
Goto edit-->pref-->privacy-->passwords and make sure that 'remember passwords' box is checked.

---

### Post by blakesmith on 2006-09-08
I haven't felt the need to try this out myself... but aparently it is a faster firefox...

[http://www.ubuntuforums.org/showthread.php?t=142798](http://www.ubuntuforums.org/showthread.php?t=142798)

---

### Post by Loki57701 on 2006-09-08
yeah its checked.....

---

### Post by Loki57701 on 2006-09-08
yeah i know about swift fox but they go by processors and theres no download for the intel core duo.........linux-i686-smp

---

### Post by crossedout on 2006-09-08
Did you happen to create a section @FAT32 when you partitioned?  If so you can share your windows profile with your ubuntu.  That might save you some of the aggrevation of reconfiguring your preferneces.

-Xout

---

### Post by Loki57701 on 2006-09-08
I have an HP dv8000t....and they have two hard drive bays, but unfortunaley If you dont select the option to actually have two hard drives installed when you order it they dont supply you with the mounting brackettes needed to pop in a 2nd hard drive! which sucks......But I didnt wanted to loose anything on my XP side (yet) so I didnt partition my hard drive I just put in  a differnt hard drive for linux whenever I want to use it. So I dont have access to any fat32 paritions

---

### Post by crossedout on 2006-09-08
Well in that case, you could copy your win profile folder to ubuntu and place it in /home/Loki57701/.mozilla
That will copy: bookmarks, extensions, themes, any toolbar preferences etc.
The big disadvantage is that changing something in one OS won't affect the other so you'll have to keep track of what you change and add if you want FF to be identical on both OS.

-Xout

---

