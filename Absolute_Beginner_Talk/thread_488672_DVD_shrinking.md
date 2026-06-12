---
title: "DVD shrinking"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-06-30
I recently backed up a DVD onto my computer as an ISO. What I first did was copy the whole DVD to my hard drive as an exact copy with K3B then i realized that it would be way to big to keep. Then I used K9copy to make the full sized ISO into an ISO that would fit onto a 4.7GB DVD. It worked great and i couldnt even tell the difference from the original and the 4.7GB ISO but I have a few questions about the whole process.

1. Is there any way i could do practically the same thing, but put less stress on my processor? during the second step of shrinking the ISO, my Pentium D was kicked up to 70% - 90% and I'm not quite comfortable with that. I would sacrifice the speed for a less processor hogging procedure.

2. I kept all the original content except for the foreign languages and my 4.7GB backup looks perfect! The program I used on windows did essentially the same thing, except it only copied the main movie, and the quality was degraded. So my question is, How the heck did this work so... perfectly?

Any help would be great :-)

---

### Post by blastus on 2007-06-30
[quote=Bohlio]1. Is there any way i could do practically the same thing, but put less stress on my processor? during the second step of shrinking the ISO, my Pentium D was kicked up to 70% - 90% and I'm not quite comfortable with that. I would sacrifice the speed for a less processor hogging procedure.[/quote]

You could always change the priority of the running process so that it doesn't hog the CPU. Go into System->Administration->System Monitor and right-click on the process and change its priority. Alternatively you can use the ps and renice commands to change the priority of a process.

[quote=Bohlio]2. I kept all the original content except for the foreign languages and my 4.7GB backup looks perfect! The program I used on windows did essentially the same thing, except it only copied the main movie, and the quality was degraded. So my question is, How the heck did this work so... perfectly?[/quote]

k9copy is good, but it doesn't remove all copy protection schemes. You can notice a difference in quality if you compare the original with the shrunk version. I haven't noticed any difference in quality between DVD Shrink on Windows and K9Copy. I'm not a big fan of shrinking as it takes too long and it reduces quality. I just decrypt with DVDFAB Decrypter (unfortunately Windows is required), boot back into Linux and create the image with mkisofs...

```
mkisofs -dvd-video -volid VOLUME_LABEL -o output.iso foldername/
```

...and then burn on double-layer if it's a double layer DVD.

---

### Post by p_quarles on 2007-06-30
I'm pretty certain that DVDShrink, K9copy, and mkisofs all work on the same basic principle. There's really no way to copy an encrypted DVD without shrinking it.

In any case, here's a guide to getting DVDDecrypter and DVDShrink working with Wine:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by blastus on 2007-07-01
> **p_quarles said:**
> I'm pretty certain that DVDShrink, K9copy, and mkisofs all work on the same basic principle. There's really no way to copy an encrypted DVD without shrinking it.

Whether a DVD is shrunk or not has nothing to do with whether it can be copied. Any DVD can be copied once it has been decrypted. If you can copy a particular encrypted DVD without decrypting it you are just lucky.

---

### Post by lisati on 2007-07-01
> **p_quarles said:**
> I'm pretty certain that DVDShrink, K9copy, and mkisofs all work on the same basic principle. There's really no way to copy an encrypted DVD without shrinking it.

In any case, here's a guide to getting DVDDecrypter and DVDShrink working with Wine:
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

Surely the need to shrink depends on whether the source disk is a DVD-9 or DVD-5, regardless of whether there's encryption?

---

### Post by p_quarles on 2007-07-01
Sorry, I guess my last post was very unclear. What I was trying to say was that you aren't likely to get many commercially-available DVDs onto a DVD5 without using a shrinking program. There, much clearer, and it didn't hurt a bit ;-)

And that, of course, has nothing to do with encryption.

Of course, if you can afford dual-layer disks, that's great. But a stack of 50 DVD-Rs here costs US$20. Shrinking is definitely the budget option.

---

### Post by orb9220 on 2007-07-01
Yes and I use Dvdshrink and DVDecrypter thru wine which works great.  [http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

I can have it either create a folder with the video_ts folder or as an iso which I can then just right click iso in Nautilus and write iso to disc.

---

### Post by Bohlio on 2007-07-01
> **blastus said:**
> 
k9copy is good, but it doesn't remove all copy protection schemes.

By this do you mean it will refuse to copy some because it cant, or do you mean it will copy it but keep it encrypted? And thanks for the tip on setting priorities. 

Yah, Shrinking is definately the budget option :-P dual layer DVD's are expensive, and I'd have to get a drive that could burn them :-P

But can anyone explain how the quality is still so good? I started with a 7.5GB exact copy of the disk, then shrunk it using K9 to be about 4.3 GB. All the content is still there (except for foreign languages) and I keep trying to compare the two and i cant really tell the difference. Ive inspected still frames, looked for differences in dark and explosive scenes, and i cant tell which is the original and which is the copy. I have a good monitor and 1024x768 so its not like Im using a crappy monitor where it wouldn't matter how good the content is. Does the program encode it more efficiently without encryption? Its a little over half the original size and I'm stunned at how good the quality turned out vs. using AoA DVD copy in windows...
Thanks,
Bohlio

Oh, And what is the biggest size (in MB) that can fit on a DVD. I know they say 4.7 GB but isnt it smaller then that when it comes to putting data on the drive? For K9copy, The DVD ISO size is set to 4400MB, can i go higher than that and still fit it on a dvd?

---

### Post by orb9220 on 2007-07-01
Actually it is 4.4 or 4.38 gb for single layer dvd's. And in shrink I custom set it from 4464mb to 4455mb so it won't bleed to the very last edge of dvd's which is usually the first area that goes bad or has problems with reading later down the time line.

I found for movies the best in mainstream stores is Verbatim 16x DVD+R with manufacture ID of MCC 004 they last alot longer. Also +R allows me to set booktype to DVD-ROM which fools the tabletop player into thinking it is a dual-layer bonafide Movie Disc which is only a issue with a few players.

I have gone back to copied movies I had on Office Depot,Memorex,Maxell's etc... And they had sprouted crc error weeds within a few month's.

You will notice the compression on HD type tv displays the bigger they are the more you will notice it. Not so much so on 21" or less.

---

### Post by blastus on 2007-07-01
[quote=Bohlio]By this do you mean it will refuse to copy some because it cant, or do you mean it will copy it but keep it encrypted? And thanks for the tip on setting priorities.[/quote]

k9copy attempts to decrypt DVDs (it has to be decrypted to be shrunk) but does not attempt to remove copy protection. k9copy will not be able to copy many DVDs because of copy protection. On the other hand, DVDFAB Decrypter removes all copy protection as it decrypts DVDs. Encryption is just one form of copy protection but the term is commonly used to mean copy protection in general.

Most copy protection involves corrupted sectors on the disc and a corrupted DVD video structure/stream in such a way that the movie can still be played in a standard player, but not copied from the disc. Some copy protection schemes, like Macrovision ACP, are embedded into the DVD video structure/stream but don't actually prevent pure digital copies from being made. k9copy will be able to copy those DVDs, but the copied disc will have that copy protection on it.

---

### Post by p_quarles on 2007-07-01
> **Bohlio said:**
> But can anyone explain how the quality is still so good? I started with a 7.5GB exact copy of the disk, then shrunk it using K9 to be about 4.3 GB. All the content is still there (except for foreign languages) and I keep trying to compare the two and i cant really tell the difference. Ive inspected still frames, looked for differences in dark and explosive scenes, and i cant tell which is the original and which is the copy.

A friend of mine (he's a film scholar, though, not a techie) explained to me that a lot of the data on a commercial DVD is junk, so most of them can be shrunk without losing much quality. Of course, it depends on how smart the shrinking software is. 

I have no idea how true this is, but it would make sense as a kind of copy protection measure.

---

### Post by Bohlio on 2007-07-01
> **blastus said:**
> k9copy attempts to decrypt DVDs (it has to be decrypted to be shrunk) but does not attempt to remove copy protection. k9copy will not be able to copy many DVDs because of copy protection...
...Some copy protection schemes, like Macrovision ACP, are embedded into the DVD video structure/stream but don't actually prevent pure digital copies from being made. k9copy will be able to copy those DVDs, but the copied disc will have that copy protection on it.


Ok so help me understand this a little more :-P
K9copy does not remove copy protection at all
K9copy will fail to copy DVD's with certain types of copy protection
K9copy may copy the DVD, but also some types of copy protection with it?
Lastly, If i copied the DVD, and can play it from an ISO on my computer, that means I'm good to go as far as playing it on a regular DVD player goes, correct?

Thank you all for your help,

-Bohlio

---

### Post by blastus on 2007-07-01
> **Bohlio said:**
> Ok so help me understand this a little more :-P

K9copy does not remove copy protection at all - I don't believe it does and if it does it doesn't do a good job

K9copy will fail to copy DVD's with certain types of copy protection - yes

K9copy may copy the DVD, but also some types of copy protection with it? - yes, example Macrovision ACP

Lastly, If i copied the DVD, and can play it from an ISO on my computer, that means I'm good to go as far as playing it on a regular DVD player goes, correct? - not necessarily, for example, you can create an ISO image from some DVDs with the dd command and it will play just fine on your computer, but you may not be able to burn it on a DVD

---

### Post by Bohlio on 2007-07-02
Alright, Thank you very much. I think I've got this whole thing worked out now. 
Once again, thanks :-)
-Bohlio

---

