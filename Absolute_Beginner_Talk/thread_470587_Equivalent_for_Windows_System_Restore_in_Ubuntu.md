---
title: "Equivalent for Windows System Restore in Ubuntu?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by LANjackal on 2007-06-11
I hope this hasn't been posted already, but I searched and couldn't find an equivalent, so here goes:

**Is there a program/feature in/available for Ubuntu that performs the equivalent of System Restore* in Windows?**

*For those of you who haven't touched Windows in aeons ;) System Restore allows you to roll back system settings to a previous point in time, usually to recover from some unknown error.

Please note that this is NOT a file/partition backup question - I already know that's possible.

Thanks a lot for your help!

---

### Post by lazyart on 2007-06-11
This question comes up from time to time and as far as I know, there is no equivalent in Linux.

---

### Post by Dedoimedo on 2007-06-11
Hello,

Yes there is. It's called file backup. Because in Linux, everything is a file.

In Windows, you have the magic "registry", which is essentially what gets backed up in System Restore, along with the crappy default My Documents and such. Because most people do not know how to access or backup registry or play with other fortune cookies of Windows.

So, write a script that backups up your system settings and you're done!!
Dedoimedo

---

### Post by Jimmyfj on 2007-06-11
Why would you want anything like system-restore software that only eats up your computers resources?

If you crash your system a few times you soon find out that in Programs/Add or remove you have tools available for both backup and restore of user-settings

---

### Post by LANjackal on 2007-06-11
> **Jimmyfj said:**
> Why would you want anything like system-restore software that only eats up your computers resources?

If you crash your system a few times you soon find out that in Programs/Add or remove you have tools available for both backup and restore of user-settings
System Restore's saved me more than a few times on my Windows system. I kinda like it because it allows the user to fix a problem without necessarily having to know exactly what went wrong. It's also nice that it runs by default and so there's little/no configuration needed, as opposed to a system backup.

I guess the feature seems to run counter to the "Linux way," however. Thanks for your replies, just wanted to see what's out there.

---

### Post by pointyblue on 2007-10-25
I agree with you, LANjackal. Windows System Restore is a very useful tool - it's one of the things I miss from Windows.

Having to backup everything all the time seems old fashioned when you are used to MS Windows' restore option.

Ubuntu ought to offer an equivalent.

---

### Post by LaRoza on 2007-10-25
> **pointyblue said:**
> Ubuntu ought to offer an equivalent.

You can write a script to save the files, but it isn't difficult to save them. It is not like mucking about in the registry.

---

### Post by por100pre1 on 2007-10-25
Try using Grsync often to backup your whole user folder to an external hdd or another partition. Yes, System Restore is a great tool for Windows but Ubuntu with Grsync works even better here. Use APTonCD to backup all your program packages.

```
sudo apt-get install grsync aptoncd
```

---

### Post by pointyblue on 2007-10-25
@LaRoza:

I guess you're right, but it's so much simpler when the option is just there without you having to write anything or actively backing up anything.

Of course you need to back up your files too but the System Restore option is a very useful feature for users who either didn't know how to back up or who just don't bother. In my view it's a safety net. (Even though it probably won't save you every time...)

@por100pre1:

I'll try Grsync, it sounds like a smart way to back up. Thanks for the tip.

---

### Post by steve.horsley on 2007-10-25
Since pretty-much all the system config is in /etc, backing up /etc will get you close. I saw an article once suggesting that /etc could be backed up to a subversion repository, allowing for reversion to any previous state.

---

### Post by offline on 2007-10-25
> **por100pre1 said:**
> Try using Grsync often to backup your whole user folder to an external hdd or another partition. Yes, System Restore is a great tool for Windows but Ubuntu with Grsync works even better here. Use APTonCD to backup all your program packages.

```
sudo apt-get install grsync aptoncd
```

Thanks for the incredibly useful aptoncd tool. OK that is for .debs. Can you give an example  of what to backup with grsync? For example I can think of some documents, videos, music etc. When there is  talk about backing up settings what does it mean?

Say MY feisty system crashed(my fault). OK now I have all my deb files documents etc backed up. You say is there a way for further backing up settings like what? Which folders?

Thanks

---

### Post by Incense on 2007-10-25
I think the best "system restore" for Ubuntu, is a separate /home partition, and the live CD. Then if you hose your install, you can just toss the live disc in, and reinstall. Sure you have to apt-get your programs again, but you're data is generally safe. (still back up every now and then though...)

[http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")

---

### Post by -grubby on 2007-10-25
> **LANjackal said:**
>  I kinda like it because it allows the user to fix a problem without necessarily having to know exactly what went wrong

IF you don't know what went wrong it's bound to happen again

---

### Post by pointyblue on 2007-10-25
Perhaps, but a system recovery option as Windows's is still very useful to people like my mom, my sister and my girlfriend - if you get my point.  ;)

---

### Post by ed-koala on 2007-10-25
Try running an alarm program that pops up an alert once a week (or whatever interval you like) reminding you to do a back-up, if you are like me and just forget about it all the time.

It's not Windows System Restore, but it's about as close as you're gonna get :)  Hmmm, now that I think about it, maybe the next version of Ubuntu can add an option to back up files before changing system files, and allow you to keep getting the reminder or just turn it off.

---

### Post by LANjackal on 2007-10-27
> **Incense said:**
> I think the best "system restore" for Ubuntu, is a separate /home partition, and the live CD. Then if you hose your install, you can just toss the live disc in, and reinstall. Sure you have to apt-get your programs again, but you're data is generally safe. (still back up every now and then though...)No offense, but you have got to be kidding me. Reinstallation of apps is nowhere near convenient, especially if you run a lot of them.

I get the impression that a lot of those who replied aren't that familar with System Restore. It's not a backup in the conventional sense of the word, i.e. it won't rescue your personal documents or anything like that. All it does is allow the user to force the OS to revert itself to a previous state. The OS knows these states as it takes "snapshots" of itself at regular intervals. Users and installation programs can also force snapshots.

An example of what I mean by "System Restore" in action:

- I save a document to my laptop's desktop at work
- When I get home,  PC fails to boot normally
- I boot into Safe Mode, and use System Restore to restore the OS to a snapshot taken before the boot problem occurred (System Restore allows you choose which snapshot you want)
- System Restore reboots the PC, which now boots normally again BUT the document I saved to my desktop is still there because System Restore deals with settings, not user files

The crucial part of the above sequence of actions is that at NO POINT does the user have to actively troubleshoot the issue. All he has to do is to tell the PC to recall a stable state and get back to said state.

Also notice that no actual backing up is necessary on the user's part as the OS does it all for him in the background. Nor is reinstallation required.

In response to the argument that "avoiding troubleshooting only sets the user up for the same error in the future", that misses the point. The point is that the user be able to get back to work ASAP, not that he be forced to spend hours Googling, trudging through forums and pulling his hair out.

Besides that, it's not hard to see that click-and-restore is often a lot easier for problem solving that actually directly attacking the problem, even when you know what said problem is.

---

### Post by por100pre1 on 2007-10-27
> **offline said:**
> Thanks for the incredibly useful aptoncd tool. OK that is for .debs. Can you give an example  of what to backup with grsync? For example I can think of some documents, videos, music etc. When there is  talk about backing up settings what does it mean?

Say MY feisty system crashed(my fault). OK now I have all my deb files documents etc backed up. You say is there a way for further backing up settings like what? Which folders?

Thanks

Here is my Grsync window for backing up my /home folder to an external hdd:

[IMG]http://img299.imageshack.us/img299/9775/grsyncjs8.png[/IMG]

Sorry for the delay. :(

---

### Post by carusoswi on 2007-10-27
> **nathangrubb said:**
> IF you don't know what went wrong it's bound to happen again

Last week, while working in my office, something went wrong on my XP machine.  It could no longer access the office server, couldn't see any of the LAN/WAN resources, could not access the internet.  I know I didn't do anything to cause this.  As a check, I booted into Ubuntu and the internet was working, so that ruled out a problem at the router.

I rolled XP back a few days using SysRestore, and all was fine again.  Saved me several hours of trouble shooting that may or may not have been fruitful.

Whatever happened should not have happened.  I don't know what caused the problem, don't really care.  It was one of those freak things.  Point is, I had work to get done and didn't want to spend the entire evening sorting out some goofy computer problem.  To be sure, XP may have been the cause of the problem, but, once in a great while, Ubuntu will act up.  Once in a while, I go thrashing about and mess something up (less frequently these days).  If you have your system set up just the way you want it, it would be nice to have some means to just restore to some earlier date.

Resources are the more expendable component, in my view, given the ample drive space available these days at reasonable prices.

Caruso

---

### Post by LANjackal on 2007-10-27
@ carusoswi: Thanks a lot, that's exactly what I'm talking about.

Anyway this is almost a moot topic for me, I upgraded from my XP SP2 machine back when I first started the thread to a new Toshiba running Windows Vista Home Premium, which is working out pretty nicely for me :).

Now that my budget has changed, I can actually afford a real home server instead of Xubuntu on an old laptop, so I'm going with Windows Home Server when that comes out.

Right now Linux just isn't worth the hair pulling/Googling/etc for what I want it to do, and to be honest, there's no way I wanna go have an OS install just go dead on me like Ubuntu did with reinstallation being the only viable repair option (see my signature for details). I'll probably return to it if my Vista machine gets too slow to be able to run apps effectively, which is what pushed me to Xubuntu on that old laptop.

Thanks for your suggestions,

LJ

---

### Post by linuxlizard on 2007-10-27
I haven't wished for a system restore in ubuntu ever. As a "general user", not a geek, ubuntu's been rock solid. There are ways to mess up the system, but if you are just doing "normal" things and installing software from synaptic or .debs, odds are pretty slim you will have problems that require a system restore.

---

### Post by barkej on 2007-10-27
As far as Windows Home Server, I wish you the best and also offer a suggestion. [Clark Connect]("http://www.clarkconnect.com/solutions/home.php").

---

