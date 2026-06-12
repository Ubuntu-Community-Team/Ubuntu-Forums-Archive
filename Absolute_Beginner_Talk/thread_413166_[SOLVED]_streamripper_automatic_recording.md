---
title: "[SOLVED] streamripper automatic recording"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by ubromtoo on 2007-04-18
Is there a way to set Streamtuner/Streamripper so that it will switch on automatically

 at a specific time and record a specified staion for a given length of time, then switch

 off?

      have used the "Search" function for several tries to find something on this,  no luck so 

  far.     :mrgreen:  newbie hopes for help

---

### Post by Marsolin on 2007-04-18
I don't know if streamripper has that capability, but you could write a simple script to do it. It could go something like this:

type the appropriate streamripper command as the first line
sleep 60    #or whatever number of seconds you'd like to record
type the command to stop recording

You could then create a cron job that points to the script that designates when to execute it.

I don't know the streamripper syntax so I just put placeholders for those lines.

---

### Post by ubromtoo on 2007-04-19
Marsolin :

     Thanks for pointing me in the right direction; I'm too ignorant to be able to do

 what you've outlined, but study should eventually get me there.    :) 


              'preciate the help !

---

### Post by ubromtoo on 2007-05-05
Here I am , two weeks down the road, and I'll repeat my request for help, Perhaps

someone could simply give me a "fill-in the blanks" solution to this little request.

    Learning to do what Marsolin suggested is certainly a goal of mine, but that is

taking quite a bit of study for a Noob such as I .

    Marsolin's kindly suggestion is generally instructive but is not the specific

 "quick fix" which must be out there somewhere....
    

                                                                                          :guitar:

---

### Post by yabbadabbadont on 2007-05-05
```
HOME=/home/yourusername
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
# m h  dom mon dow   command
15 13 * * * streamripper http://my-url-to-be-ripped -d full-path-to-my-save-directory -l number-of-seconds-to-record > /dev/null 2>&1
```
Save that as a text file.  Any name will do, but I will use mycrontabfile.txt as an example.  Then, in a terminal window, run "crontab mycrontabfile.txt" (without the quotes).  This tells cron to run streamripper at 1:15PM every day.  You will want to read up on both streamripper and the crontab file format.  ```
man streamripper
man 5 crontab
```

---

### Post by ubromtoo on 2007-05-08
YABBADABBADONT :
  
     Works like a charm !   ... and it even makes a folder with my choice of name !

  The manuals are going to be quite useful, too...  please accept my sincere TX    

                                                                                           \\:D/     :-\"

---

### Post by MrFurious on 2007-05-10
Hello forums!  This is my first post here.  I started using Ubuntu when Edgy dropped, and as a Linux noob, these forums have been an invaluable resource.

YABBADABBADONT:
Sorry to bump an old post, but I have a question about your solution.  I recently discovered streamripper myself, and I was attempting to schedule a stream download using exactly the same method.  My problem was that no matter the number of seconds specified in the -l parameter, I would always get about 1 minute of audio.  When I added the redirects, as in your example, it seemed to work fine.   My question is this; it is my understanding that "> /dev/null" discards standard out and "2>&1" redirects standard error to the display.  What I don't understand is, *why* does this fix the problem?  :)

Thanks for the great tip.

---

### Post by yabbadabbadont on 2007-05-16
> **MrFurious said:**
> Hello forums!  This is my first post here.  I started using Ubuntu when Edgy dropped, and as a Linux noob, these forums have been an invaluable resource.

YABBADABBADONT:
Sorry to bump an old post, but I have a question about your solution.  I recently discovered streamripper myself, and I was attempting to schedule a stream download using exactly the same method.  My problem was that no matter the number of seconds specified in the -l parameter, I would always get about 1 minute of audio.  When I added the redirects, as in your example, it seemed to work fine.   My question is this; it is my understanding that "> /dev/null" discards standard out and "2>&1" redirects standard error to the display.  What I don't understand is, *why* does this fix the problem?  :)

Thanks for the great tip.

2>&1 does indeed redirect stderr to stdout and stdout is redirected to /dev/null.  I have no idea why it would fix your problem though.  If you don't redirect program output, cron will try to save it and mail it to you.  Perhaps you don't have local mail delivery setup and that is causing the issue?

---

