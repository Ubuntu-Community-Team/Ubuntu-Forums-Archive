---
title: "user = root"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Adventx on 2006-09-27
Yes I would like to know how I can make my main user account have root access all the time so that I'm never getting a prompt for my password either for nautilus admin settings or in the terminal. And yes I know the possibility of me messing something up due to not being warned by putting in my password but its just an annoyance that I would like to rid myself of.

---

### Post by aysiu on 2006-09-27
You leave your apartment/house unlocked too and don't have money in the bank because it's more convenient to have cash on-hand?

---

### Post by maxpower on 2006-09-27
Adding ```
%admin ALL=NOPASSWD: ALL
``` via the visudo command will allow you to run root commands via sudo without a password.

mAx

PS this assumes your user is a member of the admin group which I believe is a Ubuntu default.

---

### Post by Perfect Storm on 2006-09-27
> **Adventx said:**
> Yes I would like to know how I can make my main user account have root access all the time so that I'm never getting a prompt for my password either for nautilus admin settings or in the terminal. And yes I know the possibility of me messing something up due to not being warned by putting in my password but its just an annoyance that I would like to rid myself of.

bad idea, very bad idea...

You can make a terminal launcher which only require your password once, that's better than the other thing.... just be careful.

Make a new launcher which have this in the commandline:
```
gksu /usr/bin/x-terminal-emulator
```

---

### Post by whizbaby on 2006-09-27
Please don't even think of an all-time root login (not even speaking of graphical root login) or you will get to know other kinds of *annoyances* that won't be funny anymore. There are reasons why a root login is disabled. If you need to administer for a longer period of hours type
sudo xterm
in the terminal and start applications from the up-popping xterm (has root privileges).
EDIT:
Some like it hot...

---

### Post by Predius on 2006-09-27
> **maxpower said:**
> Adding ```
%admin ALL=NOPASSWD: ALL
``` via the visudo command will allow you to run root commands via sudo without a password.

mAx

PS this assumes your user is a member of the admin group which I believe is a Ubuntu default.
++ read that

But the correct syntax is:

```
%admin  ALL=(ALL) NOPASSWD: ALL

```

---

### Post by maxpower on 2006-09-27
Can't say I know what the difference in synatx is, but my line is working jsut fine.

mAx

---

### Post by Adventx on 2006-09-27
I just want to be able to change anything I like on my computer easily without having to go through 3 other steps in order to do one simple thing is all. Not to compare apples to oranges but if I'm in windows and just want to move some files from one folder to another then its as simple as copy and paste or drag and drop. Now with Ubuntu it wants me to do a song and dance and remember all the terminal commands just to do one simple thing. And to be honest I dont really care if I mess anything up, if I do then I'll just reinstall and try again, its the best way for me to learn stuff and Ubuntu doesnt really spell everything out for you so I'm sure that I'm going to be messing alot of things up. So I just wanted to make it easier for myself and thanks to you who gave me a good awnser.

---

### Post by aysiu on 2006-09-27
Create a launcher for the command ```
gksudo nautilus
``` Then you can click it, enter your password, and drag and drop to your heart's content.

No terminal necessary.

---

### Post by whizbaby on 2006-09-27
When in ubuntu try forgetting what you learned in windoze (especially reinstalling is not an appropriate way to solve problems in ubuntu, what will you learn by doing that?). Getting used to it you'll see it's a lot simpler, just let it happen. And how can you tell the best way for you to learn linux when you don't know what it is?

---

### Post by Adventx on 2006-09-27
I'm not trying to forget what I've already learned. I'm trying to take something new and incorperate what I know to be easier and more efficient for me into the new thing. And I'm attempting to learn through research and trial and error. My comment about reinstalling was just to say that I dont really care about messing something up on my computer and having to start from scratch because I'll know what not to do next time and that will help me learn what I should do in the future. So I'm just trying to configure Ubuntu to work better for me so I can learn how to use Linux/Ubuntu a little better.

---

### Post by Qrk on 2006-09-27
Not running as root all of the time is a feature that almost every OS shares except windows. I'd suggest not logging in a root for your default user and listening to the tips others have posted as shortcuts for doing admin work. Its just good practice as even Vista is moving to "sudo like" behavior.

---

### Post by whizbaby on 2006-09-27
> **Adventx said:**
> I'm not trying to forget what I've already learned.I'm trying to take something new and incorperate what I know to be easier and more efficient for me into the new thing.
Of course 'forget' only in linux-working. But there you should try to find out how things are supposed to be done, WinHabits don't help much with that. It's like with learning chinese, your experience with english won't help you much.
> 
 And I'm attempting to learn through research and trial and error.

Way to go.

---

### Post by kerry_s on 2006-09-27
I must admit i do that all the time so i don't have to keep typing the password when i'm setting up my computer. I know it's a bit of a risk, but it's not like i'm activating the root account :-k . It can be returned back to it's secure state at any time. I just say what's life without a little risk and you still have to use sudo, you just don't need a password.

---

### Post by annda on 2006-09-27
why not simply use the root account all the time if you're not concerned about security and safety of your computer? that seems to be the easiest way.

and no, i don't think it's a splendid idea. but if you want it, who's to stop you?

---

### Post by nts on 2006-09-27
and then come runninf here when you screw your OS by running as root all the time...

Good Job!

---

### Post by Adventx on 2006-09-27
I'm going to be messing up alot of stuff in linux and then running back here to either search through the posts or to make my own asking questions so theres really no difference. I personally learn the best by making mistakes and then realizing what I did wrong and what I should not do in the future. And I'm sure all of you didnt install Linux knowing everything about it from the moment you installed it so you had to learn as well, and I'm also sure that you've customized your Linux system to work best with you as all people tend to do.

---

### Post by NetworkGuy on 2006-09-27
i guess what everyone is saying is that if you want to really learn linux, then learn how to make things work without being root.  Sudo is a great command and yes, I have run sudo -i on occasions when I have had to make a lot of system changes back to back.  But as a practice, run as your normal user, sudo to get everything setup properly and then you should almost never need superuser permission again, except for another install or system change.  

I also work on Windows machines where I work and yes I am one of the system administrators.  After my XP laptop was setup (as administrator) I made a user account for my day to day work.  I don't need to use the administrator account, and when I do, I right-click / run as administrator.

It only makes sense, and I found out that I don't have to rebuild my XP as often as I did when I ran with administrative access.

---

### Post by Adventx on 2006-09-27
You have a good point about the being root, I've just been trying to learn about Linux alot and whenever I need to change,move, and do anything else that requires root access, having to put in my password every 15 minutes or so can be a bother. So I'm trying to be a little flexible with Linux due to the fact I'm so used to windows that I can completely reformat and have it back to the way it was before in under 2 hours. Which is why I'm not really afraid of messing anything up here on Linux because it took me forever to get my wireless adapter to work with my network but after about 2 weeks of learning commands and configs I'm now on my laptop with Ubuntu with my wireless network working great, except P2P networks, thats what I have to work on next ^_^.

---

### Post by NetworkGuy on 2006-09-27
Well, you have your mind set on this :)

We can't stop you from using root, or setting yourself up as a root account, but remember after you are done learning linux, to reload Ubuntu one more time and don't use the root account to set everything up. :)

Have fun learning.

---

