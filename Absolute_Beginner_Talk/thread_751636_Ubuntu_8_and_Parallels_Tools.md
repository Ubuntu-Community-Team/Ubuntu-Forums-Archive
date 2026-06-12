---
title: "Ubuntu 8 and Parallels Tools"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by marksch on 2008-04-10
Hello,

Thank you for taking the time to read this.

I m trying to install Ubuntu 8 in Parallels 2 (the live CD currently available for download). Everything goes fine, until I have to install Parallels Tools. When I run the Parallels-Tools.run script in the terminal, it runs fine, until I get an error message along the lines of "can't find xorg".

I had no problems with Ubuntu 7. Does anyone have had this problem before and what can I do to get Parallels install its Tools?

Best,

Mark

---

### Post by wolfen69 on 2008-04-10
someone here may have an answer, but you may be better served asking in a mac forum.

---

### Post by marksch on 2008-04-10
Dear wolfen69,

Thank you for your reply, but I'm afraid it isn't too helpful.

Best,

Mark

---

### Post by roazena on 2008-04-11
The answer to your problem is [here]("http://forum.parallels.com/showpost.php?p=100399&postcount=3"). Basically, Parallels Tools for Linux is designed to interface with X.org 1.3.x but Hardy uses 1.4.x (prerelease), which is not backwards compatible.

When Parallels devs can get it together to make X.org 1.4.x modules and fix their detection code to manage the difference better, it should work. Given that Hardy is 13 days away from being an official release, they'd better do it sooner than later.

---

### Post by jamescoy on 2008-05-09
As you may know by now, Parallels released a new build today and unfortunately it still does not install Parallels Tools correctly to Ubuntu 8.

If one were to install xorg 1.4 separately, would that help things along?

---

### Post by inportb on 2008-05-09
As said, you need xorg 1.3. Gutsy has that.

---

### Post by hidden_premise on 2008-06-22
Here is the parallels tools iso that works with ubuntu 8. I pulled this out of a beta build of parallels that I compiled. There is an issue with screen size. You need to edit the xorg.conf in the X11 folder. There is a line that refers to parallels screen, you will see 800x600, change that to whatever you want. The file you need is attatched.

---

