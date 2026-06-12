---
title: "Booting Difficulties"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by chunkeydelight on 2008-03-24
Hello,

  I'm kind of in need for a bit of help. Maybe a lot of help. I had just recently installed Ubuntu 7.10 Gutsy Gibbon and I am experiencing the same problems as the previous version, 7.04 Feisty Fawn. Whenever I boot into linux I can get as far as the splash screen, it loads about 2% and just sits there. I try to boot in recovery and it's an endless list of errors and such. I stumbled upon the fact that whenever I only have 2 hard drives hooked up to my computer at once, I can boot up w/ no problem. Now, I would love to set my computer up so that I can boot into either Windows or Ubuntu and have access to all 5 of my hard drives (the 2 OS drives and 3 storage, one of which is an external enclosure).

  I'm still new to linux, since I don't have time to mess around with it workin two jobs and all. I don't know what else to do. I've tried re-installing and other things but I just can't seem to get it to work. Are there maybe some boot options I can throw into Grub so it recognizes more than 2 drives at a time? Do I have to build a kernel so it works like a charm with my system? Whatever advice I could get I would greatly appreciate it. I just can't seem to get linux to work the right way for me, I don't know why, I just can't. I think I'll try Kubuntu, don't know if that's much different or if it will be the same result but I think it might be worth the try.

If anybody could help I would greatly appreciate it. On top of that.. I'd like to thank whoever helps out in advance.

---

### Post by Malta paul on 2008-03-24
Can you boot from the live CD?
If not but you can get to the menu screen, try the 'Safe Graphic' entry.
Make sure you BIOS recognizes all your HD drives, also sometimes you need to change to 'Legacy mode'
Post back your results as there are plenty of knowable guys on the forum to help.  
Have fun :)

---

### Post by chunkeydelight on 2008-03-25
> **Malta paul said:**
> Can you boot from the live CD?
If not but you can get to the menu screen, try the 'Safe Graphic' entry.
Make sure you BIOS recognizes all your HD drives, also sometimes you need to change to 'Legacy mode'
Post back your results as there are plenty of knowable guys on the forum to help.  
Have fun :)

Hey, Thanks for the suggestions. Unfortunately, I only have time to check any of my posts is when I'm at work, and even that's risky since my supervisor can walk in at any time. So as soon as I can I'll try those suggestions out. But there are a few things I can tell you from past experiances.

I am able to boot up with the live CD, But, I get the same problem as if I were booting from the installed system. And I know that all my HDDs are recognized in my Bios too. I haven't tryed booting in the 'Safe Graphics' mode though so as soon as I can I'll try and do that and post my results of that.

Now, I just have a question (or 2) about the 'Legacy Mode'. 1) How would I go about doing that? and 2) Would I be able to run Windows Vista off of that Incase I need to get in there? Because, I like to have a Windows OS that I know as backup incase something happens to my main OS. Unfortunately, I don't know enough about Linux to keep that as my main OS. But I'm sure I'll have more posts up since I am having other problems that I can't seem to figure out quite yet or with the amount of time I have between my 2 jobs.    But once again.. Thank you for the advice.

---

### Post by OffAxis on 2008-03-25
First off, look out for that USB hard drive. Depending on if you had it plugged in when you installed or if you had it unplugged when trying to boot, it can effect the sequencing of your drives (which in turn effects where GRUB looks for the boot files). USB flash drives can mess with it, too.

In case you need an easy GRUB salvage boot disk, try this:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Within the BIOS make sure the boot sequence looks to the ubuntu install first.

> I try to boot in recovery and it's an endless list of errors and such. 

Could you elaborate on the errors? There are a few boot options (check the liveCD 'Options' for a list) that  can disable some of the most problematic things.

Legacy mode? I'm not sure what that is. I've never heard of it reference to hard drive settings in the BIOS before.

---

### Post by Malta paul on 2008-03-26
Just for Info.
The normal BIOS setting is normally set to 'Native Mode'.  If a live CD or a HD fails to boot sometimes changing the BIOS to 'Legacy Mode' will fix it, the when the OS has then been installed you can usual revert back to the more efficient Native mode.
The name of settings very slightly with the BIOS make. But can usually be found at Integrated peripherals>On-Chip IDE Configuration>On-Chip ATA(S) Operate Mode. 
These settings have worked for me on a number of occasions.

---

### Post by _aXXe_ on 2008-03-26
I'm having a problem with the grub loader. It was apparently skipped when I installed 7.10 because I saw no option due to the screen being scrambled for several minutes. I'm using the LiveCD (Live session user) and want to know the best way to repair this glitch. I presume that a reinstall with the safe video option might work but want to get all the ducks in a row before I delve into what may be an arduous task. 

What would be the best way to handle this?

Thanks in advance.

---

### Post by _aXXe_ on 2008-04-01
Okay. My fault. I missed the part about using a live CD. Sorry, a little knowledge causes problems.

---

### Post by chunkeydelight on 2008-06-13
i know it's been a while and i didn't keep to my word of trying all the suggestions but i did figure out how i am able to boot into ubuntu. i found if i go into my bios and i change the hard drive controller from [Standard IDE] to [AHCI] i can boot into ubuntu. the down fall to this is i'm not able to boot into windows with it since i don't think i have the drivers installed for that. but that's a story for a different day.

i just want to thank the people who replyed with suggestions, you were the first ones to help me in all 10 posts i put up about this on different sites even. so thank you.

---

