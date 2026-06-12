---
title: "Help me please"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Nuxta on 2006-07-20
G`day everyone. I am brand new to ubuntu and have just installed it on my laptop but now I have re-booted it is asking me for a username and password which I dont know. Any help would be greatly appreciated.](*,)

---

### Post by Jasper Houtman on 2006-07-20
Didn't you have to fill one in when you installed? Just enter those.

---

### Post by Nuxta on 2006-07-20
At no time during the setup process did it prompt me for a username or password

---

### Post by aysiu on 2006-07-20
Did you do an OEM install...?

---

### Post by Nuxta on 2006-07-20
Yes

---

### Post by catlett on 2006-07-20
Are you sure you don't remember this screen from the install? [IMG][IMG]http://i80.photobucket.com/albums/j180/brthomas503/username.jpg[/IMG]
Sorry about the blurry image, I cut it out and then blew it up from Aysiu's guide.

---

### Post by Nuxta on 2006-07-20
I definately never had any log in screen like that. I put the Cd into my laptop and rebooted. It asked a few questions about configs along the way but not for username and paswoord. Now I only get as far as the first log in screen.

---

### Post by stricevics on 2006-07-20
> **Nuxta said:**
> I definately never had any log in screen like that. I put the Cd into my laptop and rebooted. It asked a few questions about configs along the way but not for username and paswoord. Now I only get as far as the first log in screen.

If you didn't do almost anything with your installation, wouldn't it be easier to reinstall it and pay more attention to each step this time? I mean, you haven't even logged on once, so all you have to lose is 30' of your time to do it again.

Just throwing a suggestion here. Good luck anyhow.

Stan

---

### Post by catlett on 2006-07-20
I would recommend downloading the Live CD installer or the Alternate Install CD. They can both be found here [http://www.ubuntu.com/download](http://www.ubuntu.com/download) Just select your region and it will give you the iso links.
This is a how to for the Live CD installer [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) (It is where I got that screenshot)
This is a how to for the alternate cd installer [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) There are 3 illustrated examples based on what filesystem windows is on. Even if you don't have windows, it will still show you the process, You just won't have to worry about the windows partition if you don't.

---

### Post by Nuxta on 2006-07-20
thanks catlett, im doing that now.

---

### Post by stricevics on 2006-07-20
OK, now I'm getting a little bit confused. What exactly am I missing here:

1. there's an installation CD;
2. user starts installation procedure;
3. installation procedure runs normally but does not prompt user to set credentials at anytime;
4. installation procedure finishes, machine reboots;
5. user is supposed to enter credentials that user was never prompted to set in the first place?!

Can it be that it had some generic, default credentials (root:admin)?

I guess my next question would be for Nuxta - where did you get the installation CD?

---

### Post by Nuxta on 2006-07-20
You wouldn not believe it, right after began reinstalling the cd I found a site with a heap of info and it said the user name is oem for the initial boot.

---

### Post by cosmicthoughts on 2006-07-20
If you did an OEM install, I'd imagine your username would have been oem. It *should* have asked you for a password (which you had to enter twice).

I say should, as that is what happened to me, and I was dumb enough not to realise what the username was the first time I installed. :D

edit: just saw your post.

---

### Post by Nightmist on 2006-07-20
> **Nuxta said:**
> You wouldn not believe it, right after began reinstalling the cd I found a site with a heap of info and it said the user name is oem for the initial boot.

Aww...

Have a Cup of Ubuntu to cheer you up!
As long as it worked out in the end.
I fixed all my Ubuntu woes for today as well.
Now I'm waiting for my new LCD monitor. Now sitting on a CRT with brightness and contrast both turned to 100% so I can see anything at all. And it's still dark!

G'nite.

---

### Post by stricevics on 2006-07-20
> **Nuxta said:**
> You wouldn not believe it, right after began reinstalling the cd I found a site with a heap of info and it said the user name is oem for the initial boot.

Well, good. You're set now. Good luck with your new OS. :)

Stan

---

### Post by cosmicthoughts on 2006-07-20
don't forget to run sudo oem-config-prepare to get rid of the oem account and setup your own.

---

### Post by Nuxta on 2006-07-20
Thanks for the tips and help guys, what a learning curve Ive embarked on.:D

---

### Post by catlett on 2006-07-20
Believe it or not, you just added to the community. Now peope can find out that oem is the user name for the first boot after an oem install.
I never knew that and now I can pass it along or someone may stumble upon this thread and solve their problem.
So to wrap up the oem install first boot.
The username is ```
oem
``` Once logged in, you have to run
```
sudo oem-config-prepare
``` To create an account (thanks for that command goes to cosmic thoughts)
It may not be easy but it is fun and rewarding. Better than a night watching bad sitcoms.

---

