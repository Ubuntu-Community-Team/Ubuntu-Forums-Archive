---
title: "Help!  Where are the the help files?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by hiloguy on 2007-09-11
How do I get the HELP files to load?  For expample, There's a ? but the HELP on the screen, nothing happens when I click on it, and F1 is inoperative.  Do I need to install some files, and if so, what is the process?

I just thought it would be pretty cool to try HELP before littering this terrific forum with another of my many questions! :)

---

### Post by reckless2k2 on 2007-09-11
i think you mean man files? most commands or program info can be found like this:

man chmod

or 

info ls


is that what you mean?

---

### Post by Terl on 2007-09-11
Nope, he means the blue circle with the ? on the top panel next to the email icon

---

### Post by hiloguy on 2007-09-11
Actually, the typos in my previous post notwithstanding, what I meant is that when I click on the "Help" option within an application, nothing happens.  Also, there is a tiny question mark by the "Help" option, which (as in Windows) I'm assuming means there is something inoperative going on there.

Also, "F1" is supposed to pull up "help" from within an app and it does nada.

I was hoping for a more newbie-friendly help than the man, which is pretty much presented in UbuntuSpeak!

Failing that, this Forum is awesome!

---

### Post by jingo811 on 2007-09-11
I always resorted to Google when I wanted some quick and great tutorial help for a certain program.
F1, help, ? buttons, and manpages is written for robots.  I don't speak robot language 	[-(

---

### Post by mcduck on 2007-09-11
What happens if you try running 'yelp' from a terminal? Do you get any error messages?

---

### Post by hiloguy on 2007-09-11
The "Help" screen came up, along with the following error messages that are a mystery to me:

AT_SPI_Registry was not started at session startup.

IOR not set.

Could not locate registry.

---

### Post by mcduck on 2007-09-11
I found the bug from Launchpad, and the problem should be fixed in at-spi version 1.7.14. I'm currently running 1.18.1.. Did you install Ubuntu recently & have you installed all available updates? What version does 'apt-cache show at-spi | grep Version' report?

[https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/73517]("https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/73517")

---

### Post by hiloguy on 2007-09-11
I'm running 7.14 which I downloaded and installed along with all updates (then) about a week ago.  I think I'll just step aside on the "Help" access since there is so much available here and elsewhere.

Thanx for all the replies and maybe sometime in the future I'll get back to this.  Maybe the next update download will fix it anyway. :)

---

