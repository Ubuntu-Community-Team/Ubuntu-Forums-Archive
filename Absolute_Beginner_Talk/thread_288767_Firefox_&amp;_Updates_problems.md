---
title: "Firefox &amp; Updates problems"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-10-30
i just installed ubuntu 6.06....

i saw that they were some updates so i clicked to download and install them BUT after while i noticed that some of them failed to update so i restarted,some of those who fialed were successfuly installed but others keep failing and i had to restart 2-3 times try everytime to download them until i download them

My question is always ubuntu updates like that?

And all that was last night today i when i turned my pc on i clicked on the firefox icon to surf the internet and i got this message

<<<Could not launch application

Details: Failed to execute child process "firefox" (No such file or directory)>>>

I restarted and  still the same problem

So i was forced to go to add/remove applications and download another web browser the one that i am writing you now(epiphani web broser)to get help from this forum

SSOoo pls help me

I am really apsaid and i am thinking of reformating me HD and install windows XP only

---

### Post by Xappe on 2006-10-30
you could try to open a terminal and do:

```

$ sudo apt-get update && sudo apt-get install -f

```

---

### Post by fasoulas on 2006-10-30
> **Xappe said:**
> you could try to open a terminal and do:

```

$ sudo apt-get update && sudo apt-get install -f

```

What is that commant i tried it and nothing happend?

<<i am new to linux>>

---

### Post by slimdog360 on 2006-10-30
what does it say when the updates fail.

---

### Post by fasoulas on 2006-10-30
I don't remember but i found this commant and i think it downloads firefox 2

cd ~/Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

---

### Post by fasoulas on 2006-10-30
Does anyone now about the updates why they keep failing see my my first post on this thread for details

---

### Post by SunnyRabbiera on 2006-10-30
Alright, first in what way did you update ubuntu, did you use the update wizard?
second look in /usr/bin, do you see anything that says "firefox"?

One thing I can suggest right now is try to use synaptic package manager,
go up to "system" in the top panel then go down to "administration"
then select "synaptic package manager"
enter your main password and when synaptic comes up click on "search" then a little window will pop up and search for firefox.
You might have to trudge a bit but just scroll down and see if firefox is in green (installed packages are marked in green)
if not just mark it for reinstallation or just installation, just right click it and select "mark for installation" or "mark for reinstallation"
whatever the case.

---

### Post by Bartender on 2006-10-30
> **fasoulas said:**
> i just installed ubuntu 6.06....
I am thinking of reformating me HD and install windows XP only

Do you see anything wrong with this?  Take a deep breath, calm down, and accept that you might hit a few ruts.  Most of us did.

I mean, really, what's the worst?  You might have to reinstall Ubuntu?  What the heck, why not just do that for the practice.  Then take a look [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") for directions on enabling the repositories.  Then try getting updates.

---

### Post by SunnyRabbiera on 2006-10-30
Uh huh, just take it easy.
The thing about any update is that it can endanger your system, I had problems when there was the transition to service pack 1 on windows.
Just be careful on what you update, normally the ubuntu update manager is pretty smart but there is always a chance for error no matter what OS you are on.

---

### Post by fasoulas on 2006-10-30
ok thnx for replying i solved the problem with firefox 

And about the updates i will continue using and try to solve any problems

---

### Post by SunnyRabbiera on 2006-10-30
Just remember the "add/ remove" program is mainly for newcommers but there comes a time when you will have to get your hands a little dirsty with command line or some other method.

---

