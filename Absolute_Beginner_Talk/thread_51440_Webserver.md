---
title: "Webserver?"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by IRT on 2005-07-23
Hi,

I'm an Ubuntu user from few months. I want to setup a webserver and I need to know what distro is better for a webserver. As far I read there are few answers... Slackware, Debian, Gentoo,... 
I want something easier to understand and some other fellows told me to choose Slackware. Gentoo is hard and Debian too. So I'm thinkin about Slackware.

Now, I'm using Ubuntu (not as a webserver) and I need some prof explanations.
Why should I choose Slackware for a webserver?
Why is considered better than Ubuntu for a webserver?
**Any other pros and cons are welcome!**

_In fact I need a versus between Slackware and Ubuntu regarding the web server solution._

I know it could be interpreted as malicious to ask this here on Ubuntu's forum, but this isn't my intention. All I need is some pro and honest answers for the best choice.  :roll: 

Cheers :)

---

### Post by jasmuz on 2005-07-23
To me, any distro is good enough for a job if you SECURE it well.

So, read all about turning your Ubuntu into a super duper webserver, while you secure it from top to bottom (remember security is not a process, its an outcome)-

---

### Post by Gsibbery on 2005-07-24
I have used both Slackware and Debian and don't see where there is that much difference. Keep in mind, Slackware has no tools for automated dependency checking, so you will have to get the third party SWARET. 

But like jasmuz said, pretty much any distro will do as long as it is secured and monitored adequately.

---

### Post by IRT on 2005-07-24
:) Thanks for your answers. As I read before the Debian is the answer for an uptodate security and easy file management. Slackware is not as good and need a third party package - swaret.
Also some people told me if I'm running Ubuntu, I will not have any problems in running Debian, it's even easier.
For the moment I'll work with Ubuntu and learn more about how to secure it as a webserver.

Please, if you know how to secure Ubuntu as a webserver and have some links post it here.

Cheers

---

### Post by Gsibbery on 2005-07-24
Yes, Ubuntu is the easeist Debian (or anything for the matter) that I have ever fouind in a Linux distro. 

Before you take the plunge and use Ubuntu as your server, however,check thw Wiki at:

[https://wiki.ubuntu.com/ApachePHPMySQL](https://wiki.ubuntu.com/ApachePHPMySQL)

for setting up Apache. 

A good security guide is located at: 

[http://www-128.ibm.com/developerworks/linux/library/l-seclnx3/?ca=dgr-lnxw63SecLinP3](http://www-128.ibm.com/developerworks/linux/library/l-seclnx3/?ca=dgr-lnxw63SecLinP3)

make sure you know your firewall and do system audits to see who has been trying to access your site. Might want to get something like tripwire also to make sure that you can tell when anything has been altered.

---

