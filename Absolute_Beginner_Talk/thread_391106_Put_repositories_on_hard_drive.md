---
title: "Put repositories on hard drive?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-22
Hey all, total newbie here with a question.  I've had to install a couple of items from the repositories using the Synpatic Package Manager.  In Synaptic when I click to go to Repositories it shows them on the CD.  Is there a way to copy those onto the hard drive and have Synaptic look there instead?  I just find it mildly annoying to have to put the CD in any time I want to install something.  Let me know.  Thanks.

---

### Post by 23meg on 2007-03-22
Check out APTonCD if you'd like to make local repositories.

[http://aptoncd.sf.net](http://aptoncd.sf.net)

If you don't want package managers to use the CD as a repository, just comment out the CD entries in your sources.list.

---

### Post by noneofthem on 2007-03-22
You might as well remove the CD from the repos and just activate every online repo instead and then download all the stuff without the CD. It's the same stuff anyway. And if you have got broadband it shouldn't really make a huge difference. Also you would have the up to date versions of everything and wouldn't be stuck with the versions from the CD.

---

### Post by Thrasonic on 2007-03-22
So if I just uncheck the CD repositories, uncheck them, and make sure under Internet that all of those are checked I should be good to go?

---

### Post by 23meg on 2007-03-22
Yes, if you do that, it won't ask for the CD and download from the remote repositories instead.

---

