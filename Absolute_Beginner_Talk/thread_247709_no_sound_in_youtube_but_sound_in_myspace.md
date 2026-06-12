---
title: "no sound in youtube but sound in myspace?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by dta on 2006-08-31
Hey well i am stil new to this, and search and search and i dont think that i truely understand, or its too "geekspeak" for me. so i thought i would put my post up with this, trying to explain what i know and what i need, so i hope thats ok with you all. 

first of all, i installed ubuntu and then automatix, and did that, and got the freeflash plugin to work because before i couldnt see videos on myspace, or the main video windows in youtube wouldnt show up before hand. now that i have install the automatix, i can see the videos and hear the sound on myspace, and i can also see the video windows on youtube but i cant hear anything from youtube. also the player that i see load when myspace page, pops up is the "m-player". thats about all that i know. also i am using the onboard sound card to a dell optiplex gx520. i dont know wehre to start and i would like some help. sorry if i am sounding like a newb. lol but i AM.
well thanks for the help!

edit: also, do you think this will work for me? 

> 

In my setup, this problem was fixed with this:

# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

No other changes needed.

I hope this works for other people.


---

### Post by FuzzyUnicorn on 2007-05-05
I realize the post I'm replying to is pretty old, but it's the only one I've found that explains the exact problem I was having. Hopefully this will help others who have the same problem.

I could get sound in just about every flash site (Google Video, MySpace, etc.) but not Youtube.  I tried every trick I could find on the forums (also-oss, /tmp/esd, etc.) but could never get it to work.

But, I found that if I ran "sudo firefox", sound on Youtube worked just fine. I figured it a was permission problem, but could not figure out where. Checked /lib and /usr/lib, firefox plugins directory, everywhere I could think of that might involve sound, but nothing worked. 

 I spent a couple of months looking, and finally gave up and used wine and windows firefox. 

Today after re-installing Kubuntu Feisty with my old /home partition, and still having the problem, I decided to set up a new user just to see if they had a problem. Youtube worked just fine for them, so it had to be in my profile. It turns out ~/.macromedia/Flash_Player/ was owned by root. Not sure how that happened, but chown-ing it back to my user fixed all of my Youtube sound problems.

I hope this helps someone, so they don't have to spend months without Youtube :lolflag: 

F.U.

---

### Post by overdrank on 2007-05-05
> **FuzzyUnicorn said:**
> I realize the post I'm replying to is pretty old, but it's the only one I've found that explains the exact problem I was having. Hopefully this will help others who have the same problem.

I could get sound in just about every flash site (Google Video, MySpace, etc.) but not Youtube.  I tried every trick I could find on the forums (also-oss, /tmp/esd, etc.) but could never get it to work.

But, I found that if I ran "sudo firefox", sound on Youtube worked just fine. I figured it a was permission problem, but could not figure out where. Checked /lib and /usr/lib, firefox plugins directory, everywhere I could think of that might involve sound, but nothing worked. 

 I spent a couple of months looking, and finally gave up and used wine and windows firefox. 

Today after re-installing Kubuntu Feisty with my old /home partition, and still having the problem, I decided to set up a new user just to see if they had a problem. Youtube worked just fine for them, so it had to be in my profile. It turns out ~/.macromedia/Flash_Player/ was owned by root. Not sure how that happened, but chown-ing it back to my user fixed all of my Youtube sound problems.

I hope this helps someone, so they don't have to spend months without Youtube :lolflag: 

F.U.

Hey thanks for sharing and good work. Some times you have to try things out and see if it works  and thanks again I am sure it will help someone!

---

### Post by orangep on 2007-05-06
There is a permissions problem involved here.
I was getting:
alsamixer: function snd_ctl_open failed for default: No such device
when I tried to run alsamixer.

Go to /dev/snd and
sudo chmod 666 *

I know that it shouldn't be necessary. If I put my name in the audio group,
I should have permission to read and write those devices. But it hasn't ever
worked, not in the 7 years that I've been running Debian.
So change the permissions, and suddenly you have ALSA and sound.

---

### Post by orangep on 2007-05-06
Correction:
I was overlooking the fact that I had already earlier changed the mode of
all of the audio devices in the main /dev subdirectory.

Do this:
cd /dev
ls -l /dev/* | grep audio

And make sure that everything you see has permissions like:
crw-rw-rw-

---

