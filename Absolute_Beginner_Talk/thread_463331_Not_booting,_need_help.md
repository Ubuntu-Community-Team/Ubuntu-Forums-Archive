---
title: "Not booting, need help"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by BionicSeraph on 2007-06-03
Here's my story. I recently got a new laptop (hp pavillion dv6000) and was very excited to install linux on it. Installed Feisty very soon after getting the computer. I was very disappointed because my wireless card didn't work (I have a broadcom). After about a week of messing with it I gave up and just started using my vista partition full time.

I decided to give up on linux and install it at some other time when it had better support for my hardware. So I did something rather stupid.I repartitioned all of the linux space back to windows. #-o Which was working fine untill I rebooted. Now the computer boots into GRUB with limited commands and I cannot figure out how to get it booting into windows again. 

Here's some info:
- Currently I am able to run live cds (I'm running ubuntu off the live cds I've been carrying around.)  

- I thought of reinstalling Ubuntu, but am unable to repartition windows to make room for it. I figure installing linux will fix any problems the GRUB is having.

I hope someone here can help me!

---

### Post by Ek0nomik on 2007-06-03
What do your partitions look like it?

You can't boot into Windows either?

What kind of wireless card do you have?

---

### Post by BionicSeraph on 2007-06-03
> **Ek0nomik said:**
> What do your partitions look like it?

You can't boot into Windows either?

What kind of wireless card do you have?


Partitions look like :
nfts 140GB
nfts 10GB (vista backup partition)
I got rid of the linux ones. Kind of an ungraceful removal of linux....

I can only boot into linux because I have the live cd. 

Wireless:
Broadcom Corporation 4311

---

### Post by Ek0nomik on 2007-06-03
A Broadcom Corporation 4311 should be fairly painless to setup by the way.  What problems were you having exactly?  I see you only have 2 beans, did you make any posts on the forum asking for help?  If you are still interesting in getting your laptop to run Ubuntu with your wireless card I can try to help you out.  I have a Dell Draft N Wireless 1500, and I am using Windows drivers for my laptop and I got it working after a few tries.  Now if I reformat my laptop I know how to get my wireless card working in a matter of minutes.  Once you have done it once, you know it for life.  :)

I have only used Windows XP (and I used XP for years), but I haven't used Vista whatsoever.  My guess is that you would need to get your MBR (Master Boot Record) working again so Windows can boot.  Or, alternatively, you could reinstall Windows and it will fix the MBR.

I think the command, "fixmbr" in Windows will get the Windows bootloader back on and fix your problems.  You will probably need your Vista CD and I am not sure how you boot into command line with a Vista CD, but a quick search will find that for you.

---

### Post by BionicSeraph on 2007-06-03
I'm still in a little bit of panic mode about the whole not booting thing. I'm trying to figure out my options. Thanks for the suggestions.


As for the not posting anything about the wireless, there are a ton of posts about getting the wireless card to work. I didn't feel the need to post more. I think the main problem was that I was using the 64 bit linux. I'll probably try again soon. The appeal of ubuntu is too strong to resist for long!

---

