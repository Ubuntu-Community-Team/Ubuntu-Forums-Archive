---
title: "GIMP - Crashes While Loading/Adding/Refreshing Patterns"
date: 2013-08-06
forum: Art &amp; Design
---

### Post by amanda3 on 2013-08-06
After 3 days, countless number of hours of research, googling and trial & error on my own I am at my whits end! I NEED HELP!!! I have typed everything exactly the way it appears on my computer as not to leave any important info out. Here's what happened from the beginning:

I was using Gimp 2.8.2 and I was adding new patterns to path file:[B] Local Disk(C:) - Users - Amanda - Gimp 2.8 - Patterns 

[/B]Never had any problems before... I open Gimp after adding and organizing the new Pattern files. It is in the startup screen "looking for patterns" and an ERROR box pops up that says:[B]

ERROR: (Gimp-2.8.exe:9828) GLib- ERROR **: gmem.c:165: failed to allocate 38880000 bytes 

[/B]I <click ok> and the next box pops up and it says:
[B]
Microsoft Visual C ++Runtime Library     This application has requested the Runtime to terminate it in an unusual way. Please contact the applications support team for more information.
[/B](I have not contacted them yet only because I have always tried my best to see if I can fix it myself first... Yes, I use Forums ALOT! LOL, Learned that from all of them!!!) [B]IS THIS ERROR BOX TELLING ME THE PROBLEM IS MICROSOFT VISUAL C++ RUNTIME LIBRARY? I noticed there are 3 separate MS Visual programs installed in my PC. Why? 
*Microsoft Visual C++ Runtime Library 2008 Redistributable- x86 9.0.30729.4148
*Microsoft Visual C++ Runtime Library 2008 Redistributable- x86 9.0.30729.6161
*Microsoft Visual C++ Runtime Library 2010 x86 Redistributable- 10.0.40219[/B] 

I have tried EVERYTHING I KNOW! Let me tell you everything I've **already tried**:
*****I have taken every Brush & Pattern out of the directory. Gimp started fine. I put ALL of my Brushes BACK in and it worked fine! No prob with the brushes... I tried to put the patterns in and it crashed. It will work only when I put just a couple of folders in. I thought maybe it was a specific pattern/set so I tried them individually. It doesn't matter what set it is I put in. It seems like it's a space issue. Once I try to go past 3-4 sets it crashes on refresh and restart. I currently have 4 in it and each folder only has 2-4 patterns each. I tried to add one more folder with only 2 patterns in it and, you guessed it, it crashed!!! The 4 folder sizes in it now are **3.24MB   1.58MB   3.94MB   30.3MB** total (I had a ton & it was working fine) 
*****I have also done a disc clean up 2x and even a defrag. 
*****I uninstalled Gimp and re-installed the newest version, 2.8.6, and it made no difference. 
*****I checked the RAM here is my info on that:
[B]MY SPECS: Windows 7 - 4.00 GB RAM (3.24GB usable) System type: 32 Bit
RAM - In Task Manager/Physical Memory - 45%  (Processes: 92)  _ TOTAL_: 3317 _CACHED_: 1233 _AVAILABLE_: 1819 _FREE_: 619

Am I reading the RAM all wrong and am out of room? If so how do I go about making more room besides deleting files, picts etc as I have already done that? 
Could it be a problem inside Gimp itself? I'm sorry this is so long. I just wanted to make sure you knew everything I already tried and had all the information I was almost certain you may ask for. I sure hope someone can help. I'm going crazy! I can't afford to buy Photoshop or I would.  [/B]:-([B]
Thank You for your time...

[/B]

---

### Post by zteam2 on 2013-08-06
Hi and welcome to the Ubuntuforums. :D

Hmm, this sound really strange....

Here is some suggestions thought.

* Try renaming your gimp settings folder, if Gimp can't find your Gimp folder then it will create a new one
* Check the permissions of your folder Brush and patterns folder.  (does your user have access to them?

You can also perform a disk check just in case.

As for the Microsoft Visual C++ Runtime Library that is part of some Windows updates.

I'm not sure whetever these steps will solve your problem, but it should be a good start. :-)

---

### Post by Buntu Bunny on 2013-08-07
Yes, Amanda3, welcome to the forums.

If zteam2's suggestion doesn't work and no other answers are forthcoming, you can also try the [GIMP Forum]("http://www.gimpforums.com/").

---

### Post by amanda3 on 2013-08-07
Thank you so much for the reply! I don't know anything about the Gimp file/folder system and how it works. Is there any way you could maybe point me in the right direction to perform some of the things you're suggesting? If not I understand completely. Either way, I thank you for the assistance you've already given! :)

---

### Post by amanda3 on 2013-08-07
Thank you for welcoming me! And thank you for the suggestion to try the Gimp Forum. I will definitely give that a try as well! :)

---

### Post by zteam2 on 2013-08-08
> **amanda3 said:**
> Thank you so much for the reply! I don't know anything about the Gimp file/folder system and how it works. Is there any way you could maybe point me in the right direction to perform some of the things you're suggesting? If not I understand completely. Either way, I thank you for the assistance you've already given! :)

Yes of course!

Since you say you have had already found the patterns folder, I did assumed you had found the main Gimp folder too (it's simply the folder just above that one) ie [B]C:\Documents and Settings\username\.gimp-2.8\

Try to rename that folder and see what happens, if Gimp starts normally you may try to copy your patterns folder from the renamed Gimp folder. If gimp crashing after that, try to download some others patterns, if that works, I assume your patterns folder is simply broken. Try downloadning some new patterns to your new patterns folder and see what happens.

 
[/B] Also check that your user does have access to all the files inside the patterns folder (go to **Start**, and then click **My Computer**.On the **Tools** menu, click **Folder Options**.Click the **View** tab.In the **Advanced Settings** section, click to clear the **Use simple file sharing (Recommended)** check box.Click **OK**.)

Then right click your patterns folder and select Security -> Permissions and make sure your user does have read access to your patterns folder
[h=4]Hope this helps you  :popcorn:[/h]

---

### Post by amanda3 on 2013-08-11
Ok! Tried all of those suggestions. No Dice :( This is so frustrating... I even tried Gimp Forums and still have no response. I just don't understand.....stumped :(

---

### Post by zteam2 on 2013-08-12
> **amanda3 said:**
> Ok! Tried all of those suggestions. No Dice :( This is so frustrating... I even tried Gimp Forums and still have no response. I just don't understand.....stumped :(

You can also try to perform a system restore if Gimp worked good earlier. [B]Please note that will restore your system (except for pictures, and documents and other personal files) back to how it was at the date you select.
[/B]
If you are using Windows 7:

Click on start and type system restore (or whatever it is called on your language) click next and select a date then Gimp worked for you and click next.

If you using Windows XP

Follow these steps.

[http://support.microsoft.com/kb/306084/en-us](http://support.microsoft.com/kb/306084/en-us)

If this doesn't help either I suggest you to post a message on this forum as well (this is the official Gimp mailiing list, which means there's usually some Gimp developers reading it as well.)

[http://www.gimpusers.com/forums](http://www.gimpusers.com/forums)

---

