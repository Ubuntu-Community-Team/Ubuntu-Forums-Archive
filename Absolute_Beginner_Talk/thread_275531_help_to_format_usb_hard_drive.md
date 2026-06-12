---
title: "help to format usb hard drive"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-11
First of all i would like to thank everyone for the great amout of help that i have received in this forum. not all forums are so nice. Alot of them are very mean to new people and the anwser for everything is do a search....thats what kept me from linux but now that i got everything working i am very happy...thank you all that have helped me....


so my question is i have a 250 gig usb hard drive that i need to format there are a lot of choices to format ext2, ext3,vfat ect....all i will be using the drive for is music and pictures i want to be able to bring it with me so it needs to work in linux and windows what option should i use? and why? 

thank you very much

pre

---

### Post by soutSA on 2006-10-11
I am not totally sure on this one, but would say to try and format it to fat32. This will make it accessible by windows and then you can use the following thread to mount a fat32 drive to ubuntu:

[http://www.ubuntuforums.org/showthread.php?t=274924&highlight=mounting+fat32](http://www.ubuntuforums.org/showthread.php?t=274924&highlight=mounting+fat32)

just my 2 pence:-k

---

### Post by pregoeater on 2006-10-11
why would i want to mount the drive its usb as soon as i turn the drive on it comes up? should i mount it? and why?

thanks
pre

---

### Post by nik on 2006-10-11
Yes, use fat32. Just be aware that it doesn't support permissions like ext3 does. shouldn't matter for music and pictures.

Ubuntu (or gnome maybe) has some automounting features, so if it comes up and you can access it it's nothing to worry about :)

---

### Post by annda on 2006-10-11
i would be more concerned about the limitations of fat, namely i've read you can't format 250 gig for fat. sorry if i'm causing confusion, but i'm fairly sure you can't do that with windows, and even with other (linux) partition tools there is rumored to be a 137 gig limit (not that tragic, you can make two partitions). or does it affect only older architectures?

it would be great if someone could post their experience with large fat32 drives, as i'm still working hard on archiving stuff from my 200GB ntfs to finally reformat it, so i can't offer anything first-hand.

---

### Post by Quintin Riis on 2006-10-11
You want to use a twenty year old filesystem?

Use ext3, and the Windows driver for it so you can get at things on Windows.

If you are sure you will *never* need to have a 4GB file, then you can try fat... don't say you weren't warned though.

This depends on having admin rights to install the ext3 driver on the windows machines too.  If you don't have this you may have to settle for FAT or make 2 partitions on the disk.

```
<plug in drive> 
% dmesg | tail 
% sudo cfdisk /dev/xxx
<delete paritions, make new ones to your liking>
% mke2fs -j /dev/xxx
```

---

### Post by mozetti on 2006-10-11
@Quintiin -- it doesn't make sense to have an ext2/3 filesystem if you might be using the portable drive amongst multiple windows machines. You don't want to install the driver on your friends' computers, and you can't install the driver on library or internet cafe computers.

@ original poster -- If you want to format it as FAT32, type this in the terminal:
```
mkdosfs /dev/xxx
```

---

### Post by Quintin Riis on 2006-10-11
> **mozetti said:**
> @Quintiin -- it doesn't make sense to have an ext2/3 filesystem if you might be using the portable drive amongst multiple windows machines. You don't want to install the driver on your friends' computers, and you can't install the driver on library or internet cafe computers.
I stated that in my post, Captain Obvious.  :)

---

### Post by pregoeater on 2006-10-11
im very confused now....so if i use FAT32 i can use in both windows xp and linux without prblems but if i use EXT3 i can use in both but need a DRIVER? how do i get this driver. and what is VFAT is that FAT32.



thanks 
pre

---

### Post by Quintin Riis on 2006-10-11
> **pregoeater said:**
> im very confused now....so if i use FAT32 i can use in both windows xp and linux without prblems but if i use EXT3 i can use in both but need a DRIVER? how do i get this driver. and what is VFAT is that FAT32.
Google is your friend.  Please search the web before asking questions.

[Google]("http://www.google.com/search?q=ext3+driver&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official")

Your statement is mostly correct, yes.  See the above link for details in regards to ext3 with Windows NT.

The best solution depends on your needs.  I would use ext3.  The best solution for me may not be the best solution for you.  FAT is really crap though, on many levels.  If you are positive you won't need support for large files or partitions though, go for it.

---

### Post by pregoeater on 2006-10-11
WOW you mean i can search for stuff on google? thank you soo much WOW....im going to try that RIGHT NOW....because the first 2hours i spent trying to search was not good enough... 



pre

---

### Post by pregoeater on 2006-10-11
or better yet...i will goto every thread on this forum and tell them to do a google searh  and maybe we just wont need forum any more....

---

### Post by annda on 2006-10-11
yes, ext3 is great and all, but if you want to hook up you usb hdd to a friend's computer (with win os) to show them some photos, they will have to install this driver first to see your files:
[http://fs-driver.org/](http://fs-driver.org/)

not very convenient. and not everyone is allowed to install anything on their computers.

if you really want to carry your hdd around, use FAT (yes, we are all talking about MS FAT32 using different names). otherwise try ext3 - it is better and for one gives you more control over your files.

---

### Post by ThrobbingBrain66 on 2006-10-11
if i were you, i would use fat32 (aka vfat).  using ext3 would cause the need for another driver in windows.  better to keep things simple.

good luck!

---

### Post by pregoeater on 2006-10-11
great so i think what i am going to do is format using vfat which is fat32 ...installing a driver on other computer would be a problem. however when you say ext3 is better then fat because it gives you more control of your files what do you mean.  say i have pictures on the drive i can copy, edit, or move. if i had more control what else could i do?


thanks
pre

---

### Post by annda on 2006-10-11
and please pre, don't be put off by people who forget they are in the absolute beginner forum.

describe your problem as best as you can, follow the advice and post the results. that way you're on the safe side and any sarcastic comments are just beside the point.

ps. it's much more difficult now to search the forums than e.g. 6 months ago when there were fewer posts = easier to find answers.

---

### Post by ThrobbingBrain66 on 2006-10-11
> great so i think what i am going to do is format using vfat which is fat32 ...installing a driver on other computer would be a problem. however when you say ext3 is better then fat because it gives you more control of your files what do you mean. say i have pictures on the drive i can copy, edit, or move. if i had more control what else could i do?

others may know more than i, but ext3 virtually eliminates the need for defragmentation.  certainly i am no file system expert, so that may have no effect on a drive where only music and documents (as opposed to an OS) are kept, but it's nice to know.

---

### Post by annda on 2006-10-11
aside from filesize limits (fat can't handle e.g. huge movie files) the control issue:
for example, you could decide which files can be viewed only, and which may be modified by people other than you.

in my experience, for everyday use you can skip that for the sake of convenience - if you know who is using your files, you dont need protection by elaborate permission assignments.

when i share my disks, i know who is doing what to them, i don't do that over a network - and this is where you should be concerned about security of your data.

---

### Post by Quintin Riis on 2006-10-11
> **pregoeater said:**
> WOW you mean i can search for stuff on google? thank you soo much WOW....im going to try that RIGHT NOW....because the first 2hours i spent trying to search was not good enough... 
Don't be an asshat.  I'm not going to help someone who refuses to help themselves.  If you want hand-holding you can check into commercial support options.  Searching google and this forum provides answers much faster than whining randomly, and prevents the forum from being filled with redundant content.

Real life example:  I was wondering why Ubuntu overwrites my /etc/resolv.conf on each reboot.  Rather than post a question on the forum, I first entered /etc/resolv.conf in the search box, and my issue was resolved in about two minutes.

The first result for 'ext3 driver' on google is the Windows driver.  Are you honestly going to tell with two hours of searching you could not locate this?  Maybe you should head to your local Apple Store.. :-D

---

### Post by Phantom784 on 2006-10-11
if your'e going to use it on windows but still want to use ext3, you can create a little fat partition just big enough to hold the ext3 driver.  then, when you plug it in on windows, you can just install the driver, and not have to find it online.

---

### Post by ThrobbingBrain66 on 2006-10-11
> **Quintin Riis said:**
> Don't be an asshat.  I'm not going to help someone who refuses to help themselves.  If you want hand-holding you can check into commercial support options.  Searching google and this forum provides answers much faster than whining randomly, and prevents the forum from being filled with redundant content.

Real life example:  I was wondering why Ubuntu overwrites my /etc/resolv.conf on each reboot.  Rather than post a question on the forum, I first entered /etc/resolv.conf in the search box, and my issue was resolved in about two minutes.

The first result for 'ext3 driver' on google is the Windows driver.  Are you honestly going to tell with two hours of searching you could not locate this?  Maybe you should head to your local Apple Store.. :-D

there were still better ways you could have worded your answer.  it came off as very condescending and inappropriate.

---

### Post by pregoeater on 2006-10-11
THAT IS A FANTASIC IDEA....thank you that will work great....


thanks 
pre

---

### Post by Quintin Riis on 2006-10-11
> **ThrobbingBrain66 said:**
> there were still better ways you could have worded your answer.  it came off as very condescending and inappropriate.
"Google is your friend. Please search the web before asking questions." is 'inappropriate' and 'condescending'?]:-| 

Right. ;) 

Original Poster:  Please remember to post your final decision and resolution to your problem.

---

### Post by ThrobbingBrain66 on 2006-10-11
> **Quintin Riis said:**
> "Google is your friend. Please search the web before asking questions." is 'inappropriate' and 'condescending'?]:-| 

Right. ;) 

Original Poster:  Please remember to post your final decision and resolution to your problem.

no, the part where you called him as asshat was.

---

### Post by Quintin Riis on 2006-10-11
> **ThrobbingBrain66 said:**
> no, the part where you called him as asshat was.He was being an asshat.

And now you are as well.  Please cease and desist.

---

### Post by handy on 2006-10-13
troll

---

### Post by deeptingler on 2006-10-14
> **Phantom784 said:**
> if your'e going to use it on windows but still want to use ext3, you can create a little fat partition just big enough to hold the ext3 driver.  then, when you plug it in on windows, you can just install the driver, and not have to find it online.

This is spot on info pregoeater - I do this myself with a 320gb external usb drive with a 1 gig partition in fat32 format ready for when I take it to my mates.  on that 1 gig partition I have the windows driver so that he can use my drive and then I just bring it back to Linux as normal - good info from Annda but Quintin could have been a little more polite, soz Quintin I'm with Annda on this one! :-#

---

### Post by pregoeater on 2006-10-14
thanks for the info...thats how i will do it.



thanks pre

---

### Post by Quintin Riis on 2006-10-14
> **deeptingler said:**
> This is spot on info pregoeater - I do this myself with a 320gb external usb drive with a 1 gig partition in fat32 format ready for when I take it to my mates.  on that 1 gig partition I have the windows driver so that he can use my drive and then I just bring it back to Linux as normal - good info from Annda but Quintin could have been a little more polite, soz Quintin I'm with Annda on this one! :-#I was plenty 'polite' until pre turned into a dumbass.  So, really, piss off.  :)

---

### Post by deeptingler on 2006-10-15
Nice, Quintin.... please remember that there may be younger people reading these forums.

I understand the point you were trying to make in order that pre may have looked harder but it was the way you had "come across" on your reply.  Sometimes we all need a little guidance rather than being shot down in flames.

Still, he was given the information in the end and I assume he has gone off to try this out now.

---

