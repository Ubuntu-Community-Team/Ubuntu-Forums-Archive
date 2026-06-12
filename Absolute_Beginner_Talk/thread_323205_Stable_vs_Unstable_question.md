---
title: "Stable vs Unstable question"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by rlynch on 2006-12-21
So I am a techy, I've always wanted to use linux, but never had an extra machine to use just linux. I've tried making the switch before with Red Hat 7.2(yes, that long ago), but I couldnt get wireless working. And what is the reason to 'switch' from one OS that can do anything I need, to another OS that only does 1/3. I used to play a lot of PC games back then. . .now im more into programming and 'console' games, so there's no need to play every game now.


Here is the question. . .
My two big issues with using ubuntu(i have 100% switched, and removed my windows partition). I download from usenet, and then upload(via ftp) with kftpgrabber. I'm copying sending 4 gig dvds(in 50mb rar files) over ethernet(going at like 8-10mb/s), and it always errors out. . .well not always, but 905 of the time is gives a 'signal 11 error) and closes.

Another program I get errors that close it is on 'klibido' which is a usenet newsreader. Now it does better than kftpgrabber, but still. . .Im on LINUX, where stability is supposed to be top priority. . .I dont get it.

I will give ubuntu it's props though, as an OS it does well. The kernel itself doesn't crash. . .but what good does that do if my programs running on it keep crashing.

---

### Post by riven0 on 2006-12-21
It's most likely a bug in the program itself. I advise you report it to Launchpad and have a developer look over it.

One thing to remember though is that Linux, technically, ***is*** just the kernel. The kernel is the base operating system, and as such, it is rock solid. However, the same cannot be said for all the programs made to run on Linux, including the program you're having trouble with. 

Basically, all user programs have bugs and occasional crashes. It's when the kernel crashes that you should start worrying. :D

---

### Post by rlynch on 2006-12-21
But what good does a 'rock solid kernel', if everything(not literally) crashes.

Don't get me wrong, if it was 'occasional', I wouldnt have an issue with it. Occasionally klibido does crash, but freezes, requiring me to X it out, and tell it to 'terminate'. This might happen once, or twice a week. That's not a big deal for me.

My issue is opening a program(kftpgrabber), logging into my ftp, going to the folder(on both sides), and initiating the transfer. Then in 10 seconds after sending 4 of the 90+ files, it crashes. I spend more time, opening it back up, logging back in, and setting up the transfers again than it does sending the files.

As the saying goes, a company is only as strong as it's weakest employee. . .the same goes with an OS. If what im trying to do, crashes each time, what good does the rock solid kernel do me.


I enjoy the 'light weight' OS, being able to use 150-200mb of ram to do all I need, instead of seeing windows go crazy and eat it all up. . .the same goes with my hdd, I enjoy not having to defrag it every week. 

I waited years before making the switch, waiting for all the things to get worked out, and work correctly. Should I not have done it?

You say report it with 'launchpad' could you give me details on how to do this? I have not done it in the past. Then again that does help by just reporting a bug, that will take months for the company that makes this non-commercial program to fix the bug, and apply it to the next version. So I ask

what program should I use then? I use kftpg because I saw it on automatix2, so I just installed it. Is there a better one out there that I should be using, that possibly won't crash on me.

---

### Post by Drevan on 2006-12-21
> **rlynch said:**
> So I am a techy, I've always wanted to use linux, but never had an extra machine to use just linux. I've tried making the switch before with Red Hat 7.2(yes, that long ago), but I couldnt get wireless working. And what is the reason to 'switch' from one OS that can do anything I need, to another OS that only does 1/3. I used to play a lot of PC games back then. . .now im more into programming and 'console' games, so there's no need to play every game now.


Here is the question. . .
My two big issues with using ubuntu(i have 100% switched, and removed my windows partition). I download from usenet, and then upload(via ftp) with kftpgrabber. I'm copying sending 4 gig dvds(in 50mb rar files) over ethernet(going at like 8-10mb/s), and it always errors out. . .well not always, but 905 of the time is gives a 'signal 11 error) and closes.

Another program I get errors that close it is on 'klibido' which is a usenet newsreader. Now it does better than kftpgrabber, but still. . .Im on LINUX, where stability is supposed to be top priority. . .I dont get it.

I will give ubuntu it's props though, as an OS it does well. The kernel itself doesn't crash. . .but what good does that do if my programs running on it keep crashing.

have you tried searching the error texts in google and seeing what you come up with? Whenever I get errors in a specific application I always do that and usually there is some forum post with a solution that usually applies to my problem as well.

---

### Post by Drevan on 2006-12-21
> **rlynch said:**
> But what good does a 'rock solid kernel', if everything(not literally) crashes.

Don't get me wrong, if it was 'occasional', I wouldnt have an issue with it. Occasionally klibido does crash, but freezes, requiring me to X it out, and tell it to 'terminate'. This might happen once, or twice a week. That's not a big deal for me.

My issue is opening a program(kftpgrabber), logging into my ftp, going to the folder(on both sides), and initiating the transfer. Then in 10 seconds after sending 4 of the 90+ files, it crashes. I spend more time, opening it back up, logging back in, and setting up the transfers again than it does sending the files.

As the saying goes, a company is only as strong as it's weakest employee. . .the same goes with an OS. If what im trying to do, crashes each time, what good does the rock solid kernel do me.


I enjoy the 'light weight' OS, being able to use 150-200mb of ram to do all I need, instead of seeing windows go crazy and eat it all up. . .the same goes with my hdd, I enjoy not having to defrag it every week. 

I waited years before making the switch, waiting for all the things to get worked out, and work correctly. Should I not have done it?

You say report it with 'launchpad' could you give me details on how to do this? I have not done it in the past. Then again that does help by just reporting a bug, that will take months for the company that makes this non-commercial program to fix the bug, and apply it to the next version. So I ask

what program should I use then? I use kftpg because I saw it on automatix2, so I just installed it. Is there a better one out there that I should be using, that possibly won't crash on me.

oh and for the newsgroup downloading, definitely check out the beta version of pan that supports nzbs. It's been in beta for a long time but the program is amazingly stable and never has crashed for me.

---

### Post by seijuro on 2006-12-21
You might try [FireFTP]("http://fireftp.mozdev.org/") or gFTP. Another thing you might consider is trying a different protocol like ssh or set up apache and do a wget from the location you are sending to. I find the apache route to transfer faster than any other method I have tested so far.

---

### Post by 3rdalbum on 2006-12-21
KDE is sometimes unstable on certain computers. No idea why.

The good news is, in my experience, Gnome works much better on such machines. So, avoid using programs with a gratuitous "k" in their name :-)

---

### Post by user007usa on 2006-12-22
> **rlynch said:**
> and then upload(via ftp) with kftpgrabber. I'm copying sending 4 gig dvds(in 50mb rar files) over ethernet(going at like 8-10mb/s), and it always errors out. . .well not always, but 905 of the time is gives a 'signal 11 error) and closes.


I would suggest the linux beta versions of filezilla.  [http://sourceforge.net/project/showfiles.php?group_id=21558](http://sourceforge.net/project/showfiles.php?group_id=21558)

I am using the beta2 right now to transfer 200MB in files as I type this.  I do this about every day.  It works very well for me.  There appears to be a beta4 out now too.

This is one nice thing about linux.  You have many choices and are not stuck with one or two programs and they do not cost $20 for the full versions either.

---

### Post by rlynch on 2006-12-22
> **3rdalbum said:**
> KDE is sometimes unstable on certain computers. No idea why.

The good news is, in my experience, Gnome works much better on such machines. So, avoid using programs with a gratuitous "k" in their name :-)

yea, i was afraid of reading this response. if i pushed myself, I could go the gnome route, but i enjoy the interface windows has 'branded' on the computer industry.

I don't go as far as making a 'recycling bin' and 'my computer' icon on the desktop,  but I do like the start menu(along with the 'home/start' button. I also put the recycling bin next to those. I then have my clock, systray, and virtual desktop on the right of it. and I love setting up another 'panel', set above. . .changing the size to 'tiny' and using that for a quick launch bar.


I just had issues configuring gnome the way i wanted the OS to look like.

thanks for all the other program suggestions too. i forgot all about pan. i used to do usenet support at a major premium newsgroup company, and i thought pan was the only linux newsreader, lol

thanks again guys

---

