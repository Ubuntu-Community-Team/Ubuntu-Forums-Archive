---
title: "Avast! Antivirus Install Issues"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2007-12-27
I installed avast! from the .deb. I ran update-avast. I ran avastgui and put in my key. I ran the command from [http://ubuntuforums.org/showthread.php?t=229128](http://ubuntuforums.org/showthread.php?t=229128) to put the link in the accessories menu. Now when I run it I get the key box, which does not have the key that I just entered and this:

```
10:42:58 PM: can't open file '/home/ian/.avast/avastrc' (error 13: Permission denied)
10:42:58 PM: can't open user configuration file '/home/ian/.avast/avastrc'.
10:42:58 PM: Failed to inspect the lock file '/home/ian/.avast/lockfile-ian' (error 2: No such file or directory)
10:42:58 PM: Unable to detect whether another instance of avast! is running.
```

Re-pasting my key give me this:

```
10:42:58 PM: can't open file '/home/ian/.avast/avastrc' (error 13: Permission denied)
10:42:58 PM: can't open user configuration file '/home/ian/.avast/avastrc'.
10:42:58 PM: Failed to inspect the lock file '/home/ian/.avast/lockfile-ian' (error 2: No such file or directory)
10:42:58 PM: Unable to detect whether another instance of avast! is running.
10:44:56 PM: Directory '/home/ian/.avast/chest' couldn't be created (error 13: Permission denied)
10:44:56 PM: Couldn't create chest in directory '/home/ian/.avast/chest'.
10:44:56 PM: Error while initializing avast! chest.
```

What am I doing wrong? I tried deleting avastrc /home/ian like it said to do in the terminal, but get an error saying that I don't have the permissions to do that.

Help?

-Ian

---

### Post by hardyn on 2007-12-27
looks permissiony... do you have to run the update as root (eg. sudo)?
did the program directory or your home directory adopt root permissions as a result of install? this has happened to be before, although not with the avast program.

---

### Post by hyper_ch on 2007-12-28
are you sure that you you actually need an antivirus program?

---

### Post by Ian505 on 2007-12-29
> **hardyn said:**
> looks permissiony... do you have to run the update as root (eg. sudo)?
did the program directory or your home directory adopt root permissions as a result of install? this has happened to be before, although not with the avast program.

I tired to run the update as a root and I recall it seemed to work... as for the root permissions I have no idea. Permissions in ubuntu- linux in general- is something that is very new to me.

> **hyper_ch said:**
> are you sure that you you actually need an antivirus program?
There are 2 reasons windows is such a vulnerable operating system.

The first one is Microsoft- who tends to take forever and a day just to churn out a minor patch.
The second one is that it is currently on the majority of computers in the world. This is bad because when you have a OS that is the majority, hackers/spammers try to exploit holes in that majority OS because if their virus works it will affect many more people than if they targeted linux, which is mostly used by computer-savvy users anyway who won't fall for the old .jpg.exe trick.

That is changing, however, and Linux is becoming more popular everyday- and many people are lulled into the sense of invulnerability because they use linux. Newsflash- just because patchs are release extremely fast doesn't mean your invulnerable. The more people who adopt linux the better a target it is for hackers. I know that the time hackers switch away from windows may be eons away or may never come- but I want to be ready for anything... especially those few hours between the time a virus is first detected and the time a patch is released. (The slammer worm shut down more than half of the worlds servers by flooding the world with UDP pings in less than an hour.)

So, yes, I need antivirus.

---

### Post by oldos2er on 2007-12-29
It was my understanding that Avast only checks for Win* virii, so i don't see how that would do you much good.
"The more people who adopt linux the better a target it is for hackers." It isn't simply a matter of numbers. Linux has far better out-of-the-box security than Win*, plus its permissions model *shouldn't* allow "hackers" much if any entry.

---

### Post by hyper_ch on 2007-12-29
> **Ian505 said:**
> The first one is Microsoft- who tends to take forever and a day just to churn out a minor patch.
The second one is that it is currently on the majority of computers in the world. This is bad because when you have a OS that is the majority, hackers/spammers try to exploit holes in that majority OS because if their virus works it will affect many more people than if they targeted linux, which is mostly used by computer-savvy users anyway who won't fall for the old .jpg.exe trick.
You are mistaken in that point because of several things.

(1) An AV is retroactive. It's only good for fighting known viruses. M$ does not patch Windoze for it. However Linux will get patched. So the question should be, why using an unpatched OS first-hand?

(2) The number does not play as an important role as you tend to think it does. Would it be as important, than most webservers hacked would be Apache and not IIS. But this is not the case and there's an easy explanation. The basic security model in linux is totally different from M$. M$ pursuits the monolithic path, everthing must be stick together. Think about the important role that M$ IE plays. If you can find a loophole, you can take over the whole machine and it will be your zombie (hence all those botnets). However if you take over the browser in Linux, the most thing you can do is delete the according user's home folder and files. However you can't directly install some spyware et al. Even if Linux gains significant % in market share it will still be M$ as main target for attacks because taking control of a whole computer is worth much more than be able to control a few programs with limited rights.

(3) Another weakness by M$ is, that in order to define whether a file is executable is depending on the file extension. In linux however a file must first be made executable. Of course a possible hacker who gets access to your account can make a file executable but it still will not be as damaging as on Windoze.

An antivirus is needed if you operate a mail- or filesharing server in order to prevent M$ users from malware. The virus scanners for linux do not scan for linux viruses [not 100% sure about that] and hence you don't benefit at all.

I'm of the opinion that Windoze users need to take care of the security of their system themselves. It's not my job to prefent them from dangers and so I'm not going to install one.
Linux by itself is quite secure. new viruses can be released but then there wil be patches provided, no need for AV for that case. If you follow some basic rules (only use trusted repos, don't use the root account, ...) and keep up to date with the security patches there is not much harm.

---

### Post by Perfect Storm on 2007-12-29
No, anti-virus is not needed. If the claim Ian505 made was true, we'll see alot of virus' as a majority of servers are *nix related.

It's all about the the structure of the OS which makes it resistance to virus or not.

---

### Post by Ian505 on 2007-12-29
Okay okay, linux doesn't need antivirus. But if that is so... WHY DOESN'T MSOFT ADOPT THIS? I mean, they supposedly rewrote a lot of stuff in that nice 400 dollar DVD they call Vista... couldn't they have implemented it then?

-Ian

---

### Post by RomeReactor on 2007-12-29
Hi.
> **Ian505 said:**
> Okay okay, linux doesn't need antivirus. But if that is so... WHY DOESN'T MSOFT ADOPT THIS? I mean, they supposedly rewrote a lot of stuff in that nice 400 dollar DVD they call Vista... couldn't they have implemented it then?

-Ian

For one, vista changed to adopt a somewhat Unix-like approach to security with UAC; second, antivirus software is a really big business. I haven't used OS X, but as far as I know it implements a very similar security model to Linux

---

### Post by other guy on 2007-12-29
> **RomeReactor said:**
> Hi.


For one, vista changed to adopt a somewhat Unix-like approach to security with UAC; second, antivirus software is a really big business. I haven't used OS X, but as far as I know it implements a very similar security model to Linux

I would also like to add. Windows relies really heavy on stuff working backwards too. If they changed the kernel to much. Much of what folks expect would not be as expected. there is that nice comfy feeling using Windows. Change it to much. The masses will not be very happy or understand how to use the OS. Not unlike the new user to Linux.

If you want to get a feel for the Apple experience. Pop in a freeBSD live disc. It is about the closest you can get. Minus the bells and whistles of Apple. They are both based on Berkley code.

---

