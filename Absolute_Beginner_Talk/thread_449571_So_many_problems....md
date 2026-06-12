---
title: "So many problems..."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Cyann0923 on 2007-05-20
I am having so many problems with this switch they are hard to keep up with
I have sound support sometimes. Sometimes things will play everywhere, sometimes just in one player,  sometimes scratchy,  sometimes not at all. My sound card has no drivers for ALSA, So I chose open sound card in my system setting. Now the inconsistency.

Concerning my graphics card. ATI Radeon x1600 pro. That alone is my biggest problem. Every forum I check, the Graphics card is the sole problem.  I had thought I downloaded drivers for it, but now .avi and .mkv files play all jumbled in Caffeine and not at all in mplayer, maybe a little in vlc. I am so lost on that

I just so happen to have an AMD 64 processor as well. 

I installed Photoshop CS in wine,  worked flawlessly the first time, but wouldn't even run the second time.
Kept it up until I got fed up and deleted all the files. Gonna keep trying other programs,  maybe I will succeed.

Next issue happens to be my dual boot issue. Which in the end is on windows.
After many scripts and tests, I made grub realize that windows was there, and windows realize it was the slave. So,  then windows decided not to boot. Blue screen of joy. There was a file that was in the way. It was stdp.sys and it was from deamon tools. Couldn't boot into windows and delete it for the life of me.  Back to Linux. After much searching I found a way to allow read\write on my windows drive through linux. Deleted said file and enjoyed my files for a bit. Time to retry windows.
Blue screen, darn. Back to linux. Now I am unable to get back into that hard drive. Says there are no files on the drive. What am I doing wrong here????

I hate to rant, but I really desperately want to switch to linux for good. These are the issues I am having that are keeping me from that goal. I have searched these wonderful forums, I am patient, and I know how to copy/paste commands into konsole.  I love this OS and will as soon as I can be assisting people with the same problems I've had on these forums. 

I just want to know really if I should wait until I get a new computer with more stable hardware. That seems to be the biggest problem here, and my utter lack of computer knowledge. I use ubuntu 7.04 on my ps3, should I just stick with that for now????

Once again, I apologize. I don't want it to seem like I am (expletive)ing, I just really like this OS and don't want my own ignorance and Hardware faults to ruin it.:(

---

### Post by Henry Rayker on 2007-05-20
How did you install? Also, are you using the 64-bit version of Ubuntu, or the 32-bit?

For the sound issue, telling us what card (or chipset if it's onboard) it is would help drastically.

What's wrong with the 64-bit processor? I have an AMD 64 processor and my system runs like a dream.

The dual boot issue is likely one of you messed with files to the point that the system is entirely confused. There is no need for scripts...just making sure the menu.lst file (in /boot/grub) is in order.

---

### Post by Cyann0923 on 2007-05-20
Alright,  sound card  Diamond XTREME sound 7.1/24 bit.
Kubuntu 7.04 64 bit
I guess the amd 64 was an overreaction,  just needs more TLC
And I have issues with the dualboot due to windows.  Even when my Linux HD is disconnected I get that issue. The issue is that going into the windows HDD(Western Digital 250 gb, windows XP home:sp2) from linux. It worked the first time, but now nothing.

---

### Post by Cyann0923 on 2007-05-20
Also, I installed with the live CD after unplugging the windows drive. I am so smart when It comes to this stuff. During my great Dual Boot crisis,  I found out that I needed to put a jumper on my Windows drive,  but I had none,  So I made a makeshift one using some jumper shaped connectors from my tower that I don't use,  a little splice and it realized it was slave.

---

### Post by Cyann0923 on 2007-05-20
Fixed Dual Boot/windows problems. Sweet,sweet chkdsk.
And strangely enough my music plays in all media players except Amarok, which was the other way around before the windows fix.  I am so confused.

---

### Post by gigaferz on 2007-05-20
Its a good thing everything came together, anyway if you like amarok, but its not working, try exaile, it even lets you play radio, with no password.

I installed ina similar way that you did, I left the hdd set on cable select....the only one complaining was windows, but it checked itself and now its running...

---

### Post by Cyann0923 on 2007-05-20
This OS is quite fickle I find,  but it is worth it.
When I feel comfortable with linux,  I will gladly help anyone else. 
I still feel that my sound card is an issue. I have an ASUS a8n-sli deluxe motherboard,  should I just switch to my onboard sound card? The inconsistant sound is driving me insane. I have a 7.1 surround sound system, and I am a musician,  so I like to get the most out of my speakers. Scratchy sound and unreliable playback are a no-go to me. Any advice on this would be awesome.

---

