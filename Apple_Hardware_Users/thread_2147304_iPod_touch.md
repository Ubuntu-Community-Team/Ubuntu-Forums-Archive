---
title: "iPod touch"
date: 2013-05-21
forum: Apple Hardware Users
---

### Post by findingthebalance on 2013-05-21
After upgrading to Ubuntu 13.04 I am unable to sync my ipod touch to any of the suggested applications, Rhythmbox, Banshee, etc. I get the unable to mount error and an unhandled lockdown (-17) error and an unable to open MTP device error. Rhythmbox will sometimes detect the iPod, but will not sync and then after a few moments lose connection and crash. Searching the forums I have found many people with the same problem but no solutions. Is there anyway of making the iPod touch work with Ubuntu?

---

### Post by findingthebalance on 2013-05-22
ON this Ubuntu forum there is nobody that can offer assistance, really??? Looks like I will have to reinstall Windows 8. I am actually quite disappointed.

---

### Post by rkmugen on 2013-05-22
If I may speak frankly, you don't really come across as a very patient person.  But I'll spare you from my other opinions (I'm just being honest/sincere).  Having said that, [COLOR=#ff0000]**_though I don't even have an iPod and that I don't even have Ubuntu installed, I'm STILL willing to try to help you out_**[/COLOR].  So, I have done a Google search and I came up with these the following possible solutions you can try.

You didn't specify your Generation of the iPod Touch.  To my understanding, there are currently 5 generations total.  Depending on which generation you're using, you might have a version of iOS that Ubuntu simply has no other workaround for (currently), short of outright "jail-breaking" your iOS device.  I can't anticipate the entire list of consequences or advantages of "jail-breaking" your iOS device, but I imagine that the very latestest versions of iOS are specifically designed by Apple to prevent users from using their iOS devices with OSes that aren't either Mac OS X or Windows.  So, you can try any of the suggestions I list below WITHOUT jail-breaking your iPod Touch and see how far that takes you.  But if you're willing to take on a bit more risk, you could jail-break it and then retry the suggestions below.

Because I don't know which iPod Touch you're using, you can do a simple Google search to figure out how to jail-break your particular version of iOS before attempting to use it in Ubuntu (or any other Linux distro for that matter).  This Wikipedia entry should give you more of an idea about what's involved when you attempt to perform the "jail-break":[INDENT][http://en.wikipedia.org/wiki/IOS_jailbreaking](http://en.wikipedia.org/wiki/IOS_jailbreaking)
[/INDENT]

Side note, you might be interested in knowing the lowest/highest version of iOS your iPod Touch supports.  Perhaps you could downgrade or upgrade iOS to suit your Ubuntu needs...  so, see this Wikipedia table that displays them all for you, in order:[INDENT][http://en.wikipedia.org/wiki/IPod_Touch#Current_versions](http://en.wikipedia.org/wiki/IPod_Touch#Current_versions)
[/INDENT]

This post involves adding a PPA to your software repo... just pay attention to how the end of the link he provides says "filter=lucid", it probably should say "filter=raring".  And if you change it to say so, you should be pointed to the most recent versions of those packages for 13.04:[INDENT][http://ubuntuforums.org/showthread.php?t=1908672&p=11955803#post11955803](http://ubuntuforums.org/showthread.php?t=1908672&p=11955803#post11955803)
[/INDENT]

A YouTube personality "OSFirstTimer" has a video of his process about accessing the media files in a file manager window (the default file manager being "Nautilus"; not using Rythmbox or Banshee or anything else) on his iPhone, which is jail-broken, btw.  Though he is using 12.10 and an iPhone, I imagine the process of doing the same thing with 13.04 and your iPod Touch wouldn't be too different.  As his name suggests, he's pretty much a novice, but as his video suggests, the process is more or less straight forward... just plug in your (jail-broken) iPod and browse through the files in a Nautilus window:[INDENT][http://www.youtube.com/watch?feature=player_detailpage&v=LuTv92LOy1U#t=1044s](http://www.youtube.com/watch?feature=player_detailpage&v=LuTv92LOy1U#t=1044s)
[/INDENT]

Depending on your version of iOS, you might be able to install an older version of iTunes through WINE and ATTEMPT to use iTunes to sync your iOS device (NON-JAILBROKEN).  Again, i don't use iTunes, so I wouldn't be able to guide you through this even if my life depended on it.  But check here to see what versions of iTunes work (and to what degree they work) with the most recent version of WINE:[INDENT][http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)
[/INDENT]

While you're at it, you might want to ensure the integrity of your iPod Touch's library and that it isn't corrupted.  According to this older Ubuntu question asked by TheBlackParrot, he gives mention to resolving the issue by restoring the library on his 2nd-gen iPod Touch and then being able to use it with Banshee:[INDENT][http://askubuntu.com/questions/220395/banshee-cant-see-my-2g-ipod-touch?rq=1](http://askubuntu.com/questions/220395/banshee-cant-see-my-2g-ipod-touch?rq=1)
[/INDENT]

If all else fails, or if you are absolutely against jail-breaking your iOS device, you could just dual-boot between Windows and Ubuntu..... yes, it is a pain to have to be booted into Ubuntu and doing everything else with ease, then having to boot into Windows, just to sync your iOS device.  But if it gives you the best mix of what you need, the choice is pretty obvious.

I doubt that running the Windows version of iTunes within Windows, WITHIN [COLOR=#ff0000]_**VirtualBox**_[/COLOR], WITHIN Ubuntu 13.04 would work since Ubuntu itself can't properly detect your iPod in the first place.

That's all time I have to spare to help you... but I sincerely hope it made some difference.  Perhaps someone more knowledgeable can come by and chime in on this (or perhaps even correct me)... in either case, so much the better, i suppose.

---

### Post by rkmugen on 2013-05-22
I also stumbled onto the following post by user "sgk" about how he managed to get his iPod to work with Ubuntu 12.04 with "GtkPod" and VirtualBox with Windows XP installed on top of it.... it might work with Ubuntu 13.04... but honestly, your mileage may vary.
[INDENT]
[http://ubuntuforums.org/showthread.php?t=103071&p=12623114#post12623114](http://ubuntuforums.org/showthread.php?t=103071&p=12623114#post12623114)
[/INDENT]

---

### Post by findingthebalance on 2013-05-22
[COLOR=#000000][FONT=Verdana]I thank you for your reply and I apologize if sounded impatient which I guess I was being a little. I had spent several days trying to get my apple devices to work, but could not, but still no excuse for a sharp tongue. I reinstalled Windows [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]**8 and**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] then installed Ubuntu alongside which solved my problem. I have been using Ubuntu for some time now and except for a few snags here and there I do think it is one of the best Operating systems going and I do plan to use it as my primary OS. Thank you again, Cheers[/FONT][/COLOR]

---

### Post by rkmugen on 2013-05-22
You're welcome.

---

### Post by psychocircus on 2013-05-24
There's a known bug in 13.04 which causes sync issues in various media players:

[http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg226501.html](http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg226501.html)

In 12.10 and earlier this bug doesn't exist and you can manage your media players without any issue.  I was managing the songs on my iPod and the associated playlists on the iPod through Ubuntu until I went to 13.04 :-(

---

