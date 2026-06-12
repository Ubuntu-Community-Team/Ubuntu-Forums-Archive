---
title: "Baffled! Internet access issues"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-11-18
Hi all, 

I am currently experiencing issues accessing the internet via Ubuntu Gutsy, and unfortunatly as I am currently away from home I am unable to directly access the situation and am therefore baffled.

My Wife is attempting to access internet via ubuntu (which the only pc in the house is running) in order to keep in touch with me while iam away from home, its therefore really difficult for me to trouble shoot this issue, I was hoping that perhaps someone here could assist.

When leaving home last week the internet was functioning ok, via a wired network, over a router, my wife says that the issues started after she deleted cookies and files from firefox and shut down the pc for the night, upon running the pc in the morning it seems that internet access has gone.

She subsequently contacted the telephone proividor who state that the line is perfectly ok, and that they were able to get a signal back from our router, Ive also had her check the router settings and all passwords and information are already configured correctly.

As I remember my router has a few lamps, power, DSL which are all green, the internet lamp stays off as obviously there isnt any internet activity.

I read somewhere that perhaps firefox can create issues, any further info from this point of few?? otherwise perhaps a few pointers or basic troubleshooting steps which could help us get internet back and running and keep in touch:(

thanks in advance

---

### Post by PointyWombat on 2007-11-18
Firstly, you should see if the problem is with firefox or your internet connnection. In a terminal window (application -> accessories -> terminal), you should be able to ping an external target, such as ubuntu.com

$ ping ubuntu.com

if it comes back OK, then your internet is most likely OK and the problem is likely firefox.

if it doesn't come back, or says unknown host, then the problem is either resolution or your connectivity.

You may also just get your wife to bounce your internet router and once that's back, reboot your box. and try again.

---

### Post by TURNER on 2007-11-18
thanks alot for your assistance, i"ll have my wife try the suggested steps and come back with the info.

Could I just ask what you mean by "bouncing" the router? Not bouncing it off the floor?? :)

Thanks again

---

### Post by PointyWombat on 2007-11-18
reboot or poweroff/poweron...

---

### Post by traken on 2007-11-18
I'm currently have exactly the same problem.  Just installed 7.10 and after getting my wifi card to work it's doing this.  I can sucessfully ping any ste, but actually going to the site is very iffy.

It actually started off I could access only Google and Yahoo, but now I can only access ASDF.com (that I can find).

---

### Post by TURNER on 2007-11-18
ok, thanks again for taking the time to help out.

---

