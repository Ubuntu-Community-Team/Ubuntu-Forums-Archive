---
title: "new partition for /home"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2007-07-09
is it possible for me to be able to create a new partition and move my /home directory to it without doing a reinstall? if so, how? Also, what are the benefits?

---

### Post by FleetAdmiral74 on 2007-07-09
Yes. Spend 5 seconds and Google it. 

Thanks.

---

### Post by wana10 on 2007-07-10
what a great answer that was:rolleyes:

[try this link instead](http://www.psychocats.net/ubuntu/separatehome)

(all thanks to psychocat (aiysu is forum name i believe?), helped me tons when i was brand new to the scene)

---

### Post by Skidpad on 2007-07-10
> **meanburrito920 said:**
> is it possible for me to be able to create a new partition and move my /home directory to it without doing a reinstall? if so, how? Also, what are the benefits?
Wana10 already gave you a good link, so I'll answer your other question.

Having a separate /home partition is useful because it allows you to retain all of your files in one place - a place that can be mounted/used by several different Linux installations.  

With /home all by itself, you can install any number of distros, and have each one pointed at that common /home location.  You can then save files to /home while working in a particular distro; if you later decide you don't like that distro - or want to upgrade to the latest release - you can delete/install over it at will without losing your files/documents...etc.

:)

---

### Post by FleetAdmiral74 on 2007-07-10
And what a *great* job he did not following forum guidelines and searching.

On google, seraching "new home partition", FIRST result is "Create a separate /home partition in Ubuntu"

---

### Post by aysiu on 2007-07-10
> **FleetAdmiral74 said:**
> And what a *great* job he did not following forum guidelines and searching.

On google, seraching "new home partition", FIRST result is "Create a separate /home partition in Ubuntu"
From [the forum guidelines](http://ubuntuforums.org/index.php?page=policy): > When answering technical support issues:
# Be considerate to the person asking the question. We were all a green user at one point. Yes, some users are harder to help than others, but please be respectful to all users.
# Try to avoid acronyms and jargon when giving instructions. New, or "green" users may not be able to follow you, and many will not ask you for an explanation in order to avoid looking stupid. **RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question.** Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.

---

### Post by wana10 on 2007-07-10
when i first started using linux there were times that i had no clue what i was doing, and was more than frazzled for being so far out of my element. a beginners forum such as this greatly helped alleviate fears and concerns, primarily because i didn't recieve snarky 'google it' responses. now that i am more experienced i don't have to ask as many questions that are easily answered anbd can help myself a lot more, but not everyone can start at that level, crawling before walking and all that.

---

### Post by FleetAdmiral74 on 2007-07-10
Ok, point taken. Apologies. 

I can't say I agree with the guidelines, but I  shall respect them. Guess I had better do some reading.

---

### Post by aysiu on 2007-07-10
It's okay, FleetAdmiral74. I think all parties participating in this thread have the best of intentions.

---

### Post by ReverendJ1 on 2007-07-10
@aysiu - I was just reading your tutorial that wana10 mentioned. It is very nice, easy to follow, but I was unsure what this line is doing exactly:
```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```
I know most people probably wouldn't really care, as long as it works, but I am trying my best to **learn** Linux/Ubuntu instead of merely **using** it. 

Also for anyone else reading this post who is trying to set up a /home partition from what I have been able to find (aysiu back me up here) is that you should leave about 10-20GB as your / (root) partition for Ubuntu and all your installed programs. 

aysiu, maybe you should include a little note about recommended partition sizes on that page. I noticed that on the partitioning page you said that your partitions should look like *insert picture here*, but did not have any values. I mean, I could see that it was ~25% but a number of GB would be helpful on both pages. Just a thought.

---

### Post by aysiu on 2007-07-10
I don't actually know what that command means, to be honest. I just know it works.

Even though people like to link to [my Psychocats tutorial on separate /home](http://psychocats.net/ubuntu/separatehome), it was actually just a rewrite of [another tutorial on the same topic,](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) explaining that command thisway: > Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the [Debian archiving guide:](http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving) ```
cd /home/
find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /mnt/newhome/
``` Make sure everything copied over correctly. You might have to do some tweaking and honing to make sure you get it all right, just in case. As for recommended partition size, I'd say the root partition usually need not be bigger than 10 GB. It kind of depends on what you dump in there, though.

I'll consider adding recommended partition sizes to the partition planing page, though. Thanks for the suggestion!

---

### Post by ReverendJ1 on 2007-07-10
Oh, ok. Well after reading both man pages for find and cpio, (I just got home and back to Linux) I still am not much more enlightened. I guess for this I will just have to accept it as a special way of copying that preserves links better. Thanks for your help. :-)

---

### Post by Laplace's Daemon on 2007-07-10
I actually just finished following **aysiu**'s tutorial this morning, and I booted up to discover that the Ubuntu default background, theme and panels were on my desktop (except the panel text was still white, which I had changed manually in some configuration file that I can't remember at the moment).  I won't have time to test out much else until I get home from work tonight, but does anyone know what might have gone wrong, or how I can fix it?

---

### Post by Skidpad on 2007-07-10
^^^^ Perhaps the theme you were using previously was located in your original /home folder, and now the theme manager doesn't know where the new /home partition is located, so it can't find your chosen theme, and therefore defaults to the standard Ubuntu theme?

---

### Post by Laplace's Daemon on 2007-07-11
After examining the computer more closely, things seem to be a bit worse that I had initially thought.  Some of my old files didn't get transferred over, and config files for programs weren't working.  So I followed the recovery instructions (more on this later), and now I'm back on the original / partition, which all seems to be working at the moment.  First, I would like to get back to a position where I can try this again, and hopefully do better.  When i tried the first time, GParted on the Ubuntu Live CD gave an error on resizing the / partition (it seems that / was remounted near the end of the resizing work).  However, nothing seemed to be wrong in the GParted screen, so I pressed onwards.  I want to get back to my original / partition so I can try the whole process again, but I want to confirm how to properly do this.  I imagine it going something like this:

Open GParted Live CD (not with Ubuntu this time)
Right click on the new partition (which is /dev/sda7) and choose Delete.  This, I think, will turn the new partition into unallocated space.
Then resize the / partition (dev/sda6 on this computer) to be the maximum size
Restart to make sure that everything is ok, then do the guide again.

Will this course of action correct any partition error that may have occured the first time around?

I also believe that the recovery code in aysiu's guide can be improved a bit.  Specificially the line:```
sudo cp -R /recovery/home_backup /recovery/home
```produces the directory structure:```
/recovery/home/home_backup/{list of user names}
```and sets all ownerships to root.   Looking at the man page for cp, it seems that you may want to add the -p option or --preserve=all, but I have not tested this so I may be wrong.

---

