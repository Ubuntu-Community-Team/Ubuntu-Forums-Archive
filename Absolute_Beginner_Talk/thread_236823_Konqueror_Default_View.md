---
title: "Konqueror Default View"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Satyr451 on 2006-08-15
Is there a way to set the default view for Konquerer to Detailed List View?  I understand that I can go to the view menu and choose view mode -> detailed list view, but I have to do that every time and it's annoying.  What I want to happen is when Konquerer opens the view is already set to detailed list view.  I've tried creating a new profile, setting the view mode to detailed list and saving the profile.  That works, but only for the folder that I was in at the time.  

For example, I open Konquerer, click Media View and all my hard drives come up in detailed list view.  however, as soon as I click to open a drive it switches back to icon view which is absolutely maddening.  

Using windows explorer under winXP I can accomplish this by tell it to take the currently displayed view settings and apply them as the default to ALL folders on the system.  That's exactly what I want to do with Konquerer.  Forgive the comparison to windows, but I know that OS well and in trying to make the switch I constantly wind up trying to do something in KDE that I used to be able to easily accomplish in windows. 

I've seen a few threads on similar subjects but nothing that directly answers my question.  Most revolve around a missing switch view button in dapper kubuntu.  However, if the default is icon view, I don't see why there isn't a way to switch it to default to detailed view.  Is there a text file somewhere that can be modified?

Any help out there?

---

### Post by siacs on 2006-08-15
Change the view to detailed view in View Mode first

Then  goto Settings > Save View Profile - Kubuntu File Manager > hit the save button

Restart and it should be in detailed view now.

---

### Post by Satyr451 on 2006-08-15
Thanks for your response.  

When I do that it only saves that view for the particular folder I was in when I changed the view.  

What I want to know is if there is a way to change Konquerer so that it ALWAYS uses the detailed view.  

Any ideas?

---

### Post by siacs on 2006-08-15
Try it from your home folder. Make sure there are no other tabs open or instances of Konqueror running. Make sure you save it as Kubuntu File Manager and not Kubuntu Web. 

That should change the global default. It should work, it does on mine. Any folder, tab or window I go to is detailed view by default.

---

### Post by Satyr451 on 2006-08-16
Ok, that worked!  As long as I open Konqueror to my home folder first anywhere else I go comes up as list.  

If I open it using the "storage media" link then it goes back to icon view...weird.  

Anyway, I can deal with opening my home directory first, that's usually where I'm going anyway.  

Thanks for your help.

---

### Post by siacs on 2006-08-17
Glad to help :)  

The media bug was verified fixed in KDE 3.5.3 
[http://bugs.kde.org/show_bug.cgi?id=108542](http://bugs.kde.org/show_bug.cgi?id=108542)

Try this
[http://ubuntuforums.org/showthread.php?t=79640](http://ubuntuforums.org/showthread.php?t=79640)

or like you said,just start from home.

---

