---
title: "Flash, Java, and Miro"
date: 2008-01-05
forum: Apple PPC Users
---

### Post by thespottedelf on 2008-01-05
ok got 7.0.04 running fine... but i don't have flash or java.  And this great app that i found (i use all the time on my intel imac) miro, i installed it and now i can't find were to open it.

i followed this on how to install it. [http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)
but i can't find the app

I would also like some good guides on installing flash (i tried the way the wiki said and it didn't work for me :()

And Java i haven't even started on.  So if i could get some help it would be much appresiated.

---

### Post by Auria on 2008-01-05
First you mention an intel mac... is your current Ubuntu installation on PPC? If you are currently on an intel computer you should move to the Apple Intel computers forum as they work rather differently from PPCs

If you are on PPC, it's rather simple, you can't install flash. You can try gnash
As for Java it's in the FAQ (it's a sticky on these forums)

As for miro i never installed it, but as a simple guess, did you try 'miro' in a terminal?

---

### Post by thespottedelf on 2008-01-05
yes i wasn't very clear, i'm running ubuntu on a imac g3 500 mhz.

what do you mean by miro in terminal?

i just typed miro and hit enter and it said command not found.

---

### Post by ubuntubrian on 2008-01-05
I'm not sure how you installed miro. I used the info on the Miro website but running it is not too hard. If you installed it into your home directory then you need to, in a terminal, go into the miro directory, then into the platforms directory then into the gtk-x11 directory and there you will see a shell script. Run the script, "sh run.sh". this will start miro. I have not had great luck with the later versions of miro and some videos play well, some don't at all and some do without sound.
Java is a bit harder and I have the Java packages from the repositories installed plus from the IBM website. There's a "how-to" for the IBM version and then you need to run some utilities to get the proper Java to run for various other software. thunderbird, for instance, uses the IBM Java, whereas Firefox is happy with the repository versions.
It took me months to get all of this configured and much of it I have forgotten and just let it run.
I could probably dig up the links if I had to.
there is quite a bit on the Forums regarding Java so do a bit of searching here in Ubuntu.
Gnash is a real pain and that took 100's of hours and I had to use the Gnash Bugzilla forums a lot. It doesn't just happily install and the variables and configuration possibilities are vast and the dependencies huge. It runs and plays Youtube and some other videos but it pales compared to my OSX player. It is an adventure!

---

### Post by thespottedelf on 2008-01-05
hm.... well i'm going to do some research on java then.  I think i'll just give up on gnash for now, maybe later on down the road.

---

### Post by Auria on 2008-01-06
I just use a video-download firefox extension. Anyway Gnash is not reliable for most stuff so the extesion route is often easier and less frustrating (you won't have non-video flash stuff, but gnash often can't either)

---

### Post by ubuntubrian on 2008-01-06
I didn't mean to discourage you but just to let you know that it can be laborious and I have the time, fortunately. Video down loader works great too. The Java thing is a pain for sure but the IBM Java does work. there's an Ubuntu PPC thread somewhere that has the install instructions and how to set your Java to work. I had to manually configure Thunderbird to use the IBM Java no matter how I tried.
Here's the how-to: 
[https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64)

It's just harder on a PPC machine sometimes just plain won't work. I may buy an Intel Laptop just so I can quit bucking the waves

---

