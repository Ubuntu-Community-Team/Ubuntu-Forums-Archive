---
title: "Brand new, some advice requested"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-08-29
Hello everyone! As the title mentions, I'm not only brand new to Ubuntu, but also to Unix-based OS's. I grew up with Windows (3.1 as a child, 98 for *my* first OS, then XP for the past 5 years or so). About three weeks ago, MS crashed on me for the last time, so I started looking into alternatives. I was ordering some stuff for my wife's PC online and did a random search for OS's - Linspire popped up. I was intruiged so I bought a copy and tested it out. It was new, but nothing jumped out at me. A few days later, someone who posts on a gaming MB heard about it and suggested Ubuntu. I researched a bit on the website and downloaded a copy that night. I've always been computer-literate, but sadly, the majority of my skills were honed from years of MS-based software, so open-source is...let's say somewhat familiar, but very different than what I'm used to.

I've been absorbing every bit of info I can find on both Ubuntu and open-source in general. I do have some questions though, which I'll get to in a moment. I had all of my XP files backed up on another hard drive, so I re-installed and copied everything back over. As it stands now, my Ubuntu disk has just the OS and some other small stuff on it, as I'm in the process of syncronizing everything. I installed Wine (a lot of folks have mixed feeling, I know...) because I absolutely *needed* to have specific gaming software (i'm someone what of a GemStone addict). Other that Wine and the gaming software, i didn't add anything to the install.

My questions are...

1 - What's a good all-around DVD player? I tried Kaffeine and Ogle-mmx, but for some reason, I couldn't open a DVD to play on either. I'm fairly certain I opened the Packages correctly (same way I got Wine to finally work, which failed the first two times, but I adapted my way of thinking and realized how to do it), but still no DVD. Are their any extra steps after opening the Packages? Now, I love RealPlayer for Windows, but don't want to take the easy way out by using it with Wine.

2 - For that matter and on the same subject...Recommendations on music players and .jpg/.avi/.mpg/etc. viewers? I have tons of pictures and video clips that I would love to use with the new OS.

3 - As of now, I love the desktop background, however, I know I'll want something new in a few weeks. Is it possible to add custom pics to have as a background?

4 - Some of the screen savers are just unbelievable! I went through the entire list and was amazed at how fluid they were on the setting screen. Problem is, on the full-screen mode, they're 'jumpy' and don't flow so well. Ideas on what to do?

5 - And finally, after several attempts on networking all household computers (my Desktop, wife's Desktop, wife's Notebook) through the Windows wizard, something always went wrong. Without even realizing it had happened, after installing Ubuntu on my desktop, then grabbing a file from her notebook, I realixed Ubuntu had configured the network perfectly and her two computers are now linked up. However, only her computers can locate/share from eachother. They don't recognize either OS on my desktop, which is a bit frustrating. For Ubuntu, I'm guessing it's a because of the different file syster, but why not for the XP? (more info on my setup at the end of the post)

Whew, ok that's it for now! When I first installed Ubuntu, I was 100% clueless on the actual operation on the system, but understood enough about general computing to take a few steps forward. In the 2 weeks or so, I've picked up a lot (at least I think so!) but these are still giving me problems for some reason.

Any help is very grateful, so thank you so much! Glad to be here!

Jason


My current desktop setup (completely self-built):

P25G Via Socket 478
P4 2.4
512 MB memory (32 MB shared video)
160 GB Seagate HDD (running WinXP) (slave)
60 BG Western Digital (Ubuntu) (master)

WinXP HDD is one partition

Ubuntu HDD contains:
1 GB /swap
4 GB /root
15 GB (was going to store all the XP stuff here
40 GB /home
(all formated ext3)

---

### Post by ewl1217 on 2006-08-29
1 - Follow the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9").

2 - I reccomend amaroK as a music player, not sure about other media.

3 - Yes, you should be able to browse for other pictures from the background slection menu.

4 - You might need video card drivers for the cool OpenGL screensavers. Let us know what your video card is. Otherwise, just pick a more plain one that doesn't use OpenGL.

5 - I'll have to think a little more about this one...

**EDIT:** How exactly are your computers networked? Have you set up an SMB or NFS share on your computer?

---

### Post by Bachstelze on 2006-08-29
Hi and welcome to Ubuntu :)

1 and 2 : For DVD playing, you can use VLC just like in Windows, it will work pretty fine. Personnally, I use mplayer to play pretty much everything. For everything multimedia related, see [here](https://help.ubuntu.com/community/RestrictedFormats).

3 : Of course it is possible, just richt click on your BG and look around for a bit ;)

4 : You'll need drivers for your videoacr installed.

5 : For the Samba filesharing, I can't help you much here but I know Windoze manages it extremely badly. I just got rid of that crap and use a FTP server on my network instead, which works flawlessly.

---

### Post by PPAAUULL on 2006-08-29
Ok, I will do my best at answering those questions.

1) Personaly I love Mplayer. It is a great video player for a lot of stuff and works well. Also you might need to install codecs to play dvds. for that you can look at this link. it has instructions on how to get things running like MP3s and such working. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

2)Mplayer again which you can get in synaptic. Jpegs and such can be viewed from the file explorer.

3)Very easy to get personal pictures as backgrounds. You just make sure they are the right size and then select them. I think it is a right click on the picture and set as background. I will look it up.

4)Not sure. Might just be a video issue.

5)Don't have a clue. Sorry.

I hope I help a bit.

Paul

---

