---
title: "k9Copy problems"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Francis3366 on 2008-03-24
Hello, 

    I am a new user of Ubuntu.

    I have been using k9copy for the past couple of weeks to copy DVDs and when it does copy the DVD, it works fine, shrinking the data to less than 4.5 GB to an iso file.  However, this process has been sporadic as k9copy works on some disks and refuses to copy others. 

    When I then use K3b to copy the iso file to a DVD disk, the subsequent process of copying the iso file to the DVD disk goes without a hitch.  

    When I attempt to copy a DVD to an iso file and there are problems, one of the following three things occurs:  an error message; a notification that the program has crashed; the copying of nothing but garbled screens.  There seems to be no pattern as to what type of failure happens as I have run the same disk a number of times and gotten different messages.

    I have tried manipulating the settings to no avail.  I have also tried removing and reinstalling the program. I have also looked in the Ubuntu Linux Bible (von Hagen) but can come up with nothing.  I also tried installing KDE as it was mentioned in the info block on K9Copy.. 

    I also tried "Activate support for encrypted DVDs."  The first line seemed to work (sudo apt-get . . . ) but the second (sudo /sur/share . . . ) indicated, "command not found." 

    I am stuck at this point and anything you can suggest will be appreciated.

    I am using Ubuntu ver 7.10 (Gutsy Gibbon), and k9Copy, ver 1.1.3

    A this is my first post, I don't know how quickly you reply, but I will be going off line as soon as I send this and will not be back on line until tomorrow afternoon.

    Thank you,

    Francis
    [email]francis3366@gmail.com[/email]

---

### Post by mgranet on 2008-03-24
```
(sudo /sur/share . . . )
```

Is this a forum typo, or is that the actual thing you typed? It should read "/usr/share".

Also, I would not like to see your inbox. Full of the spams, it will be. :(

---

### Post by Francis3366 on 2008-03-25
Is is a typo error on this post only.  

So far no spam.

---

### Post by mgranet on 2008-03-25
Hrm. Have you the latest version of libdvdcss2? Also, can you post exactly what commands you are typing?

As for the spam, you won't see it until this thread gets cached by a search engine. It's always a bad idea to post your email address in plaintext. The Prince of Nigeria's bot will find it, and you probably know the rest.

---

### Post by Francis3366 on 2008-03-25
I had not installed libdvdcss 2.  I came across this installation on a post by royal314 last night in his post to another k9copy user.  I installed it and k9copy worked like a charm.

I thank you also for the help as well as the advice about posting my email address.  I will not do so in the future.

Francis

---

