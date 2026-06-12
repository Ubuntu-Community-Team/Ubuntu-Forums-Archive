---
title: "Is it possible to run Ubuntu from OSX?"
date: 2007-06-23
forum: Apple PPC Users
---

### Post by tnseditor on 2007-06-23
Hello,
A friend of mine has a Mac Mini with a G4 PPC processor and OSX Tiger.  Is there any way to boot Ubuntu inside OSX?

---

### Post by immelman on 2007-06-24
Hey!

You could try [Q ( kju: )]("http://www.kju-app.org/kju/"). I don't know how it will work since I have a dual boot system.
Otherwise you might just want to show him the LiveCD, if it is to show him how it runs.

Cheers,

---

### Post by czechman86 on 2007-06-24
there is also mac on mac, but i have yet to get that to work. from what i understand, MoM is now part of the mac on linux project and maybe an update will come soon.

---

### Post by Phoenix301 on 2007-06-24
Hey, this is the friend that tnseditor was taling about. I have already viewed the live CD, but i dont want to install it over osX, and i dont really want the dual boot either where i boot in one or the other. What im hoping for is something like the reverse of Mac on Linux where i could boot Linux directly while in osX rather than booting osX while in Linux. I hope that clears up what is being asked for sure...

(btw, im a 'her' not a 'him' ;) )

---

### Post by Auria on 2007-06-24
> **Phoenix301 said:**
> Hey, this is the friend that tnseditor was taling about. I have already viewed the live CD, but i dont want to install it over osX, and i dont really want the dual boot either where i boot in one or the other. What im hoping for is something like the reverse of Mac on Linux where i could boot Linux directly while in osX rather than booting osX while in Linux. I hope that clears up what is being asked for sure...

(btw, im a 'her' not a 'him' ;) )

Well Mac-on-Mac, despite what its name suggests, should be able to run Linux in a window from your mac. However its home page is now dead and i thought the project was definitely gone, but if czechman86 is right then it could be it :)

PS: all those computing boards should definitely need a 'gender' thing like other forums got, i don't like being called "him" either :-P

---

### Post by quizno50 on 2007-06-24
Well; if your Mac is fast enough, you can always try Q.app... I don't have a link but you can google for it... I don't know how well it'll run a PPC processor, since it's designed more so to emulate an Intel system... I use it to run old DOS stuff when the mood hits me, but on my poor iBook anything more than command-line Linux or DOS is pretty much un-usable... Let me know how it works for you if you give it a try... 

BTW: Here in the North West US, I don't know where you all are at, but girls running Linux, much less, PPC Linux is very rare; so, my apologies in advance if I make that mistake...

EDIT: woops... Should have read all the posts first [IMG]http://www.terborg.net/images/emoticons/embarrassed.png[/IMG]

---

### Post by Phoenix301 on 2007-06-25
i will eventually try the Q.app if i can get approval from my parental units.. :p I think it would do okay, tho that may just be my ego speaking cuz i love os X. I am on a Mac Mini with 512 MB of ram, 1.5 GHz PPC G4 running OS X version 10.4.10...not the best in the world, but any thoughts on how that might handle with Q.app? 

btw, no hard feelings if im mistaken as a guy :p I was just putting that im a girl for reference

---

### Post by 3rdalbum on 2007-06-25
Q.app (Qemu) will be slow, and not really very usable. Sorry to say that, but it's the truth - my computer is better specced, yet emulating an x86 processor is only good for extremely lightweight systems like Syllable and Haiku. And there are no other virtualisation programs for PowerPC.

If you can convince your parents to let you run a dual-boot system (you can do it with an external hard disk), or if you can buy a cheap "behind the technology wave" x86 PC, you'd be able to run Ubuntu as a perminant option.

---

### Post by terinjokes on 2007-06-25
> **czechman86 said:**
> there is also mac on mac, but i have yet to get that to work. from what i understand, MoM is now part of the mac on linux project and maybe an update will come soon.

Hey! I'm working with the MOL project. I'm a gentoo user, but using Ubuntu ATM to investigate problems.

Yes, we have merged the MoM fixes back into MOL, however we still do not have it booting in OSX (incompatible bootloader), and we have temporarily lost the ability to boot 2.6.x linux kernels. Our lead developer, JoseJX, is away in Africa, so development has slowed for the time being.

---

### Post by czechman86 on 2007-06-25
> **terinjokes said:**
> Hey! I'm working with the MOL project. I'm a gentoo user, but using Ubuntu ATM to investigate problems.

Yes, we have merged the MoM fixes back into MOL, however we still do not have it booting in OSX (incompatible bootloader), and we have temporarily lost the ability to boot 2.6.x linux kernels. Our lead developer, JoseJX, is away in Africa, so development has slowed for the time being.

i cant wait til he comes back. the little that i have used of mac on linux, i thought was great! i cant wait to see what you do with mac on mac. good luck!

---

### Post by dfennell on 2007-07-30
I am running Unbuntu 7.0.4 on an emulated x86 32bit machine under Q. The performance is ok, but my host is a dual PPC G5 running at 2.3GHz.

I agree with 3rdalbum's comments that you will likely find it unusable on a G4. You can see feedback from other Q users [here]("http://qemu-forum.ipi.fi/viewforum.php?f=6").

---

### Post by ajmctaggart on 2007-07-30
TO THE FRIEND OF TSEDITOR-

I believe Parallels (definitely not free) gives a trial, try it and see how you like it...

Sorry guys, but when it comes to Apple, it's just not as easy to get the Open Source/Freeware nowadays...Parallels is great but is by no means a free alternative...

Just my input,
ajm

---

### Post by ajmctaggart on 2007-07-30
Stupid, Stupid, Stupid

Sorry, Parallels is only for Intel Macs, those aren't even real macs anyways- lol

Sorry, I was wrong on that one...

Anyone for VMware?

---

### Post by 3rdalbum on 2007-07-31
> **ajmctaggart said:**
> 
Sorry, I was wrong on that one...

Anyone for VMware?

Count me out - it doesn't run on my Mac as it's a PowerPC Mac :-)

---

