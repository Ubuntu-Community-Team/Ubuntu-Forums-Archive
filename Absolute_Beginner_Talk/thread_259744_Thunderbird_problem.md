---
title: "Thunderbird problem"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by patslap on 2006-09-17
Hi

When opening Thunderbird I get a message stating that 'This folder is being processed. Please wait until processing is complete to get messages.'

I've been using Ubuntu for around 3 weeks, and haven't seen this message before. I've only 1 email in my inbox, but it takes about 5 seconds to process, and once the processing has finished the 'Get mail' button doesn't respond.

To d/l new messsages I have to click on the down arrow on the edge of the Get Mail button and select 'get all new messages'.

Can anyone help me as to why this is happening and suggest a way to fox this?

Thanks

patslap

---

### Post by crossedout on 2006-09-18
Have you compacted your folders recently?  It is located under File->Compact Folders.  It should be done routinely, TB recommends weekly but if you have alot of email you should think about doing it more often than that.
If that doesn't solve the problem then you'll need to delete all the .msf files in your profile folder.
It would probably be wise to start cateloging your messages in folders other than Inbox as well, if you haven't started doing so already.

-Xout

---

### Post by patslap on 2006-09-18
Files are compacted. Only 1 email in inbox. I've deleted all .msf files from 5 folders within my profile folder.

But I still get this problem. Tbird pauses for about 10 seconds now, and the Get Mail button doesn't respond.

Any ideas?]#-o

---

### Post by Sprogg2001 on 2006-09-18
Even though you may only have one email, if you have used Tbird for a while and had emails back and forth if you didnt compact your folders on a regular basis this will cause a problems no matter what size your inbox is, and even compacting them now may not save you! 

Think of it as a wearing well worn shoe's after so many miles walked, you begin to feel the bumps in the road. 

my suggestion is head over to thunderbird forum and read the section on performance. 

[http://kb.mozillazine.org/Performance_%28Thunderbird%29](http://kb.mozillazine.org/Performance_%28Thunderbird%29)

and then read the trouble shooter on compacting 

[http://kb.mozillazine.org/Compacting_folders#Compacting_doesn.E2.80.99t_seem_to_work](http://kb.mozillazine.org/Compacting_folders#Compacting_doesn.E2.80.99t_seem_to_work)

go through the steps to resolve your problem.

Then try a nifty little extension called automsgselect that will auto compact your folders in the future and save you the trouble of going through this again ;)

---

### Post by crossedout on 2006-09-18
Looking at your screenshot, it appears as though you are using global inbox under Local Folders for your account(s).  If so, Make sure TB is checking the account Edit->Account Settings->*Each Account*->Server Settings->Advanced, check the box for "Include this server when getting new mail".


-Xout

---

### Post by patslap on 2006-09-18
Great.

Thanks for the suggestions, crossedout and Sprogg2001.

I will try these tomorrow. :D

---

