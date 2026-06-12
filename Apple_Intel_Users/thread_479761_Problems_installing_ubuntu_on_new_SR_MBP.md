---
title: "Problems installing ubuntu on new SR MBP"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by GinKen on 2007-06-20
Greetings to this forum,
Have been having so much trouble getting Ubuntu up and running on new Santa Rosa MacBook Pro that the $600 Ubuntu friendly Dell laptops are looking very tempting, as (ppc)Ubuntu has been my OS of choice over a year.  But, as a web designer, I need to see how my work looks on different operating systems, so hope to stick this out, and, since this seems a friendly and helpful forum, thought I'd try posting here.  I followed various directions I found for installing Ubuntu, not knowing about this forum then, but none of the tutorials exactly suited to my situation.  Now, on booting my computer, refit let's me choose Linux, then I see text saying grub is loading, then the Ubuntu splash screen appears, and then, where the login screen should appear, it doesn't.  The screen is just black, no text, no nothing.  I don't know where I am, how to get out of there, or where to go from there.
I first installed rEFIt 0.10, then partitioned the 120G from MacOS command line using diskutil into a 45G partition for OS X, a 55 partition for Ubuntu, and the remainder saved for Windows when I get a hold of an installation CD, but is now JHFS+ format.  From then I used the alternate 7.0.4 installation CD.  On completion of installation, went to boot Ubuntu and nothing at all happened, so followed someone's advice and used gptsync in the  rEFIt EFI shell.  After this, Ubuntu booted up to where the login screen should appear but doesn,t as I've already described.
I know there have been other threads on triple booting on MacBook Pro, so hope you'll forgive me if I'm being repetitive, but I feel I could save time if my exact issue got addressed, and time I need.  I'm also completely willing to erase partition and start from scratch.  
Another thing I'd like to know is if I should install lilo, and if so, how.
Any help or pointing in the right direction will be much appreciated.

---

### Post by ivesjd on 2007-06-20
From what I've read, rEFIt only supports 4 partitions. The 200MB efi partition that must remain, then in your case, OS X, Ubuntu, and then Windows. It doesn't sound like your problems is having to many partitions though. Just a thought.

---

### Post by ronocdh on 2007-06-20
GinKen,

Sorry, I don't see the thread readily (it might have fallen to page 2 or 3 of the forum), but someone recently posted about the splash screen failure. The solution was to remove the splash screen from the booting, and then the user made it to the login screen. I'll edit this post with more detailed information later on if I find it.

---

### Post by GinKen on 2007-06-21
Ronocdh ,
Thanks for reply.  I look forward to your answer.  I noticed in your signature a link:
Failing to start X on a MacBook Pro (or other Radeon X series)
Do you think this could also be part of my problem?  If so, how would one enter the commands suggested at this link, as I cannot even get to login screen?  Is there a way to get to command line (terminal) before login?
Thanks
GinKen

---

### Post by ronocdh on 2007-06-21
> **GinKen said:**
> Ronocdh ,
Thanks for reply.  I look forward to your answer.  I noticed in your signature a link:
Failing to start X on a MacBook Pro (or other Radeon X series)
Do you think this could also be part of my problem?  If so, how would one enter the commands suggested at this link, as I cannot even get to login screen?  Is there a way to get to command line (terminal) before login?
Thanks
GinKen
Unfortunately that is not for you; the problem AIUI pertains only to the cards in the older MacBook Pros (ATI), not the newer ones (Nvidia), which you have. Let me comb around and see what I can come up with. I know I read a post here about it.

*Edit: [Found it!]("http://ubuntuforums.org/showthread.php?t=474144&highlight=splash+screen+xxx")*

---

### Post by GinKen on 2007-06-21
Yes, trouble1313's booting issue sounds like it could be mine.  He recommends turning splash off in grub.  Would you know how I can get into grub to do this???  All I've got is a blank screen.  
Thanks

---

### Post by ronocdh on 2007-06-21
> **GinKen said:**
> Yes, trouble1313's booting issue sounds like it could be mine.  He recommends turning splash off in grub.  Would you know how I can get into grub to do this???  All I've got is a blank screen.  
Thanks
You don't even seen the GRUB screen? Is this after the rEFIt screen? Obviously trouble1313 got that far, and it's strange that you didn't. Are you sure Ubuntu installed correctly? (You're using Feisty, right?)

---

### Post by GinKen on 2007-06-22
Using 7.0.4 alternate install.  Did I install it correctly?  That's what I'm trying to find out.  Does grub screen come up?  Not sure what this means.  After choosing to boot Linux in rEFIt, get a text message on the screen, "loading grub 2"  At this point have option to press esc key, when a screen appears like so:

Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic(recovery mode)
Ubuntu, membest 86+

From here I can press 'e' to edit or 'c' for command line  Sorry for my ignorance, but since I don't know what I'm doing, I haven't tried anything with it.  But this is the only option I have to change anything, so if I can get rid of the splash, it would have to be here, but not sure how to go about it.
Thanks

---

### Post by GinKen on 2007-06-22
Oh, just one more thing forgot to mention, if I choose recovery mode from screen, everything seems to mount ok, and leaves me at root command line, but any idea what I can do from here?
Mahalo

---

### Post by trouble1313 on 2007-06-22
Ok you're good then...Go into recovery mode and let it drop you to the root prompt. Then go into /boot/grub end edit menu.lst.  There's lots of stuff in there (most of which is commented out) so go and look for the 'Ubuntu, kernel 2.6.20-15-generic' section. You'll see a line that says:

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ea173bb5-b5d9-485b-9ce
4-c55b466d2651 ro quiet splash

(or something like this since your UUID= will be a little different )

Go ahead and delete 'quiet' and 'splash'  from that line and save the file.

While you're still in recovery mode, go and edit /etc/X11/xorg.conf

Look for the line that says '  Driver        "nvidia"  

and change it to  Driver     "vesa"    

save the file and type reboot
The system should reboot and bring up into Gnome

You could use that 'e' option at the grub menu but I figure this way gets it done in one shot.

-Trouble

---

### Post by ronocdh on 2007-06-22
> **trouble1313 said:**
> Ok you're good then...Go into recovery mode and let it drop you to the root prompt. Then go into /boot/grub end edit menu.lst.  There's lots of stuff in there (most of which is commented out) so go and look for the 'Ubuntu, kernel 2.6.20-15-generic' section. You'll see a line that says:

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ea173bb5-b5d9-485b-9ce
4-c55b466d2651 ro quiet splash

(or something like this since your UUID= will be a little different )

Go ahead and delete 'quiet' and 'splash'  from that line and save the file.

While you're still in recovery mode, go and edit /etc/X11/xorg.conf

Look for the line that says '  Driver        "nvidia"  

and change it to  Driver     "vesa"    

save the file and type reboot
The system should reboot and bring up into Gnome

You could use that 'e' option at the grub menu but I figure this way gets it done in one shot.

-Trouble
This is an extremely helpful post and should be a sticky!

---

### Post by GinKen on 2007-06-23
Trouble,
Edited menu.lst as you suggested.  As for /etc/X11/xorg.conf file, could not fine the line 
Driver "nvidia"  Did find line Driver "nv"  
Should I change "nv" to "vesa" ?
Thanks
GinKen

---

### Post by ronocdh on 2007-06-23
> **GinKen said:**
> Trouble,
Edited menu.lst as you suggested.  As for /etc/X11/xorg.conf file, could not fine the line 
Driver "nvidia"  Did find line Driver "nv"  
Should I change "nv" to "vesa" ?
Thanks
GinKen
Warning: I do not have a Santa Rosa MBP. That said, I think you are safe to change the "nv" driver to "vesa." Another way to change the driver would be:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by GinKen on 2007-06-23
Just for the record, changing the nv to vesa did work, though as someone who likes to know the why of things as well as the how, I wonder why nv wasn't working.
But I want to thank everyone.  I can at least login, though I have the feeling I'm not out of the woods yet.
GinKen

---

### Post by Gen2ly on 2007-06-23
Probably won't be a resolution to the nvidia issue for a little bit.  I was reading somewhere about this too.   New cards usually add certain abilities and it's conflicting with the driver.  Ive never had an nvidia card but I haven't heard very many angry with their support, even in linux.

---

### Post by trouble1313 on 2007-06-23
Yeah sorry guys, it'll indeed be 'nv' and not 'nvidia' if you haven't gone and installed the (broken) Nvidia sourced non GPL drivers! Neither 'nv' nor 'nvidia' actually worked right so the result is the same...we're all stuck with the 'vesa' driver.....This isn't terrible but it isn't good either. No Beryl, 3d, accelleration etc.


-Trouble

---

### Post by ronocdh on 2007-06-24
> **trouble1313 said:**
> Yeah sorry guys, it'll indeed be 'nv' and not 'nvidia' if you haven't gone and installed the (broken) Nvidia sourced non GPL drivers! Neither 'nv' nor 'nvidia' actually worked right so the result is the same...we're all stuck with the 'vesa' driver.....This isn't terrible but it isn't good either. No Beryl, 3d, accelleration etc.


-Trouble
Well, boo. This is precisely one of the reasons I was clapping my hands when Apple switched. Oh well, I don't think it'll be too long before there's a binary blob for the new chipset, at least.

---

