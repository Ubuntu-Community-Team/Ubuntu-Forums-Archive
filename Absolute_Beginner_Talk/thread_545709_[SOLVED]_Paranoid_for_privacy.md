---
title: "[SOLVED] Paranoid for privacy"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by nicenick on 2007-09-07
It is my system, my life, my business, NOT ANYONE ELSE.
Ok, I abandoned M$ because I could not control all the data windows collected about my every keystoke.  
1. Now I find Ubuntu is logging EVERYTHING I do in /var/log/<everything>.  How do i prevent this from happening? How to I prevent Ubuntu from logging anything?  I know, this helps in troubleshooting, but if my sytem works fine, I have a 'live CD' and I can reload Ubuntu easily at any time, WHY do I want anything recorded?
2. How do I prevent every file I open from being displayed in Places>Recent Documents so I don't have to remember to go there each time I am ready to turn off my computer and remove them?
3. How do I make a secure system, I don't want anything recorded, stored, saved, viewed, ANYTHING.  It is my system, my business and is not for sale to anyone.  Why is anything being recorded!!!!
Is there an Ubuntu for paranoids (they ARE watching me) perhaps an aluminum foil hat I can put on my monitor to prevent the aliens from reading my e-thoughts:lolflag:

Thank in advance,
Nice Nick

---

### Post by ExSuSEusr on 2007-09-07
Good question.. I too would like to know.  I was compromised by a key logger (hidden in a virus) on Windows (hence why I formatted with Linux and 'tossed' the Windows disks away).

---

### Post by Beggar on 2007-09-07
As far as I know there isnt really a way to disable either of these features as for the majority of other users both of these very commonly used items. If you really care that much, what about a cron job that deletes ~/.recent-documents and /var/log/*? Alternatly you could create a script that does this on every log off, would that be acceptable?

---

### Post by ORBiTrus on 2007-09-07
*rollseyes*

Nice.  I exp. like #3 - nothing to be viewed.... hah.

OK, joke of the day is over.  Let's not keep this at the top of the forum.

---

### Post by asmoore82 on 2007-09-07
just copy the LiveCD to your harddrive and never actually install Ubuntu.

It's all gone when the power's off.

:lolflag:

---

### Post by ORBiTrus on 2007-09-07
hah, asmoore...

That would work wonders, but what if someone sticks a transmitter on the RAM like in (*shudder*) Charlie's Angels?

---

### Post by Chris S. on 2007-09-07
[http://en.wikipedia.org/wiki/Van_Eck_phreaking](http://en.wikipedia.org/wiki/Van_Eck_phreaking)

solution: tin foil hat for the computer

[http://www.lattimore.id.au/images/tinfoil-computer-2.jpg](http://www.lattimore.id.au/images/tinfoil-computer-2.jpg)

Good luck!

---

### Post by nicenick on 2007-09-07
Beggar,
This would be a fine solution, HOWEVER, I am a newbie and I have no idea what a 'cron job' is (lol I can quess some really wild things). A script that does tis at every log off would also be nice, but you may as well ask me to write the equation for sending an orbitor to Mars, Not likely to happen with out major intervention.

Please help me do these things, I seems I hit a sore point to many others also

Regards,

nice Nick

---

### Post by Wiebelhaus on 2007-09-07
["Kleansweep"]("http://www.kde-apps.org/content/show.php?content=28631")

*You can get this from add/remove in U)buntu btw*

```
[IMG]http://www.kde-apps.org/CONTENT/content-pre1/28631-1.jpg[/IMG]


[IMG]http://www.kde-apps.org/CONTENT/content-pre2/28631-2.jpg[/IMG]


[IMG]http://www.kde-apps.org/CONTENT/content-pre3/28631-3.jpg[/IMG]


```

---

### Post by ORBiTrus on 2007-09-07
Look, if you are REALLY serious, do what I do.

I have an old 386.  It's a nice system.  But it's old.  So, I installed OpenBSD on it.  All my monitors are already tasked elsewhere, and this one takes MCA cards (which I don't have) so I have to dial in to the web.

Basically, it's a keyboard attached to a box.  When it's ready for me to log in it beeps so I know.  I have anything I consider extremely sensitive on it there - all my sleeper cell contacts at ABC mostly (that's a joke in case you don't watch the news and know about Chaser).

So I turn it on, wait, log in, perform tasks which queue, then connect and let them send.

Sure, you have to be used to the good old days when displays were too expensive to use, and a strong knowledge of ex won't hurt, but hey, it works and it's 99% secure.

---

### Post by nicenick on 2007-09-07
Used Synaptic Package Manager to install kleassweep, but when I selected kleansweep from Applications>Accessories It said a directory did not exist.
So I remove kleansweep from my system and rebooted.

---

### Post by nicenick on 2007-09-07
It just seems like not asking too much for ME to control MY computer with MY information and My surfing activities.  As soon as 'others' (read Microsoft, Google, Yahoo, etc.) get involved the thought of 'I can make money selling other peoples lives' (basic IT) then privacy gets lost.  If 'others' can make a dollar selling my information, why can't I get a dollar from them for sharing my information? If they don't want to share with ME, their bread and butter, Why should I sotore this information for them to be able to read.  Therefore, I want my computer to store nothing, save nothing, share nothing (soulds like Sgt. Shultz from 'Hogans Hero's) Then I am happy.

Nice Nick

---

### Post by Paulmd on 2007-09-07
> **asmoore82 said:**
> just copy the LiveCD to your harddrive and never actually install Ubuntu.

It's all gone when the power's off.

:lolflag:

Better yet, Remove the hard driive altogether. It would be a bit slow, but there's zero chance of data being stored on the hard drive when you don't have one. 

Knoppix (a different distro) actually runs better on the live cd than it does when installed. :)

You can even burn CDs in Knoppix, provided you have a second CD drive.

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by Tiekyl on 2007-09-08
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

I did a couple minutes of searching, I'm trying to setup something to execute every night on my comp, and this *might* be a good place to start if you want to just clean up your computer every night. 

Otherwise, if you have a good cd burner, there was...umm...puppy linux maybe? That lets you make a multi-session CD to burn stuff to the CD, which also might be a solution.

---

### Post by nicenick on 2007-09-08
Maybe I am being niave, but why is it so important for an operating system to do things without my knowledge? I remember fondly good old DOS.  it never did anything without being told to do so. In fact most times it didn't do anything when you did tell it to. Seriously, why can't the OWNER of the Hardware and De-Facto Owner of the software have control of his own system? Plainly, I don't want this or any other information saved, shared, stored, without my explicit consent.  What am I missing that I can not control all aspects of my system?

Seriously, 
Nick Nick

---

### Post by Tiekyl on 2007-09-08
I can understand why Linux would appeal to you, really. I think most of the time its really trying to do good...like saving the log files incase something goes wrong. Maybe you can find a distribution that lets you control a lot more, but didn't you say that you were relatively new? The more friendly OS's have to do a lot of this stuff without asking, or else people that didn't know would mess it up. (My thoughts are running together, tired)

---

### Post by ORBiTrus on 2007-09-08
> **nicenick said:**
> It just seems like not asking too much for ME to control MY computer with MY information and My surfing activities.  As soon as 'others' (read Microsoft, Google, Yahoo, etc.) get involved the thought of 'I can make money selling other peoples lives' (basic IT) then privacy gets lost.  If 'others' can make a dollar selling my information, why can't I get a dollar from them for sharing my information? If they don't want to share with ME, their bread and butter, Why should I sotore this information for them to be able to read.  Therefore, I want my computer to store nothing, save nothing, share nothing (soulds like Sgt. Shultz from 'Hogans Hero's) Then I am happy.

Nice Nick

Uhhh.... use SELinux or AppArmour, and set up the profiles so third-party programs can't read the relevant sections?  That's REALLY a lot easier than going tin foil hat and trying to protect your physical environment.  Unless you don't trust the NSA/SuSE respectively; I know I don't trust the NSA, those bastards are probably reading this email message and plotting the next invasion of Canada.  [No comment, I know some classified things; but they might be old enough to be declassified now.]  Simply put, they want the gold in the Artic.

You think that the Canadian forces doing activities in the Artic circle, Global Warming, Bush's pro-carbon stance, US tax terrifs on Canadian goods [despite NAFTA which WE still have to honour], and increased interest in a direct land-based connection to Alaska are all circumstance?  Make no mistake, WW3 will either be triggered in the middle east, or in the Artic circle.  OK, maybe there won't be a war, but the powerkeg is packed right now [Russia wants it, the US wants it, Canada claims it, NATO's breaking down, the commonwealth still is strong, etc.]

---

### Post by nicenick on 2007-09-08
Tiekyl,

Oh man, this is great, this looks like the ticket I was looking for.  Contrab help this is a great starting resource.

Many Many thanks for this.

I will consider this matter closed for now.
Thank you Thank you Thank you.

---

### Post by Tiekyl on 2007-09-08
Wee. Glad to help!

---

### Post by nicenick on 2007-09-08
Orbitrus
Thanks, I will look into AppArmor, I intend to change to Ubuntu 7.10 Gutsy Gibbon in October.  I preparation, I have some hard disk utility to set the entire hard drive back to FF which I will do before loading Gutsy. 

I think gold in the artic is a flight of fancy, however, when the Ice melts and the southern climates get too hot, I would like to have a few acres in the upper yukon to move to.

President Bush, sorry, no one in America listens to that clown anymore. Look up in Wikipedia "Lame (as in broken ***) Duck".  [see Moron]
Nice Nick

---

### Post by Paulmd on 2007-09-08
> **nicenick said:**
> Maybe I am being niave, but why is it so important for an operating system to do things without my knowledge? I remember fondly good old DOS.  it never did anything without being told to do so. In fact most times it didn't do anything when you did tell it to. Seriously, why can't the OWNER of the Hardware and De-Facto Owner of the software have control of his own system? Plainly, I don't want this or any other information saved, shared, stored, without my explicit consent.  What am I missing that I can not control all aspects of my system?

Seriously, 
Nick Nick

Logs let you know if you've been hacked. They are also useful for troubleshooting.

None of the system logs contain personal data.  

Your internet browser has a cache of recently accessed files. this is quicker than re-downloading them. Especially via modem. It also stores browser history. Both features can be turned off.

Not that turning off all logs will keep people from finding your porn. :)  And lots of it would be in the swap partition, as would anything you loaded. 

The only way from perventing information from being stored is to run the live cds. You really can browse the web, and do lots of things without a hard drive with live cds. It's slow. but it works.



If you want good old dos 6.22 I think i can find a copy. 8)

---

