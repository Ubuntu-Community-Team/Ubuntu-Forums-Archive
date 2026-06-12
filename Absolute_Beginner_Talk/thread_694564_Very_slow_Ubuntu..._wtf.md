---
title: "Very slow Ubuntu... wtf"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by wiktor91 on 2008-02-12
Well i don't know is it problem with that new version 7.10 or my computer is going mad... 
Before when i had a 6.10 i had absolutely no problems with it, but when i upgraded problems are just coming. Well i solved most of them but i have a new one that's been iritating me since i installed flash player and started watching youtube... 

Well when i watch video, picture is constantly reloading(i'm not good english speaker so i don't know a right word), it's not smooth motion, id call it lag. And when i try to listen music on youtube and when i turn on for example another tab in firefox music starts laging. It iritates me because i can't watch videos normaly... 

And not only that, when i had 6.10 version Ubuntu was so quick that i was constantly asking myself why i was so long on Windows! But now i'm seriously interested in returning to Windows because 7.10 version is much more slower than Windows and that is very anoying! For example i canot listen to music and browse web pages, because music stops or lags and even my cursor is laging. 
In 6.10 i listen to music, chat on aMSN, downloading torrents, browse web and playing flash games! Nothing lags and now such a dissapointment! 

How can i solve this because i like Ubuntu and i'm used to it already... 

Just for information i'm running on HP laptop with 512mb of RAM, 2.8Ghz Intel and ATI video card. 
My first thought from windows was that i have low virtual memory, but i don't know if Ubuntu have that virtual memory and i don't know where can i modify it... So please help me!

---

### Post by PmDematagoda on 2008-02-12
Since you upgraded to Ubuntu 7.10 and have those problems, did you try doing a clean install of Ubuntu 7.10?

---

### Post by LaRoza on 2008-02-12
> **wiktor91 said:**
> 
In 6.10 i listen to music, chat on aMSN, downloading torrents, browse web and playing flash games! Nothing lags and now such a dissapointment! 

Just for information i'm running on HP laptop with 512mb of RAM, 2.8Ghz Intel and ATI video card. 
My first thought from windows was that i have low virtual memory, but i don't know if Ubuntu have that virtual memory and i don't know where can i modify it... So please help me!

If 6.10 was perfect for you, you might want to go back to that.

It may be your graphics card. Ubuntu uses a swap partition, which is similiar (but better) than Windows's page file. It probably isn't the solution.

You could look into video card drivers, to make sure that isn't the problem.

A clean install might fix things.

---

### Post by wiktor91 on 2008-02-12
Well as i said my english is low....

I did a clean install, i had a XP and i formated disk. Installed new version of Ubuntu and here are the problems... 
I lost my 6.10 CD so i can't go back to 6.10, but i'm sure that you can help me fix my problem!

Well you mention a swap partition, when i was installing Ubuntu it asked for swap partition size, i don't remmember exactly but it said to me that swap must be at least 512mb if i remember good. I think that i put 1gb or more but i don't remmeber so that shouldn't be a problem.

---

### Post by jhenager on 2008-02-12
I had an issue with 6.10 that was imported into Gutsy when I upgraded. When I was forced to do a clean install because of a hard disk crash, the problem went away.

Lesson learned - clean install if at all possible. I would also recommend guided partitioning - use entire disk. It sounds like something went wrong during that portion of the setup.
7.10 is not any slower than 6.10, at least as far as I can tell.

---

### Post by wiktor91 on 2008-02-12
I'm using entire disk and i don't have anything than Ubuntu on disk... 

I don't want to loose all my data! Can i solve this without new install?

---

### Post by ajgreeny on 2008-02-12
Try disabling compiz in the System>Preferences>Appearance>Visual Effercts menu. It may simply be that your machine is not working very well because of that, perticularly if video is jerky and not running smoothly.  Forlong's Compiz-switch [http://blogage.de/files/1393/download?compiz-switch_0.2.0~ubuntu_i386.deb](http://blogage.de/files/1393/download?compiz-switch_0.2.0~ubuntu_i386.deb) is worth getting as you can quickly switch compiz off and on again with it by just clicking on the icon.

---

### Post by jonabyte on 2008-02-12
> **LaRoza said:**
> If 6.10 was perfect for you, you might want to go back to that.


I have found 7.04 to be much more stable than 7.10, I never used 6.10 so I can't comment on that version, but maybe give it a try??

---

### Post by LaRoza on 2008-02-12
> **jonabyte said:**
> I have found 7.04 to be much more stable than 7.10, I never used 6.10 so I can't comment on that version, but maybe give it a try??

Use whatever worked. So many people upgrade without reason.

I wouldn't use an earlier version unless I knew it would work.

I have found 7.10 to be much better than 7.04. It depends on your hardware.

---

### Post by wieman01 on 2008-02-12
> **LaRoza said:**
> Use whatever worked. So many people upgrade without reason.

I wouldn't use an earlier version unless I knew it would work.

I have found 7.10 to be much better than 7.04. It depends on your hardware.
That is true indeed. 7.10 is a much better choice as far as my desktop PC is concerned, however, 7.04 works better for my laptop computer. Odd, but a fact.

---

### Post by LowSky on 2008-02-12
Personally fiesty was faster than gutsy,, and edgy was faster than fiesty, and dapper well, you get the idea. For some reasonthe deveopers keep throwing in all these new "exciting" features, but some how along the way forgot that ubuntu was supposed to be designed to work on old hardware and be more stable than anything Microsoft has put out. I partly blame ubuntu's inclusion of compiz, and the lack of decent drivers from Nvidia and ATI, but you must also blame the user. People assume that all these new features are not goin to tax the system more than before. Fusion is great but uses more resources than Beryl did. 

For some reason Ubuntu now comes with indexing software that is automaticsally on, which is a resource hog. Bluetooth software is now automatically installed yet 99% of the hardware that people are using this version of Linux dont have bluetooth devices. Can someone please explain to me why we have bluetooth support and indexing when barely anyone want them, yet I have to answer countless post about how to set up 7 button mice? Why is no one working on a GUI for Xorg set up, I think that is more important for new users. Hell why not have the set up ask what kind of install you need, full, minimum, custom...

just realized I'm starting to get mad and rant.. time to stop..

---

### Post by wiktor91 on 2008-02-12
I turned off Indexing and nothing changes...

I'll propably somehow save most important files and download 6.10 version... 
In 6.10 version i had flash player instantly, in 7.10 i was strugling to install it and get it to work.

In 6.10 audio worked instantly, in 7.10 off course it didn't work. 

This is very sad that new versions are slower and slower and that there is so much bugs.

---

### Post by kwacka on 2008-02-12
If you have a separate partition for /home do a complete re-install. When you get to partitioning select 'manual' but do not format '/home.

The partitions will be labelled according to the partition  - e.g. hda1, hda2, hda3 - edit each partition to give it a correct mount point - if you have 3 partitions they are likely to be hda1 - / 
hda2 - /swap
hda3 - /home

If you only have 2 partitions one will be / (which will contain /home, /etc, /usr, and so on) and the other swap. Obviously if you re-partition you will lose everything in that partition.

But yo do have backups, don't you.  ;)

What graphics card are you using?

7.04 was/is the current version with long-term support. 7.10 has short-term support.

---

### Post by ajgreeny on 2008-02-13
Sorry, but I think the only LTS version so far was 6.06.  8.04 is intended to be the next.

---

### Post by cybertron3000 on 2008-02-13
Your RAM should be plenty - I'm running Ubuntu with 750MB RAM, 1.47Ghz processor, HP Pavilion 521c [and loud compared to new machines], and it only uses 17%MB RAM most of the time.  Version  7.10 Gutsy.

---

### Post by wiktor91 on 2008-02-15
> **kwacka said:**
> If you have a separate partition for /home do a complete re-install. When you get to partitioning select 'manual' but do not format '/home.

The partitions will be labelled according to the partition  - e.g. hda1, hda2, hda3 - edit each partition to give it a correct mount point - if you have 3 partitions they are likely to be hda1 - / 
hda2 - /swap
hda3 - /home

If you only have 2 partitions one will be / (which will contain /home, /etc, /usr, and so on) and the other swap. Obviously if you re-partition you will lose everything in that partition.

But yo do have backups, don't you.  ;)

What graphics card are you using?

7.04 was/is the current version with long-term support. 7.10 has short-term support.

I don't have special partition for /home
I have only swap and / partition nothing else.

---

### Post by wiktor91 on 2008-02-15
I have a ATI video card i don't know exactly, but i don't think that graphic card is a problem... if 6.10 worked fine than it's not a problem with my hardware, and Ubuntu should work good on older computers than mine. Jesus i'm very frustrated because Ubuntu is so ****** slow that i sometimes want to kick my computer and throw Ubuntu out of window! Please help me because i'm serriously thinking of installing windows again! Windows is so fast compared to this! Now my letters are delaying, i press a button and 3 seconds after the letter apears on screen.

---

