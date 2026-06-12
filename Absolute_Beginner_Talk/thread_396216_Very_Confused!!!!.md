---
title: "Very Confused!!!!"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by bobalicious on 2007-03-29
Hey, 

I am very new to linux, and my knowledge of computers is very limited. 

I converted to ubuntu today, and am having very big problems with my network connection.

To Clarify:
I am connected to my router, i can access it via wireless on firefox (10.1.1.1), i am told i am connected, but i cannot acces the internet. What have i done wrong and what do i need to do to fix it??

---

### Post by mendingo84 on 2007-03-29
open a terminal and type this:
> 
ping [www.google.com](www.google.com)

post the result plz

---

### Post by bobalicious on 2007-03-29
Sorry, forgot to add that i pinged google and got back a reply

---

### Post by mendingo84 on 2007-03-29
if you get a reply it means that you really are connected...hmmm, have you set up your ip address in Firefox->Edit->Preferences?

---

### Post by Bartender on 2007-03-29
Here's something else to try that's fairly common.  Ubuntu and Firefox use the newer IPV6 protocol for handling packets of data on the internet.  That's fine, but if your router and/or modem weren't built to be IPV6 capable their performance will be very spotty.  You'll see a little bit of activity on your modem or router lights, then they just sit there til the website times out.

First thing to try is disabling IPV6 in Firefox
[http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html](http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html)
Follow the directions in post #3

If that works, and Firefox is now connecting, then the next step is disabling IPV6 across the entire Ubuntu OS
[http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/](http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/)
That's relatively easy, but if you've never tweaked around in the command line it might be a little scary.  Print the directions out and follow them carefully.

If tweaking Firefox doesn't make a dif, then probly no point in the second step described above.  Post back and let us know!

---

### Post by bobalicious on 2007-03-29
Thanks Bartender!

resolved my issues, now just got to do the 2nd step :)

---

