---
title: "What!!! Windows faster than Ubuntu?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-16
Hi
I am very dissapointed and impressed at the same time with the behaviour of Ubuntu. I've just installed it in my laptop, and sorprisingly for me windows in some points works faster.... for example when I type sudo nautilus it opens the explorer about a minute or more later, and in some things like that it really behaves very slow. In internet it is slower than windows, it says it has less connectivity and the same page that opened in in 5 seconds in windows in Ubuntu takes 15 secs aprox to open it or to start opening it.

So is it possible for me to have something configurated wrong? I mean what's the point of the change to Linux if I lose functions as fingerprint reader, or things like that ; if Linux is even slower? 

Please I am getting very disappointed....

---

### Post by aysiu on 2007-05-16
Nothing to do with speed, but you should use ```
gksudo nautilus
``` instead of ```
sudo nautilus
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jtraub on 2007-05-16
Possible cause of slow internet is ipv6. Try to turn it off.

Also, remeber, that Windows XP was released in 2001 and was oriented for middle class computer of that time (Feisty Fawn released in April of 2007). It is weel known, that Linux is better than Windows for old computers. You just should choose right options.

---

### Post by Jorge32 on 2007-05-16
in fact I've used them both and after a couple of minutes and even when I had closed the termina I see three or more explorers open at the same time. it just says, initializing gnome-mount extention and nothing happens...



I even tried now and since I started writting this it hasn't opened! it has just about 2 minutes!!!!!!


and what does it has to do with internet? I mean with Windows I had no problems with speed and here, even close to the wireless modem it says that the percentage of signal is about 80 percent!




just took the exact time from the moment I gave enter to gksudo natilus until the windows opened and it took 3 :13 minutes...

---

### Post by Jorge32 on 2007-05-16
> **jtraub said:**
> Possible cause of slow internet is ipv6. Try to turn it off.

Also, remeber, that Windows XP was released in 2001 and was oriented for middle class computer of that time (Feisty Fawn released in April of 2007). It is weel known, that Linux is better than Windows for old computers. You just should choose right options.

how do you turn ipv6 off? 

and about the version of computers I have one month with mine... and it's a professional version, I mean the version for work and not for home.

---

### Post by jtraub on 2007-05-17
> **Jorge32 said:**
> how do you turn ipv6 off? 
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by esoterica on 2007-05-17
Saying either one is faster than the other is just ignorant, there are so many possible factors that could affect either that there is no way to make such a comparison. Even software specifically designed for Bench Mark testing is distorted and flawed. If your using this as your decision factor in determining which OS to use then your going to spend a lifetime of never being satisfied or knowing what your missing no matter which one you were to choose.

I my self am probably different than most people, I just love my computers, which or multiple Operating Systems on them just make them that much cooler to me. I love Linux, just wish someday I'll get over the learning curve aspect to really be able to dig deep into it like I can do with my Windows computers I'm use to and already know how to do anything with or on. I have to keep reminding myself I didn't learn what I know in Windows over night, it had a learning curve to it as well, just happened so long ago I sometimes forget that fact.

Your crying about your fingerprint reader not working, have you even spent 5 minutes trying to get it to work. I'm on a Toshiba laptop with my Linux install and my fingerprint reader works fine, I just looked up and followed the directions for my laptop that I found here...

[http://en.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://en.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

On the other hand, I also have a brand new Dell Latitude D820 laptop that came with XP Pro on it and a fingerprint reader working on it. When I wiped out XP Pro and installed Vista on it I still have a fingerprint reader on that one that doesn't work because Dell hasn't provided Vista software yet to do so. Now I'll probably have to hunt down and BUY as in PAY FOR (again) special software just to be able to use it again in Vista now.

I'm really getting sick and tired of paying for all this new software every couple of years, or worse, the Windows software providers who charge you for their buggy products, then charge you again for updates to it so you can fix the original problems they left in it. 

I've attempted to use Linux for years now, every time I ended up walking away from it because something would break in it and frustrate me. There's still buggy free software for Linux out there that just doesn't work or causes a lot of problems and unfortunately no central database anywhere to weed them out. I am finding though Linux has really come a long ways since the last time I tried using it, it installs easy now and you can find software that actually works now. Not to mention it's free, so if your not happy with it, to each their own, get your money back and go back to using just Windows, try getting your money back from Microsoft though if your not happy with one of their products which you did have to pay for.

P.S.
Another reason I've left Linux in the past was because support and documentation for it was absolutely pathetic to non existent.  I still have problems with the search feature not finding things I know I've seen already in the Ubuntu documentation, but once I do find what I'm looking for the documentation is absolutely amazing, the support from the community here is great, people actually figure out and solve problems here, something that's rare to find on any type of Microsoft support options, even if your contacting Microsoft support directly the actual help is ridiculous and often worthless.

I thought having to use the terminal window so much in Ubuntu would be a deterant for many people, though after seeing how people use it for helping others around here it's a god send. You can help someone fix their problems by just giving them a simple command they can copy paste in as opposed to helping someone in Windows which would require pages of instructions to accomplish the same thing.

---

### Post by kelvin spratt on 2007-05-17
esoterica I  agree with most things you say yes and you can't really compare, after over a decade with windows, the support is disgusting Ubuntu is free and support is Excellent, when you consider a lot of the queries are duplicated, and if people spent time looking in the forum most answers are there already. Fiesty is very fast on my machine as is Xp pro. about the same but Fiesty is fast when working, on our 64bit Laptop Xp is very slow so we won't bother with vista on that one

---

### Post by Rui Pais on 2007-05-17
I will never understand how can it be possible saying that 2 different things have this or that speed... they are always doing different things! 

Anyway, in most cases you are comparing apps performance not OS performance. 
Even if you compare the windows/linux versions of gimp, OOffice or firefox you will face the speed of this apps in each environment more then the environment speed by itself... 

In a general way, windows is faster when it cames to graphical stuff (redraw/refresh windows, fps, etc.) due to it's intrinsic design. Windows have graphical support build directly on its kernel, while on Linux we rely on the separated X server. It has some (huge) advantages, but speed it's not one of them.

Nautilus is a very heavy and slow app. It has an excellent design (for usability) but a terrible implementation. It's natural that Windows explorer (a relatively good windows app) would be faster. If you want a faster file manager try thunar, pcmanfm or rox. They are similar but lighter. Thunar even offers some functionality (recover from trash) that nautilus miss. 


The other issue, network speed should be dependent of your network provider, not the OS. I second the ipv6 suspect. 
In any case, try other browsers. Firefox, it's notorious for being faster on Windows then on Linux (never understand why. I even read a thread on a guy says it use it the Win version through wine and it stills faster! that was around 1.0 version. Now things are better.) and not the fastest browser on Linux anyway. Check opera or kazehakase to see if the performance matches the windows one.

In most cases it's just a question of choosing the right app, instead of accept what is settled as default.

---

### Post by esoterica on 2007-05-17
> 
I agree with most things you say


I could word things in a way I know everyone here would agree to, but there wouldn't be any fun in that if we didn't leave the door open for some controversy to take place. ;-)

> 
when you consider a lot of the queries are duplicated, and if people spent time looking in the forum most answers are there already


I haven't been to a message board yet where this hasn't been thought to be a working suggestion on paper, however the sad truth is everyone seems to think their problems are unique and require a specific response just for them. Then you have those that think if you add your question into someone else's post your hijacking it. I've even seen message boards where the admins complain if you open a new post by not searching, then the same people turn around and complain if a question gets asked in a related existing post.

Searching in this particular forum for beginners would be a nightmare. Things move so crazy fast in this forum it's like being in an online chat room instead of a message board. I've never seen anything like it, then I seen the other day just how many users are online on this message board and I thought we must be on one heck of a monster of a server and pipe to handle that level of traffic, wow, that's impressive!

I've found that rather than searching for questions I have or even posting them myself, I just refresh my browser here a few times and within about 10 minutes someone else is sure to ask exactly what I was thinking about. Even more insane, in just the time it takes me to move my pointer and open that new post, someone else will have likely already replied in it with the working answer, amazing.

The support from the community around here is just unbelievable, I've never in my life seen anything like it anywhere else. Sometimes I go to the other forums around here that are a little slower paced just so I can catch my breath. Ubuntu is certainly all around very impressive, with each day I use it a little more the more I find I'm likening it a lot.

I'm actually taking an entire semester of Linux at school in the Fall, so I went out and bought this new laptop just to install Linux on it so I wouldn't mess up my new Vista Laptop (which was about three times more expensive). Now I keep looking at that other laptop thinking I'm probably going to swap them and run Linux on the better one instead and put Vista on this one. I would have told you that your crazy if you'd of suggested such a thing to me a week ago.

A bonus to running Linux, none of my friends ask me to use my computer anymore, they're afraid of it.

I do sadly have to admit though, I like IE7 a whole lot better than Firefox or any of the other alternatives out there. I wouldn't say the same for IE6 or older versions, but I do like IE7 a lot, it's the only thing I'd miss if I went full blown Linux on everything.

---

### Post by esoterica on 2007-05-17
Very good points and very nicely said Rui Pais!

---

### Post by esoterica on 2007-05-18
> 
try getting your money back from Microsoft though if your not happy with one of their products which you did have to pay for.


Maybe a person can get their money back for Windows after all, I just found this that someone had written, wish I would have known this info before buying the last two laptops I just purchased...

[http://community.linux.com/community/07/01/03/227237.shtml](http://community.linux.com/community/07/01/03/227237.shtml)

---

