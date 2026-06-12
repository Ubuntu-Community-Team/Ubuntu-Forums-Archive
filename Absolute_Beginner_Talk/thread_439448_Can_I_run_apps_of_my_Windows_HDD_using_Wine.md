---
title: "Can I run apps of my Windows HDD using Wine?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-05-10
**I really need to use Microsoft Word to write up and edit resumes. I've tried to use Openoffice and Kword but the format always gets messed up and since 99% of the people that will read my resume will view it with Word I need to see what they see. So is there anyway to run Word in Linux off of my Windows HDD. I was think of something like linking the directories under my .wine folder to the Windows HDD. I also tried to install it in wine but I can't get it to work.**

---

### Post by Nekiruhs on 2007-05-10
Yes you can, if you have NTFS-3g installed.

---

### Post by Martin on 2007-05-10
It's not that simple and it depends upon which version of Word you have. Older version are supported better under wine. Why don't you save your resume as a pdf directly from Openoffice and distribute that?

---

### Post by annda on 2007-05-10
i don't know about word, but you can try

wine /media/sda1/Program\ Files/Microsoft\ Office/winword.exe

i just made up that path, i don't have MS Office, so i can't check. just remember: linux is case sensitive and spaces need a backslash.

BTW: why not save your CV as a PDF? that way everyone will see the right thing.

---

### Post by bodhi.zazen on 2007-05-10
You have several options.

1. Dual boot.

2. Take a look at crossover office. [http://www.codeweavers.com/](http://www.codeweavers.com/)

3. Wine. Doh ... Looks this will not work acording to wine Hq

4. Use Open Office and save the document as a .rtf or pdf

5. Virtualization. [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by fakie_flip on 2007-05-10
You could install VMWare Server and run a virtual XP inside of Linux. Then install Word in that. Power on the XP virtual machine whenever you need to use Word. Power it off when you are done to return all the system resources back to Ubuntu. This is much more convient than a dual boot, but you need at least 512 mb of ram, and if you have more, then VMWare should work even better.

---

### Post by Skidpad on 2007-05-10
> **Martin said:**
> It's not that simple and it depends upon which version of Word you have. Older version are supported better under wine. Why don't you save your resume as a pdf directly from Openoffice and distribute that?

I 2nd this.  If your intended recipients don't need to *edit* your resume' - this is the best way to go.  It's built into OOo and works great.

---

### Post by fakie_flip on 2007-05-10
> **Martin said:**
> It's not that simple and it depends upon which version of Word you have. Older version are supported better under wine. Why don't you save your resume as a pdf directly from Openoffice and distribute that?

That's because MS has seen how successful Wine has been, and so they are trying to make their software not work under Wine. My brothers MS Flight Simulator will not run under Wine or Cedega. The zune mp3 player software made by MS will not run under Wine, and last time I checked IE7 would not run under Wine however the previous versions did.

---

### Post by fakie_flip on 2007-05-10
Microsoft's goal is to get you to buy Vista, not just use, but buy, and not use any other os such as Linux. They want to make sure you bought it by having your Vista computer call to MS servers about once a month, so they can be sure your install has been bought. They also are trying to get people to ditch XP, and force you to upgrade to Vista by not supporting XP anymore. This means that after you have installed XP, you can't run the Microsoft update anymore to get updates for security, so your computer is going to be vulnerable to hackers, and you won't have bug fixes. New games will only run under Vista, so if the big gamers are going to have to buy Vista and buy a computer powerful enough to run that bloated os.

---

### Post by Dallas_Alien on 2007-05-14
> **fakie_flip said:**
> Microsoft's goal is to get you to buy Vista, not just use, but buy, and not use any other os such as Linux. They want to make sure you bought it by having your Vista computer call to MS servers about once a month, so they can be sure your install has been bought. They also are trying to get people to ditch XP, and force you to upgrade to Vista by not supporting XP anymore. This means that after you have installed XP, you can't run the Microsoft update anymore to get updates for security, so your computer is going to be vulnerable to hackers, and you won't have bug fixes. New games will only run under Vista, so if the big gamers are going to have to buy Vista and buy a computer powerful enough to run that bloated os.

Microsoft is actually supporting consumer editions of XP software until 2014. You can will be able to run XP update for some time as long as you have SP2 installed, which is really something you should have already.

Only games requiring DirectX10 will require the use of Vista (DirectX10 wont be available in XP), of which I don't think there are any available at the time of this post. And only a few Graphics cards support it, I think ATI's was actually released today, so DirectX10 wont be required for a short while at least. 

And as far as having to buy a powerful computer to run vista if you want the latest games you probably want a  much more powerful computer than the minimum spec to run vista with aero to run the latest games in vista, xp or ubuntu.

---

