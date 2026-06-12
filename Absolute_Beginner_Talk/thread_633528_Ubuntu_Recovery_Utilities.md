---
title: "Ubuntu Recovery Utilities"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-12-06
I monitor Ubuntu Forums on a regular basis. It is truly amazing the amount of stuff one can learn or do. The people here are just fantastic in trying to help folks. 

The one theme that always seems to be asked is 'how to I fix ____". In many cases, responses are 'Well what are your computer components. Another issue seems to involve the ever sensitive GRUB configuration.

It would seem to me that logic dictates that a single comprehensive 'analysis/fix up' program would be beneficial. Whether this comes on the live CD or otherwise as a separate iso matters not but this program should include:

1. GRUB analysis and automatic fix / recovery;
2. Video Analysis and auto driver dl, install and fix;
3. Audio reset, analysis, driver dl & install and fix;
4. Network analysis, auto install after base answers to a few question, plus, auto fixes.
5. HD analysis, auto fix, remount, or a better way to automount other HDs.

Now I know there are a whole bunch of commands, individual scripts, some other programs like SuperGrub that try to do this. However, there does not seem to be comprehensive program to do all.

While I am a 'user' my intimate knowledge of Linux/Unix is limited and certainly judging by the number of questions on the forums, this seems to apply to a whole bunch of people. 

I think also Ubuntu should adopt a new approach to backup/restore for critical and user files; make such mandatory. Further the if the main startup fails for some reason, an option should be provided to auto restore last critical o/s files, so at least one can start (barring hw failures).

What do you think?

---

### Post by ajmorris on 2007-12-06
Hmm, i think you're onto something. Would make certain parts of the os more user friendly or the new linux user. Perhaps send a pm to Ubuntu Geek? See what he thinks.

---

### Post by sdgreen on 2007-12-07
Good suggestion

---

### Post by ebeard on 2007-12-07
Being a newby and having reinstalled Ubuntu more times than I have fingers over the last two months, I enthusiastically support something like this. If I understand you are talking about a one source disk for common fixes. 

I have installed and killed Ubunutu trying to get wireless, graphics, etc working. I have no idea how to undo, and the instructions I find in this forum and other places seldom have back out instructions. So, I wind up wiping the partition and reinstalling (I only have luck  installing into unallocated space). 

I really like the idea of open source, but I keep saying it is not worth the aggravation, then come back for more. Almost the last straw was another attempt at Gutsy with its non-functional wireless woes (worked in Edgy, but I can't get anything but Vesa graphics in Edgy). I made an image of my Edgy Linux partitions and bootable sectors with maxblast5. So, I thought I would just go back when Gutsy went haywire (stopped loading). Restoring the image of Edgy (including boot sectors) gave the infamous grub error 17. My brother had also  screwed up his windows trying to fix an error 17, but thank goodness for testdisk. I have a supposed live rescue disk from another source with various utilities on it. It boots up to a command line with cryptic instructions, but I have never been able to get anything to run on it. It just says command not found and stays at the command line. 

All these words to offer these suggestions as a novice. Make it a live rescue disk that comes as an ISO image. Include an easy to use interface image utility (partimage?) for restoration from hosed Ubuntu "learning experiences". Include testdisk if legal to do so. 

Thanks for considering this.

---

### Post by Joeb454 on 2007-12-07
As for the last part about being able to boot even if you broke it...I'm not sure whether that's possible now, if you notice when the grub menu comes up, it says something like:

```
Ubuntu 7.10
Ubuntu 7.10 (Recovery Mode)
```

---

### Post by sdgreen on 2007-12-08
Yes, but Recovery mode for a noobie is like being transporto another world. Seems to me that if there is a startup error (which the system must know) then the o/o should immediately go to a 'fix' routine. The 'fix' routine could be a separate block on the hdd, or a simple message to insert 'fix' disk. 

The system should then identify the failures and suggest cmds to run repairs. Of all the issues, it seems that the GRUB routines are the most difficult followed by video then networking. 

There should be no reason why the system can't do its own analysis of failures and do a 'fix' on the fly. 

But then again, I might be asking too much automagic stuff.

---

