---
title: "[SOLVED] Ugh! My problems, (and hopefully aswers.)"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-16
What the @*%$ I am so out of it today. I had just finished typing this when I accidentally closed firefox... ](*,)
Anyways down to business.
I am fairly new to Ubuntu (use to play around with linx using vmware but that's it.) and am having some problems. Let's start with this screen shot:
[[IMG]http://img03.picoodle.com/img/img03/9/9/16/t_Screenshotm_f3dcdb5.png[/IMG]](http://www.picoodle.com/view.php?img=/9/9/16/f_Screenshotm_f3dcdb5.png&srv=img03)
Anyways My Compiz icon thingy is not showing up (you can acess the menu and such but there is no picture) Not a major problem but one nonetheless. Second beagle has stopped saying that it has not finished indexing which should mean it has finished indexing, but it can't find things still. AndI am getting the fugliest whatever you call it on top of my menu bar thing (whatever) and windows. I'm pretty sure it as something to do with me installing emerald... Is there some way to disable it? Yes there is more...

I am having driver problems, I for the longest time couldn't find a driver for my printer until a friend of mine who uses redhat suggested hplip (HP Linux Imaging and Printing system) Which worked great. Now I need to find a driver for my pvr (WinFast TV2000 XP Series) XP could suggezst it doesn't work with linux... But theres always some way around. And I will need A program for watching the shows such as myth tv which I had to uninstall due to my total lack of comprehension of using/ configuring it (winfast pvr comes with it but i'd have to use it with wine). Which reminds me: I installed My purchased version of Peggle Deluxe In wine but When it started all I got was sound and a black screen. So I unistalled it (by going to terminal and typing "uninstaller" then clicking remove on peggle.) I thought that my system might require a re-start so I gave it one. Then when I went to Apps/ Wine/ Pegg... OMG!!! It's still there!!! WTF??? And two compiz fusion problems: I for some reason cant enable the screensavers without compiz closing and only being able to start again once I disable it. And some of my animations don't work. I've got an GeForce 5200 with up-to-date drivers using envy so that's not it.

So if anyone can come uo for a solution to at least one of my problems I would greatly Appreciate it.
Niko

---

### Post by High Camp on 2007-09-16
Hey nikoPSK

I had trouble completely understanding your search problem so I hope I'm giving you a usable answer. I just tested my desktop search (on Xubuntu) and it does not find drives either. Try searching for a file on that drive and see if it comes up.

Also, generally when I have multiple problems I try to separate them into paragraphs so there is a clear break between ideas (problems). It just makes it easier to read and respond. If you really want to help you can number the paragraphs so people can reply to a paragraph number.

For example:

1. I have a problem with desktop search.

2. I have a problem with beagle.

3. etc.

I hope that helps, if not don't surprised, I'm a n00b.

---

### Post by Ptero-4 on 2007-09-17
For your compiz-fusion issues, you might want to try heliodor. It might be more stable than emerald (fewer rendering glitches) on your computer and it's gnome native (you use your metacity themes and using metathemes changes your window borders theme as well), but you may only use it if you are outside of USA (or any other country where M$ have strong presence), if you try this in USA or anywhere that M$ is well established in you'll get the M$ thought-police banging your door in less than a second.

---

### Post by nikoPSK on 2007-09-17
Thank you for the suggestion.... I am in canada so I should be able to use helior. I'm sorry I forgot to Number my probems, It was 2 in the morning... Anyways Linux is quite nice otherwise,
Niko

---

### Post by wirelessmonkey on 2007-09-17
FYI, I've not been able to get Peggle to work via wine either.

---

### Post by perce on 2007-09-17
I might have a solution for your black screen on video with beryl - found somewhere in the forum and working for me. You should use X windows System (non xv) as your video output. For gnome default applications go to System > Preference > Multimedia System Selector > video and choose X windows System (non xv) as your output video plugin. For non gnome application you have to look case by case in their preferencies

EDIT: I found the link, it's all explained here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback)

---

### Post by nikoPSK on 2007-09-17
Thank you very much all of you. Peggle is a wonderful game and I'ts too bad it doesn't function on linux... Is there some other kind of windows emulator for ubuntu? And thnk you for the tip about back screen. 

Why does everyone say M$ or windowz? Is there a infringement or something?
Thanks,
NIko

---

### Post by nikoPSK on 2007-09-17
Anyways I didn't have that problem but thanks anyways.

---

### Post by narehart on 2007-09-17
have you tried closing compiz before playing peggle?

if that doesn't work and you still want o remove peggle from your menu i believe you can left click the menu and it will give you an option to edit it.  You can then delete it from the menu and if you really want to make sure it's gone go to your home folder, set it to show hidden folders.  Then go into the wine folder and then into the program files and then delete it manually.  You might have to do this as administrator, however. I'm not sure because I don't have Ubuntu installed right now.

---

### Post by nikoPSK on 2007-09-17
Thanks for the tip. I went into

.wine
drive_c
program files

and deleted everything exept ieand common files. I also cleared the temp. For some reason (i deleted it from the .wine folder) utorrent still shows up whn i gto to edit menus and I caan't delete it. Thanks everyone.
Niko

Gee replys come in so fast...

---

### Post by nikoPSK on 2007-09-17
It says heliodor is for beryl. I am using Compiz fusion (which is a mergance of beryl and compiz) Will heliodor work with it?

---

### Post by nikoPSK on 2007-09-17
Animation Problems fixed! So now all I need are pvr drivers, fix to no-icon in the fusion icon, screensaver fix, non-fuglyness and beagle fix/ emerald fix! I'm getting there...

---

### Post by nikoPSK on 2007-09-21
Fusion icon solved! (read my mini-how-to!):):popcorn:

---

### Post by nikoPSK on 2007-09-22
All problems fixed exept pvr driver and pvr software.:KS

---

### Post by warmwaddle on 2007-09-22
At least you got that far... I still can't boot with the cd in the drive. I restart, there's a black screen for three seconds, then the Windows XP loading screen....then the log in screen. I went to my boot settings, and set my cd drive to first priority...nothing. Probably because the boo options were from a hibernation screen... on the start up screen there are no "press F10" or any options of the sort that I see.

I am such a newbie.:lolflag:

---

### Post by nikoPSK on 2007-09-22
> **warmwaddle said:**
> At least you got that far... I still can't boot with the cd in the drive. I restart, there's a black screen for three seconds, then the Windows XP loading screen....then the log in screen. I went to my boot settings, and set my cd drive to first priority...nothing. Probably because the boo options were from a hibernation screen... on the start up screen there are no "press F10" or any options of the sort that I see.

I am such a newbie.:lolflag:

Me too when I tried installing xubuntu on my laptop. Your computer probably doesn't meet ubuntu's specifications

---

### Post by warmwaddle on 2007-09-22
I solved it :]

---

### Post by nikoPSK on 2007-09-22
how? My laptop is slow so I thought xubuntu would be great

Laptop specs:
pentium 2 
128 RAM

:confused:

---

