---
title: "dapper server installed! now what?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by WIVO_Riley on 2006-12-15
Have a couple of questions.
I have 4 computers:
1 is celeron laptop running XP pro
1 is celeron desktop also running XP pro
1 is core2 duo running dual boot ubuntu 6.1 and XP home
last one I am (so far so good) attempting to run as a server

Server computer is old- (read FREE!)  AMD K6- 475mhz I threw in a couple of sticks of memory I had layin around (now up to around 320mb RAM) and an 8gig hard drive to go with the stock 12 gig.  It took me ALOT of frustration just to find out that it DEFINITELY REQUIRES the alternate server install (dapper).

**NOTE** I tried to install around 4 or 5 times- couldn't get it to go- finally I googled that the hard drive partitions must be deleted and partioned from scratch before it would take- i t was getting hung on the booting the kernal... at startup.

For those who are still looking for their help- configure the partitions manually if it's an old AMDK6 like mine.  MAKE SURE THAT THESE PARTITIONS ARE SET AS PRIMARY: I set 150mb for the /boot (make sure the boot flag is set), 750mb for swap (again make sure that it is set as swap, and the balance of master hde as / .  Next I set the other drive as /home (and as a logical partition).

EUREKA!!- IT TOOK!!

Now for the questions:

I want to use this as a webserver, a file and print server (as I go along, I may want to keep going, but its a piece of "sht", so for now, I'm considering it a learning tool"

I'd like to set it up to network with my other computers, serve as a file and print server, and if possible  host a couple of low-traffic web sites.

I want to keep everything safe, and not configure something badly out of ignorance, but I'm not really sure where to go from here.
I've installed ubuntu desktop on the server and webmin as I need GUI's right now until I get more familiar with using the terminal , etc.

Could anyone either give me a rundown on a good configuration or point me in the direction of where to start reading someone else's tips?  I've probably had 4- tabs going in the last 2 days helping me through this far. 

I'm trying to learn, but it's tough starting from scratch- I don't do this for a living- but I could build you a HECK of a parking lot!!

any help is appreciated, and thanks in advance.

still a n00b and proud of it! lol

Riley

---

### Post by Tipo on 2006-12-16
I found this setup article to be very helpful in terms of editing config files to get my server live: [howtoforge.com/perfect_setup_ubuntu_5.10]("howtoforge.com/perfect_setup_ubuntu_5.10")

---

### Post by TheRingmaster on 2006-12-16
> **WIVO_Riley said:**
> 
1 is core2 duo running dual boot ubuntu 6.1 and XP home
last one I am (so far so good) attempting to run as a server


you must mean ubuntu 6.10?

---

### Post by WIVO_Riley on 2006-12-17
> **TheRingmaster said:**
> you must mean ubuntu 6.10?

6.1 on the core 2 dual boot.

6.06 LTS alt server on the AMD K6.

Took me a while to get it installed, but finally got it right- I followed an online newbie install run-through- but it was only about 80% right and/or complete.

I think I am gettin a handle on the installations- I could probably figure out to configure everything now, but I just don't want to screw something up or make it insecure.

Maybe I should rephrase my original question-(?)

Anybody have some things to definitely NOT do during the course of configuration?

Thanks for any and all replies.

MAN this board travels fast.  

Riley

---

### Post by Littleweseth on 2006-12-17
WIVO_Riley, you have a *very* disturbing avatar. Just allow me to say : OW!

</thread hijack>

---

### Post by WIVO_Riley on 2006-12-18
> **Littleweseth said:**
> WIVO_Riley, you have a *very* disturbing avatar. Just allow me to say : OW!

</thread hijack>

lol- this forum doesn't allow animated .gifs for avatars.  You should see the... :shock: 

</thread hijack>

<thread>

---

