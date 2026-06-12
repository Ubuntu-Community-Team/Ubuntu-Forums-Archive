---
title: "I really want to stick with linux"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Charles Hand on 2006-08-28
I really want to stick with linux, and it's true, modern distros are a lot less hassle than they were five years ago. But the thing is, when something goes wrong, it's just totally frustrating.

Once I exhaust the forums, the howto's, the wiki, the IRCs, and do exhaustive searches of the web, and maybe go through a few long and fruitless procedures, then I really got nowhere to go. I've tried plowing through source code, but source code is never documented or even commented.

I guess what I want to ask is, you guys who are able to get linux to work for you, what methodology do you use to solve problems? Is it just a matter of plowing through source code for hundreds of hours?

-Charlie

---

### Post by Dinerty on 2006-08-28
Honestly depends on the problem, most of the time just create a thread here and somebody will answer it.

---

### Post by orb9220 on 2006-08-28
There has never been a problem that the forums here didn't have the answer.

It might not be what you want to hear tho like specific hardware not working or need to jump thru many hoops to get it to work.

I have been lucky in that everything ran straight out of the box.

Problematic area's seem to be trying to get stuff working is:
ati video cards,wireless cards,some nvidia based mobo's,printers.
64-bit kernel versions which is why I stick to 386.
and partitioning on install which alot of people do not grasp.

Just my opion.

---

### Post by bodhi.zazen on 2006-08-28
> **Charles Hand said:**
> I really want to stick with linux, and it's true, modern distros are a lot less hassle than they were five years ago. But the thing is, when something goes wrong, it's just totally frustrating.

Once I exhaust the forums, the howto's, the wiki, the IRCs, and do exhaustive searches of the web, and maybe go through a few long and fruitless procedures, then I really got nowhere to go. I've tried plowing through source code, but source code is never documented or even commented.

I guess what I want to ask is, you guys who are able to get linux to work for you, what methodology do you use to solve problems? Is it just a matter of plowing through source code for hundreds of hours?

-Charlie

What makes you think Linux works for us? Then again Windows is not exactly problem free. Linux is just as "user debugged" as windows. With Linux you can:

1. Find a solution with a google search.

2. Post in the (Ubuntu) forms.

3. Solve it yourself.

With the last two you help others, not just yourself. Not so in windows or OSX.

For myself I use Linux because:

1. A commitment to the open source community.

2. An interest to learn and work with an OS rather then mindlessly using windows. I consider myself a "power user" and Linux puts me in the driver seat with a full set of controls.

3. At least in Linux you can inspect and modify the code.

4. Linux is more workable then windows. I find it easier to fix Linux then windows. Don't believe me, when was the last time you fixed windows?

Do I have problems, you bet I do. I have managed to break Ubuntu more then once. Would I go back to Windows because of it? 

- Never

---

### Post by IYY on 2006-08-28
You're on the right track. The more problems you solve, the more intuitive the solutions will become. As for that source code debugging; you really shouldn't *have* to do anything so complex untill you are a pro at this game, but if you have the patience, it is a great way to learn and truly understand your programs and OS.

---

### Post by r4ik on 2006-08-28
Try the CLI, break things and fix it.
Reinstall break it again get angry.
Ask the Forum.
Blame Linux.
Blame youreself and the computer.
Bash youre head into the wall and start over again.
That's is how i learned some....

Good luck !

---

### Post by lapsey on 2006-08-28
The most important thing I learned was how to back up my home directory to another disc (like a USB key) and reinstall. This way all your settings, email and saved files are still intact.

This may not be the "ideal" way of dealing with problems, but it certainly is the quickest when nobody has any idea what has happened.

---

### Post by Charles Hand on 2006-08-28
Thanks, Bodhi, I needed that. And that is exactly why I'm here. I'd love to become one of the guys who answers many of the questions, but in order to get there I have to learn it all myself. And I don't see any way of doing that besides going through line-by-line. I guess what intimidates me is, if so many high-level questions go unanswered, can I expect highly technical questions to be answered? Or will I be all by myself?

---

### Post by Charles Hand on 2006-08-28
Great answers, all. I just need to keep up the gumption!

---

### Post by xpod on 2006-08-28
Ive broke and repaired my way here from an m.e in the spring to an xp in the summer and now im breaking my way through Ubunto for the autumn...

CANT WAIT TILL WINTER......have a break....you`ll learn loads

---

### Post by TooDamFast on 2006-08-29
i started linux (ubuntu) 3 months ago with the idea that I WOULD break it.  I backed up every file that i would miss.  Ive broken it a few time in the last few months (only once did i have to reinstall it).  Its a learning process just like the first time I ran windows.  After 3 months I feel good about Linux.  I love these forums and spend a lot of time reading about others problems so if i run into them I may know what to do.  You didnt state a single problem in your post,  whats giving you the headache?

---

### Post by Toxicity999 on 2006-08-29
After a certain point you can just troubleshoot for youself and be able to come to the root of the problem... Of course this. In most cases the answer doesn't lie in the source unless you use Edgy the Source that rolls from the Devs is solid (by that I mean there shouldn't be any huge problems like what you're talking about.) It's all trial and error... I mean there are only a few problem categories really. Such as, File Links, Dependancies, Config files etc. And, they all have their own warning signs. Picking up on those warning signs narrows it down and you should already know to what package the problem occurs by common sense. At that point you can refer back to memory for what you have changed, or need to change to get things working. It's something that you just pick up as you go I guess but I don't find myself posting to the forum much when things break. Atleasts Ubuntus answer to brekages isn't to format the entire HD and reinstall like... some other competitors... It will be frustrating yes but, it's worth it if you want a free OS all your own.

---

### Post by NotoriousMee on 2006-08-29
Well, I started my first foray in to linux about a week ago and broke it 3 times already. Was up till 4 am last night bashing my head against the wall.  Haven't booted windows since I started. I like the challenge.

---

### Post by powder on 2006-08-29
Here's a little something I do to make it easier on myself if I screw something up and have to reinstall Ubuntu.  On a seperate drive I have created a file called 'dapper_install.txt' and I have documented all of the commands I use to set up a fresh Ubuntu installation.  It makes reinstalling MUCH easier when I can just go back to the file and copy and paste the commands, one after another, into the terminal.  I also create backups of 'xorg.conf' as well as 'sources.list' which simplifies things as well.

Here is an example of what I am talking about:
```
sudo aptitude install msttcorefonts
sudo fc-cache

sudo aptitude install firestarter mplayer-686 xchat acroread unrar gaim-guifications bittornado-gui
sudo aptitude install mozilla-mplayer mozilla-acroread flashplugin-nonfree
sudo aptitude install beep-media-player bmp-mp4
sudo aptitude install xmms-flac
sudo ln -s /usr/lib/xmms/Input/libxmms-flac.* /usr/lib/bmp/Input
sudo ln -s /usr/lib/xmms/Visualization/libogl_spectrum.* /usr/lib/bmp/Visualization

sudo aptitude install sun-java5-jre
sudo update-alternatives --config java
```

Another tip is stay away from things like Automatix and Easy Ubuntu.  Do things for yourself so you can learn them!!!

---

