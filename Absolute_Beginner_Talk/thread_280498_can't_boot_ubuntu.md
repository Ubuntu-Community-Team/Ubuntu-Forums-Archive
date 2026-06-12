---
title: "can't boot ubuntu"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by jtpinhead on 2006-10-19
The md5 matches the one on the  iso.  I burned to a cd-rw.  I get the error while loading from the cd, it stops on loading drivers and then the screen goes black into cmd prompt.

---

### Post by raul_ on 2006-10-19
Try to check the CD for errors. There's probably a problem with the .iso . If u run the tests and some sumcheck fails, then u'll have to re-burn the .iso . If not, post again :)

---

### Post by jtpinhead on 2006-10-19
It had some mismatch on it when i ran the check from the book.  the checksum was perfect though.

---

### Post by gn2 on 2006-10-19
> **jtpinhead said:**
> The md5 matches the one on the  iso.  I burned to a cd-rw.  I get the error while loading from the cd, it stops on loading drivers and then the screen goes black into cmd prompt.

Have you tried the additional boot options, it's F6 I think, it's on the Ubuntu Live CD splash screen.

After trial and error, "noapic nolapic" worked for me.

---

### Post by bulldog on 2006-10-19
> **jtpinhead said:**
> The md5 matches the one on the  iso.  I burned to a cd-rw.  I get the error while loading from the cd, it stops on loading drivers and then the screen goes black into cmd prompt.

It's not advised to use a cd-rw,try a cdr instead.

Burn it on low speed for the best results.

---

### Post by jtpinhead on 2006-10-19
> **bulldog said:**
> It's not advised to use a cd-rw,try a cdr instead.

Burn it on low speed for the best results.

if it really makes a difference ill try that.  i just hate wasting cds.

---

### Post by bulldog on 2006-10-19
> **jtpinhead said:**
> if it really makes a difference ill try that.  i just hate wasting cds.


An Ubuntu cd is **never** wasted,if you won't use it ,pass it trough to one of your friends.:D

---

### Post by jtpinhead on 2006-10-19
I wrote it to a cdr.  same thing.  after
configuring drivers   ok 
it does nothing then goes to a blank screen.  "noapic nolapic" didnt work either

---

### Post by jtpinhead on 2006-10-20
Ive been trying withall these suggestions someone please help.

---

### Post by localuser on 2006-10-20
Have you tried to re-download the image?  If not then I would recommend it.  Sometimes those bits get disoriented in the ether :) 

~Cheers

---

### Post by jtpinhead on 2006-10-20
the sum was perfect i dont see why redownloading would make a difference

---

### Post by Henry Rayker on 2006-10-20
Maybe give us your hardware specs. Also which image did you download? You may want to try the alternate install iso.

---

### Post by jtpinhead on 2006-10-20
i dl'd desktop.

amd athlon 64 3500+
1 gig ram
nvidia geforce 6600 gt
2x 160 gb hitachi hd raid0
40 gb western digital hd
dvd burner

---

### Post by jtpinhead on 2006-10-20
please can someone help any more suggestions?

---

### Post by Nayani P on 2006-10-20
Hello All,
I have the same problem too. I am new to UBUNTU and tried the Live CD (original live CD from Ubuntu). The system booted first time and thereafter it just doesnt boot. Any suggestions please? Thank you.

regards
Nayani

---

### Post by jtpinhead on 2006-10-20
strange.  What error are you getting?  Any suggestions for either of our problems?

---

### Post by localuser on 2006-10-20
> **jtpinhead said:**
> the sum was perfect i dont see why redownloading would make a difference

Sorry.  My bad.  I thought you said that you got errors or a mismatch of some kind.

---

### Post by jtpinhead on 2006-10-20
> **localuser said:**
> Sorry.  My bad.  I thought you said that you got errors or a mismatch of some kind.

When i sumchecked the iso it came out the same as the md5 file, but when i checked the cd for defects in the boot meneu it had a mismatch.

---

### Post by localuser on 2006-10-21
Where are you with this?  One of the suggestions was to re-burn the image on a CD-R rather than a CD-RW.

Have you tried that?  If not, then try it on a slow burn rate.

EDIT: I just found your previous post stating that you tried this.  I missed it on the first read-through.

---

### Post by jtpinhead on 2006-10-21
so what should i do? why is the md5 sum correct but the check for defects a mismatch?

---

### Post by localuser on 2006-10-21
> **jtpinhead said:**
> so what should i do? why is the md5 sum correct but the check for defects a mismatch?

Well, why there's a mismatch, I couldn't know.

But since there is this mysterious mismatch, and the image isn't working as it should, then perhaps it couldn't hurt to try to re-download a new image.

It may not be the best solution, and it may not fix the problem, but I guess that's what I would do next.

Also, I noticed that you're on an AMD Athelon 64.  I'll mention this at the risk of being obvious, but did you ensure that you downloaded the AMD64 version?

---

### Post by jtpinhead on 2006-10-21
i thought the intel x86 version worked on the 64 bit processors.
in the description it says
> For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure
I also heard some programs dont work on 64 bit.
theres also this option on my cd burning software that says use buffer protection (burn proof, just link, ect).  I use it because its checked by default.  should i turn this off while burning the ubuntu cd?

---

### Post by localuser on 2006-10-21
I've never dealt with the AMD64 version of Ubuntu but the fact that the download page states "For computers based on the AMD64 or EM64T architecture" tells me that perhaps that should be your choice.  I would definitely try this given all the problems you've encountered.

Perhaps this also explains the strange discrepancy that you found with the checksum.

EDIT: By the way, I too thought that the AMD64 was functionally compatible with the x86 instruction set, but I would at least try both out to see where the problem may be.

---

### Post by bulldog on 2006-10-21
> **localuser said:**
> I've never dealt with the AMD64 version of Ubuntu but the fact that the download page states "For computers based on the AMD64 or EM64T architecture" tells me that perhaps that should be your choice.  I would definitely try this given all the problems you've encountered.

Perhaps this also explains the strange discrepancy that you found with the checksum.

EDIT: By the way, I too thought that the AMD64 was functionally compatible with the x86 instruction set, but I would at least try both out to see where the problem may be.

The best thing is to use the alternate as first choice and the live cd second.

If you're not familiar with Ubuntu **don't** use the 64bit version,this causes only more trouble.

I saw you have a raid 0 config and another hdd.
It's possible that this causes your trouble.

I'm not familiar with raid config's,but I should look if there are problems with Ubuntu and raid.

---

### Post by localuser on 2006-10-21
> **bulldog said:**
> If you're not familiar with Ubuntu **don't** use the 64bit version,this causes only more trouble.

Hey bulldog, just out of curiosity, what's up with the 64 bit version that makes it a bad choice?  I infer from your post that it's okay for non-beginners, is that correct?  Or is it a bad choice all around?

What's different with the 64 bit version than the x86 version?

---

### Post by raul_ on 2006-10-21
64 bit words vs 32 bit words :P that's what's different. But u can run 32 bit version in a 64 bit processor, it won't explore it to the max but u won't tell the difference. and some 64 bit are a bit unstable from what i've heard

---

### Post by gn2 on 2006-10-21
> **localuser said:**
> Hey bulldog, just out of curiosity, what's up with the 64 bit version that makes it a bad choice?  I infer from your post that it's okay for non-beginners, is that correct?  Or is it a bad choice all around?

What's different with the 64 bit version than the x86 version?

It's problematic. The problem being that there isn't much 64-bit software to take advantage of.

And it's buggy and nasty and causes problems. Any truly honest 64-bit user would admit that.

If they won't they're kidding themselves.

That being said I wish them well, because I'm looking forward to using it in 5-10 years time when it's more reliable and relevant.

---

### Post by Boar on 2006-10-21
I tried to install Edgy and didn't work for me either. I think it doesn't recognize my hard drive, a Sata Barracuda model.

---

### Post by jtpinhead on 2006-10-23
so what should i do to fix this problem?  How can there be a mismatch but not an md5 sum error?

---

### Post by bulldog on 2006-10-23
> **localuser said:**
> Hey bulldog, just out of curiosity, what's up with the 64 bit version that makes it a bad choice?  I infer from your post that it's okay for non-beginners, is that correct?  Or is it a bad choice all around?

What's different with the 64 bit version than the x86 version?

There's nothing wrong with the 64bit ISO,but you will have trouble with flashplayer and other things.

When you have a little experience with Linux and know where to look you can just give it a try though.:D 

But there's little performance to win so I advice the 32bit version.

---

### Post by bulldog on 2006-10-23
> **jtpinhead said:**
> so what should i do to fix this problem?  How can there be a mismatch but not an md5 sum error?

Well we can be argumenting this for a week..............just download the alternate cd and try again.

We can't solve your problems,only give advice in what you could do.

You have to do it yourself you know.

---

### Post by jtpinhead on 2006-10-26
Its working now.  I plugged in a external HD.  Strange isnt it?  Anyways, when I try installing it,it stops at 30% and freezes.

---

### Post by Bartender on 2006-10-26
jt - 
I think I can explain your question about md5's.  The downloaded .iso is one monolithic file that creates just one md5 checksum.  You checked that against the md5 on the website and it matched, right?  That tells you the download was good.  That was the first transfer of data to be checked.  

Then you convert that .iso into a bootable CD.  That conversion creates hundreds of files and there are md5's for every one of 'em.  Several things can cause a bad burn - a worn out optical drive, burning too fast, cheesy media, a crappy power supply in your PC, etc. etc.
So there are 2 steps.  Your original md5 checksum has nothing to do with whether the burn came out OK.  If your disc failed the "Check CD for Defects" test then that means the disc wasn't burned correctly.  If the download md5 (the first check) came out OK and you still have the download saved on your hard drive, try burning again really slow with a good quality CD-R, not RW.

---

### Post by dmiller622 on 2006-10-28
> **gn2 said:**
> Have you tried the additional boot options, it's F6 I think, it's on the Ubuntu Live CD splash screen.

After trial and error, "noapic nolapic" worked for me.

I am a noob on this, what do you mean by boot options noapic nolapic.

 Can you be more specific on the boot option. When i boot from the live cd and I go to boot options. Once I press F6 (I think ) do I add noapic nolapic end of the boot line that is already in there.

Thanks

---

