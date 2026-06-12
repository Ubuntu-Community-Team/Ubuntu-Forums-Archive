---
title: "Can't shut down"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-07-09
I only have the Log Out, Lock screen, Switch Users, and Hibernate options when I click on the Exit button or go to System > Quit.  Pretty sure Shut Down was an option before.

If I go to Log Out and type "exit" then I'll get a DOS-type screen; I guess I could hit the power button from there with minimal negative effects, but I'd rather fix the problem.  Ideas?

Also, I have a LOT of questions.  Some are clearly related to threads already posted and others, not so much.  Should I enter threads and ask my own question if it's similar to the thread title, or should I start my own thread to account for my specific hardware?

Thanks.

---

### Post by Dr. Nick on 2006-07-09
Welcome to the Forums

Their is a similar issue about the shutdown buttons [here]("http://ubuntuforums.org/showthread.php?t=192871")

It doesnt appear a solution was found, but their are a few workarounds listed. 

About starting your own thread vs positing in another, It really depends. If your issues are related to old post that are several pages long when you post at the end it is less likely to be noticed, for example people are less likely to read a 10pg thread from 4 months ago and see your question buried at the end. In that circumstance I would start a new one.

It is usually ok to post in a thread with similar problems as to say "yeah I have that issue too" but it is frowned upon by most to pick a random thread and post a totally off topic question.

As long as its a similar situation and you desire the similar outcome as the origional poster does then its really not a big deal. I just hate reading a thread concerning someones ethernet issuse and see a post from someone asking how to fix thier video card.

---

### Post by Tom Brokaw on 2006-07-09
OK, thanks for the link and the advice.  I'll give some of the suggestions in the other thread a try later, right now it's pool time.

---

### Post by Tom Brokaw on 2006-07-10
OK, it was asked in that thread if the user had started from a cold boot or had restarted Xserver.  I had done the latter, and upon a shutdown and restart (a few hours later) all six options were in the Quit menu once again.  Thanks for the pointer!

---

### Post by Dr. Nick on 2006-07-10
No Problem, Glad you got it.

---

### Post by digby on 2006-07-10
As a brief aside, it is still a bad idea to shutdown the computer from the command line by simpling turning it off.  This could potentially cause damage to your filesystems.  If you happen to end up there again, you can shutdown by typing```
sudo shutdown -h now
```or reboot with```
sudo shutdown -r now
```

---

### Post by dolphinsonar on 2006-09-19
Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

---

