---
title: "broke laptop after compiling alsa"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-03-01
Hi all, 

I can't believe the day I am having. to cut a long story short, I have just finished finally getting the wireless on my laptop to work after the update to kernel -11, and as I was revelling in the fact that it was working, I noticed a blog that suggested compiling the latest version of alsa to fix the headphone issue that my laptop (compaq presario v3118AU) has - amongst quite a few other basic functionality that doesnt work.

So I searched on the forums for how to compile alsa, and found a post which said to download and extract alsa, then run ./configure, make, sudo make install

which I did, and then restarted. 

all looked good, there was no sound which was i believe normal as it said in the terminal that it starts muted by default. I put in username and password, pressed enter, the screen went as it normally does before loading naughtilus etc, and then nothing. 

it just hangs. I am desperate to get this fixed, as I have already lost (now) 9 hours of today trying to get my laptop useable again, and as it is 11.30pm and i have been up since 6.30am, I really would like to get this sorted as soon as possible. 

I am still a newbie to the world of command line, i can start the laptop in safe mode but that is all command line and i dont know what to type to get things back to how they were.

I eagerly await some advice and suggestions, 

Thanks

Patrick

---

### Post by ozPATT on 2007-03-01
anyone? if i could just get back into the desktop i would be a happy man. i dont care if i have to go without sound for a buit, that would be better than going without a computer...

---

### Post by astrolabio on 2007-03-01
What do you mean by "broke"?
You mean that you can't even put a live disk and make the computer boot?

Beside what sound card you have?

---

### Post by ozPATT on 2007-03-01
Hi, 

when i say broke, i mean i cant log in. 

I can log in to recovery mode, and see all my files and execute commands, but i dont know enough about command line stuff to know how to revert my alsa driver back to what it was so that i can log into the GUI

When i try to log into the gui. it takes me to the login screen with no problems. It asks for my user and password, then once i have provided that, it just hangs. It isnt freezing as such, as I can still press ctrl+backspce to reload the login bit and try again, but then it hangs again when i try to log in. 

I just want to ba able to log in to the gui again, i dont mind if i have no sound for a while...

Thanks

Patrick

---

### Post by ozPATT on 2007-03-01
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

I didnt download the lib and utils for 1.0.13

Could this be why it isnt working? I'm really starting to stress now... nearly work time :s

---

### Post by annda on 2007-03-01
it looks like either you xorg.conf is messed up or you don't have enough space on your disk (both those issues will get to the log in screen but will throw you off).

this probably has nothing to do with sound. have you tried to modify xorg.conf manually? changed graphics drivers recently? use ati/nvidia drivers and updated the kernel recently (by update-manager)?

if not, try to free some space on your disk in recovery mode. a good guide to basic commands is here|:
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by ozPATT on 2007-03-01
hi there, it was to do with the sound... from looking at the link i posted above, it seemed like i was supposed to have and compile the driver, lin and utils. I had only compiled the driver for 1.0.13

So, i searched into the depths of my brain and remembered that i could download stuff using wget. So I downloaded 1.0.14rc1 as the link above suggests, then followed the steps in the link i posted above. rebooted, and IT WORKS!!! i am so happy/relieved/exhausted

Thanks anyway. Headphones work now too which is cool. Still no mic, but not sure i am braveenough to tackle that though..

Thanks again,

Patrick

---

### Post by Maestro23 on 2007-03-01
> **ozPATT said:**
> hi there, it was to do with the sound... from looking at the link i posted above, it seemed like i was supposed to have and compile the driver, lin and utils. I had only compiled the driver for 1.0.13

So, i searched into the depths of my brain and remembered that i could download stuff using wget. So I downloaded 1.0.14rc1 as the link above suggests, then followed the steps in the link i posted above. rebooted, and IT WORKS!!! i am so happy/relieved/exhausted

Thanks anyway. Headphones work now too which is cool. Still no mic, but not sure i am braveenough to tackle that though..

Thanks again,

Patrick

Good deal man. Glad you got it figured out.  You can go back and edit your first post to "Resolved".

---

