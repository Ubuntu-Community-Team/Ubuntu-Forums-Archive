---
title: "Parental Control"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-03-26
Hi Community,

There is only one good thing I think that has come out of Windows Vista and that is it's Parental Control monitoring system which you can set when users can log onto the PC, what software they can run, set websites they can visit, set times they can surf the net and the list goes on.  Big A+ for this Vista.

Now... does Ubuntu have any equivalent?

---

### Post by Google Spider on 2008-03-26
This one is for Linux
[http://dansguardian.org/?page=whatisdg](http://dansguardian.org/?page=whatisdg)
But I have never used this and don't know how it will work on Ubuntu.

---

### Post by oedha on 2008-03-26
Dans will work in ubuntu....
and also you can take a look to ubuntu moslem edition it has WCC as parental control

---

### Post by spupy on 2008-03-26
Check out the Firefox extension LeechBlock:
[https://addons.mozilla.org/en-US/firefox/addon/4476](https://addons.mozilla.org/en-US/firefox/addon/4476)
It can do the web-related things you listed. Of course, password protected.

---

### Post by kolisikepu on 2008-03-26
Thank you for the suggestions, but not only am I wanting to filter Web contents, but I also want to restrict times the PC is used by a particular user, times they can use broadband, etc.

To be exact with what I'm hoping for Ubuntu is the following;

[http://www.microsoft.com/windows/products/windowsvista/features/details/parentalcontrols.mspx](http://www.microsoft.com/windows/products/windowsvista/features/details/parentalcontrols.mspx)

In a nut shell, exactly what Vista has for Ubuntu.

---

### Post by oedha on 2008-03-26
based on your link......
dansguardian still my suggestion
and for time to access.....i dont know yet....but it still can be cofigured by turning on and off the network/internet from crontab ( linux scheduler ) CMIIW :)

---

### Post by kolisikepu on 2008-03-26
What about access to the computer??  Not only web contents.

---

### Post by SunnyRabbiera on 2008-03-26
well you can close off certain permissions per account via the users and groups apps, you can also change the password on your own in that.

---

### Post by queuedvariable on 2008-03-26
Well, presuming your young'uns don't have root, you could schedule a crontab to disable their login at certain predetermined times.  The easiest way to do this is to use passwd's lock function in cron.

So, say you wanted your progeny to only be able to use the computer between 7 and 9 PM on weekdays.  The output of crontab -e run as root should look like this:

[IMG]http://staff.washington.edu/lynx/chilluns.jpg[/IMG]

(where 'progeny' is replaced by the litl'uns account name)

This locks the password for that account every night at 9pm, and unlocks it at 7.  It won't boot them- just will only allow logins between those times.

---

