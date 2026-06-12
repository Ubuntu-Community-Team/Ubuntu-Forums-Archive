---
title: "How do you add KDE and Xfce to Gnome"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by shoki on 2006-08-07
Hello All,

What is the right way to add KDE and xfce to a stock 6.06 ubuntu gnome install? I see that I can add parts of these with Synaptic Package Manager but what grouop of files should I add to get a complete install of these?

Thank you.
--Shoki

---

### Post by s6dalane on 2006-08-07
You can install KDE and XFCE with only one command:

> sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

---

### Post by padre999 on 2006-08-07
> **s6dalane said:**
> You can install KDE and XFCE with only one command:
It is better though to use aptitude instead of apt-get. Because if you don't like KDE or Xfce you can easily uninstall the packages together with all the other packages that came with it. So you can easily go back to your original configuration. This is not possible with apt-get.

so open a terminal and```
sudo aptitude
```

Then choose the packages mentioned above and install them.

---

### Post by shoki on 2006-08-08
So are you saying to do a

```
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

```

Then if I don't like it do
```
sudo aptitude remove kubuntu-desktop
sudo aptitude remove xubuntu-desktop
```

Where can I get more info on using aptitude?

Thanks for the tip!
--Shoki

---

### Post by aysiu on 2006-08-08
I would do an update first: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
``` Do not use *apt-get*!

---

### Post by padre999 on 2006-08-08
> **shoki said:**
> So are you saying to do a

```
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

```


If you run
```
sudo aptitude
```
in a terminal you will get a kind of graphical interface... just try and see. But it is also possible to use the command line as aysiu suggested in his post.

---

### Post by xpod on 2006-08-08
Sorry for butting in .Aysiu,were you advising Shoki NEVER to use "apt-get or just that it`s not preferable for the task in hand???

What should really be used for what???

---

### Post by dmizer on 2006-08-08
i would say never use apt-get if you intend to remove an installed program later.  apt-get doesn't remove intelegently.  otherwise, i haven't run into any problems with it.

---

### Post by xpod on 2006-08-08
What about when im informed of updates every other day.......The apt-get update command was what i was advised to use seeing as i could`nt use the update function that you get if you click the flashing updates icon.

Is that different.....a lot of these updates i get notified of seem like things that will never be of any use to me anyway.

---

### Post by Jagot on 2006-08-08
> **xpod said:**
> What about when im informed of updates every other day.......The apt-get update command was what i was advised to use seeing as i could`nt use the update function that you get if you click the flashing updates icon.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by dmizer on 2006-08-08
> **xpod said:**
> What about when im informed of updates every other day.......The apt-get update command was what i was advised to use seeing as i could`nt use the update function that you get if you click the flashing updates icon.

Is that different.....a lot of these updates i get notified of seem like things that will never be of any use to me anyway.
perhaps they may not be of use to you, but there are still good reasons to install the updated versions.  if for no other reason, just for security sake.

aptitude and apt-get are both differen tools (front ends) for accessing the debian package system.  they both perform exactly the same basic function. the differences are in the details of exactly how they perform this function.

for example ... there are many programs available for you to use in linux to browse the web.  just a few: opera, mozilla, firefox, epiphany ... all of them can browse the web and display a vast majority of the webpages out there.  the differences are in exactly how they get the job (of displaying that webpage) done.

so to complete the analogy, apt-get and aptitude are different from eachother in the way that opera is different from firefox.

---

### Post by shoki on 2006-08-08
Thanks all for the help... I found a how to at:
[http://ubuntuforums.org/showthread.php?t=205002](http://ubuntuforums.org/showthread.php?t=205002)

I always seem to find the how-to after asking for help. It's like I don't even know what to ask for until I have seen it once.

Anyway a lot of good information here in this thread so that's good.

I did end up using the graphical interface. Found the desktop packages in the /Tasks Section.

Would you guys always use aptitude over apt-get or synaptic?

---

### Post by Drakkor on 2006-08-08
Don't have KDE desktop ? Ok, I did: sudo aptitude install kubuntu-desktop,
downloaded all the files,got to some sort of gui configuration stuff I didn't understand,then decided to just keep my stock Ubuntu gnome configuration,because I didn't want to mess it up,and then just closed the terminal.Am I right in assuming that by closing the terminal all the kubuntu files are gone ? Because I did this and found nothing to remove.
Thanks ! [-o< 

drakkor@drakkor:~$ sudo aptitude remove kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
drakkor@drakkor:~$

---

### Post by xpod on 2006-08-08
What about the add/remove and automatix ive ended up with?  Are these just different versions of the same synaptic and apt-get & aptitude as well.

Albeit with less applications to offer(automatix seems to have got all the usual stuff going for me).

Makes a change to going out and hunting for what you think you want in windows.Having all these options and applications to look at and opt for.

So if i SEE it in one of the mentioned applications i can just click install and if i dont see what i want i can use the apt-get OR indeed aptitude commands as long as i know WHAT it`s called.

IS that all about right???

---

