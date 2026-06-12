---
title: "[SOLVED] Trying to get online using Sprint Novatel U720 USB aircard"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-31
I have Ubuntu 7.04. I signed up with Sprint, the Novatel USB aircard came today, I set it up according to the PDF file instructions from the Sprint website using the KPPP software (Linux software made to work with wireless cards). Everything tested out and configured fine-- the computer, the modem, and the KPPP software all recognize each other. But when I click on "connect" to go on line, it just tries and tries, but doesn't connect. 

I tried the aircard with my Win XP machine, and it works great. So I know the Sprint service and aircard are working fine.

What do I do now to get my Ubuntu machine on-line?

---

### Post by pappapump on 2007-05-31
Try sprint faq first, there aren't a lot of people on Ubuntu using those.
I have had problems with them in windows also so, Ubuntu and Sprint aren't even a concept to me.

---

### Post by deadgobby on 2007-05-31
[http://www.evdoforums.com/thread3308.html](http://www.evdoforums.com/thread3308.html).
. This may work

Gobby

---

### Post by pablodavid on 2007-10-07
I have the same sprint usb model and was able to install it. Please follow the instructions from this site : [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)
good luck and enjoy.
Pablo

---

### Post by lazyart on 2007-10-11
I used the method outlined [here]("http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html"), coupled with [this]("http://samat.org/weblog/20070128-sprints-evdo-mobile-broadband-on-ubuntu-linux.html") and it works with my shiny new U727 (I had to add the vendor id from sprint's pdf that is mentioned above).  Now I can click on the connection manager and use the dial up connection entry that is created as a result.

The advantage to the this method is speed.  Using sprint's method you might be limited to 500 kb/s transfers.  Using this method I got 800 kb/s down (and my laptop uses USB1.1)

Sprint's method is probably easier to set up.  Which is neither better nor worse. Speed vs. simplicity.  By making changes to airprime.c (outlined in the method I linked) you have to redo it for every kernal upgrade until it is added in (I have filed a bug report).

---

### Post by swarup on 2007-10-12
Thank you very much, everyone. It is very kind of you to have given your suggestions this long after I initially posted. And it is my fault really, for not changing the thread title to [SOLVED]. I got it working back in May, and should have reported that here. I just use GNOME PPP dial-up connector, and it works like a charm. I have to think back now, how I got it working. --Yes, I got a hold of someone in the highest level of tech support at Sprint. Although they don't support Linux, but there was a fellow there who uses Linux at his home. And he had helped many people to get Sprint set up in Linux. He told me what to do, and since then it's been working great. I actually get download speeds of 1.1 MB/Sec, and upload speeds of 700-800 KB/Sec. 

Since then, I've set up the Novatel U720 aircard with a Kyocera wireless router, and that way both our Linux machines can go on line at the same time. And the speeds are great with both machines.

Thanks again for all your help.

---

