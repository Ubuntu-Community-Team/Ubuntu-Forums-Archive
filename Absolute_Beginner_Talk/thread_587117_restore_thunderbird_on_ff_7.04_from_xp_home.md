---
title: "restore thunderbird on ff 7.04 from xp home"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-10-22
HIi,

I just got a new dell FF 7.04 at my office, that I'm going to be using in addition to the XP home on my desk.  I would like to start using thunderbird 1.5 on my FF 7.04.  I have backed up my profile form the XP comp, but I can't figure out how to restore the profile on my FF 7.04 computer.  I've looked at the instructions on Mozillazine, but for me they aren't that understandable.  Can anyone help me?

---

### Post by Daveth on 2007-10-22
is this  more manageable?

[http://www.cyberciti.biz/faq/linux-backup-thunderbird-email-profile/](http://www.cyberciti.biz/faq/linux-backup-thunderbird-email-profile/)

---

### Post by kebes on 2007-10-22
In your home directory, there should be a hidden directory called ".mozilla-thunderbird". That's where it stores your preferences. You'll see a directory with a random name (like e8lkjafd.default or whatever), and a file called "profiles.ini".

The easiest way to load a backed-up copy of your Thunderbird mail/settings is to copy all of the files into that directory (this is assuming that you don't have any settings/mail on your Thunderbird install in Ubuntu, otherwise this will overwrite them).


If you prefer, you can create a new directory (in /home/user/.mozilla-thunderbird), copy all of your mail files into that directory, and manually update the "profiles.ini" file.


I could describe it in more detail, but it depends on exactly what your situation is. Feel free to ask for any clarification needed.

Hope that helps.

---

### Post by ammmom on 2007-10-22
Thank you so much for answering!!!

Sort of.  I'm not understanding how to format the command line.  The name of the profile-folder from windows xp is wlrb19cq.default .  The name of the flash drive on my "places" is "disk".  

I tried typing in terminal >  $  tar -zxvf /wlrb19cq.default -c /disk 
but I got >  tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
any suggestions???  again thanks so much.......

---

### Post by ammmom on 2007-10-22
> **kebes said:**
> In your home directory, there should be a hidden directory called ".mozilla-thunderbird". That's where it stores your preferences. You'll see a directory with a random name (like e8lkjafd.default or whatever), and a file called "profiles.ini".

The easiest way to load a backed-up copy of your Thunderbird mail/settings is to copy all of the files into that directory (this is assuming that you don't have any settings/mail on your Thunderbird install in Ubuntu, otherwise this will overwrite them).


If you prefer, you can create a new directory (in /home/user/.mozilla-thunderbird), copy all of your mail files into that directory, and manually update the "profiles.ini" file.


I could describe it in more detail, but it depends on exactly what your situation is. Feel free to ask for any clarification needed.

Hope that helps.

Kebes that did it for me!!! I can't thank you enough.  I was so ready to have a self-pity party.  Thanks for helping me avoid that.

Although, I shoudn't speak so soon.  I might bump into a glitch later on.  But in the mean time, I'm estatic!!!!!

---

### Post by ammmom on 2007-10-22
I forget, can I give you a bean for your help? If so, so you mind telling me how to do that again.  Many thanks.

---

### Post by kebes on 2007-10-22
> **ammmom said:**
> I forget, can I give you a bean for your help? If so, so you mind telling me how to do that again.  Many thanks.

No, the forums don't have any official tracking like that. (The "bean count" is just the number of posts a user has made in the help forums.)

In any case, I'm glad that it worked for you!

---

