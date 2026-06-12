---
title: "[SOLVED] Permissions of 'Recordings' could not be determined - MythTV, chmod 666 trou"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by armin00as on 2007-08-05
Hi Forum... I need some help, please:  ](*,)

While setting up MythTV on Feisty (and since MythTV wouldn't show a picture), I got the advice to check the permission of the 'recordings' folder. So I changed them...

>1. First, I made a mistake with the command, as I typed 'cmod' instead of 'chmod' (..does that matter?) :confused:

>2. Then I tried to change the permission of the entire MythTV folder by typing 
> chmod 666 /var/lib/mythtv . 
I didn't get any errors, or such, as a result...  

>3. Then, I realized that I actually should have changed the permissions for the 'recordings' folder only, and to make sure, I did the following in addition: 
> chmod 666 /var/lib/mythtv/recordings  

RESULT: 
When trying to access the contents of the 'recordings' folder now, it just shows a file of 'unknown type'. The file's property>permission settings reveal that...
>  **"The permissions of recording could not be determined."** :confused:

Well, I'm aware that I must have messed something up here, and I promise I'll read up on Unix Commands some more...  
But can someone please help me -now- and post the commands to:

   A.) ...let me fix the permissions problem of the 'MythTV' and/or 'Recordings' folder
   B.) ...allow all users (666) access to the folder, so MythTV can write into it... ??

Thanks, guys - I'm counting on you! :) :)


P.S.: Found some very helpful "UNIX Commands" documents online and promise to study hard to get better with this ... ;-)

---

### Post by armin00as on 2007-08-05
*..anyone??*  :confused:


Come on, guys... I know you can do it. A little help (or at least some pointers), please...


Thanks!

---

### Post by armin00as on 2007-08-05
Fixed it myself... 


I deleted the entire MythTV folder and then created two new folders, MythTV and (within) recordings. 
Gotta say I'm warming up to UNIX commands - especially rm -r and mkdir, it seems... ;)

Now I just have to master the chmod correctly, and I'll be back to normal - or so I hope.

Update: Yep, 'cmod' and 'chown' fixed my issues. - Thanks, Armin ;)
Hope I'll get MythTV running now...


[Guess this was too easy for you forum guys to respond, huh..?]

---

