---
title: "MacJanitor for Ubuntu?"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by Jerry Wolczanski on 2005-11-06
My Mac G4 began to slow down terribly a year or so ago.  One of my Macintosh friends suggested I run "MacJanitor" periodically.  Apparently UNIX, or at least that version of UNIX on my Mac (now 10.3.9) was designed to run 24/7; shutting my computer down when not in use, often for days, really caused all these housekeeping chores to back up.  I began running MacJanitor and I've had no problem since.

**Ubuntu Question** (I'm using a recycled PC):  Is there such a house-keeping need for Ubuntu?  The UNIX on the Mac had daily, weekly, and monthly routines.  

Thanks
Jerry W

---

### Post by gord on 2005-11-06
ubuntu and unix style opperating systems in general are pritty tidy and clean, the only thing that comes to mind is the 30-boot check of your harddrive, its nothing much, just makes sure your drive isn't starting to die.

---

### Post by ow50 on 2005-11-07
[QUOTE=Jerry Wolczanski]**Ubuntu Question** (I'm using a recycled PC):  Is there such a house-keeping need for Ubuntu?  The UNIX on the Mac had daily, weekly, and monthly routines.[/QUOTE]
Take a look at the scripts in the following directories
[LIST]
[*]/etc/cron.d
[*]/etc/cron.daily
[*]/etc/cron.hourly
[*]/etc/cron.monthly
[*]/etc/cron.weekly
[/LIST]
to get an idea of what tasks are scheduled. I don't quite know how crucial they are  and how advanced cron is in running them if your computer isn't on 24/7.

---

### Post by Rxke on 2005-11-07
Nowadays, most people don't let their computers run 24/7 so that cron can't do its work (because, usually, the cron tasks are sheduled to run during the night, when the computer has less other stuff to do etc...)

However: there is a simple solution to this: anacron. When you start up your computer, anacron looks at the 'to-do' list of cron, and if it sees anything that had to be done, but wasn't done, because the computer was switched off, anacron runs it. 

So, in short, install anacron. Via synaptic or via apt-get install anacron 
Although I believe anacron is already installed by default.... So probably all the housekeeping is already being done for you. :D

---

### Post by Jerry Wolczanski on 2005-11-07
[QUOTE=Rxke]Nowadays, most people don't let their computers run 24/7 so that cron can't do its work (because, usually, the cron tasks are sheduled to run during the night, when the computer has less other stuff to do etc...)

However: there is a simple solution to this: anacron. When you start up your computer, anacron looks at the 'to-do' list of cron, and if it sees anything that had to be done, but wasn't done, because the computer was switched off, anacron runs it. 

So, in short, install anacron. Via synaptic or via apt-get install anacron 
Although I believe anacron is already installed by default.... So probably all the housekeeping is already being done for you. :D[/QUOTE]
Thanks so much for this post and the previous posts, yes ANACRON is installed on my computer, I'm going to have to play/search a bit to see if it's actually running.  I'm hoping that UBUNTU will succeed in the larger computer community.  If it does, it'll be because of folks like you who support this forum.
Thanks again
jerry w

---

### Post by Rxke on 2005-11-08
You're welcome. 
I, too, think the community is what makes Ubuntu tick. (besides the detail that it is a really nice distro, heehee ;) )
I mean: I'm a newbie, like most other people, still you see many people taking some of their free time to look around the forums... Encountering 'beginners' problems they faced too, giving advice how they solved it... 
And then there are the real veterans, with thousands of posts, yet they still post regular answers to 'stupid' beginners-questions, in a friendly way.
Man, how I love that! There are other distributions where asking questions is sort of... an excercise in self-castigation...

---

