---
title: "Questions, Questions..."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by File13 on 2007-07-26
Ok well im new to Ubuntu and im liking it so far, i know its not fully noob proof yet but im working my way around installing things and using terminal here and there. I do however have a few questions...I was having the issue of when i plugged in my headphones the audio still came out of my laptop speakers, rather than just my headphones. I followed the comprehensive sound guide thread and that didnt fix anything, now as a matter of fact when i play audio its all crackly and popping. So my question there is how would i go about fixing the popping thing and how would i get my headphone issue to work. One big thing on my mind however is that since i have sometimes had to go through some things more than once to install properly i get the feeling that Ubuntu is screwed up somehow behind the scenes. Being that you do indeed have to use the terminal to install and do things i just think for some odd reason that at any time something could go wrong because of perhaps of something i did wrong along the lines, that may sound weird but i dunno. Anyways thanks in advance for any help, im looking forward to becoming a full time ubuntu user.

---

### Post by mrgnash on 2007-07-26
If you could perhaps be more specific with regard to 'installing things'; did you install these things from the Ubuntu repositories, or did you compile them, or did you install them from a deb you downloaded from the internet? Most of the time, installation errors can be attributed to unsatisfied dependencies (a missing library or some much), and apt can usually resolved these by simply downloading the necessary packages. Where you will most frequently run into errors of this sort is during a manual compile from source, where the unmet dependencies aren't automatically 'fetched' for you, and you have to instead track down the packages yourself or run a build-dep. 

That said, if you are installing things, so to speak, 'willy nilly,' then you can indeed run into problems. Third party repositories can often replace files during the installation of whatever program you're trying to install, that other programs depend on, or that may conflict with future upgrades -- especially when upgrading to a new iteration of the distribution itself. Now as long as you have your personal data on a separate /home partition, then nothing overly calamitous is likely to result -- this is what I do, and it's a good thing to because I tend to be be quite adventurous in installing all the latest bleeding edge stuff, and while I haven't had any show-stoppers, I usually need to a 'fresh install' with each new release. Otherwise, I suggest that you always err on the side of caution and confine yourself to the official Ubuntu repositories as much as possible.

---

### Post by paradoc on 2007-07-26
First thoughts--
Install using Applications-->Add/Remove. This GUI method is far easier than using terminal, until you become more proficient in sudo'ing etc.

Are your headphones the USB variety?........if so look at Preferences-->sound for more tweak-options, but If they are the simple plug-in type, do they work OK in Windows?

(have to go now, but I'll watch your progress in this thread!)

---

### Post by File13 on 2007-07-26
so you dont just update via ubuntu when a new version comes out, you just reinstall the new version? how do you save all your data? As far as the being more specific im not going and changing repositories to my knowledge, most of the tutorials i follow are doing the default things, just installing needed packages and deleting others, etc.

---

### Post by File13 on 2007-07-26
my headphones are normal headphones, not USB. and they work fine on my windows partition yes, its only on Ubuntu that when i plug them in sound still comes through my laptop speakers.

---

### Post by sloggerkhan on 2007-07-26
I find that most of the important audio options are hidden under the 'open volume controll' option when right clicking on the volume control panel applet and not in the sound control panel. Don't know if that will help any.

---

### Post by File13 on 2007-07-26
Ive seen that before, heres what i have for the options. 

Under the play back tab i have listed,
Master
PCM
EXT Mic
INT Mic

Then under the switches tab i have,
Line-in
IEC958
Int-Mic

---

### Post by mrgnash on 2007-07-26
> **File13 said:**
> so you dont just update via ubuntu when a new version comes out, you just reinstall the new version? how do you save all your data? As far as the being more specific im not going and changing repositories to my knowledge, most of the tutorials i follow are doing the default things, just installing needed packages and deleting others, etc.

Some people do, but they tend to be the ones who have not messed with their install too much by installing things from source, or restricted drivers, etc. etc. As for how you keep all your data in the event of a fresh install, I already alluded to that when I mentioned the creation of a separate /home partition. Doing this at install time, allows you to format the root or / partition (where the nuts and bots of the operating system as such are stored) while leaving your personal data (stored in /home) intact.

---

### Post by File13 on 2007-07-26
bump

---

### Post by File13 on 2007-07-26
bump

---

