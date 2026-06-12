---
title: "Do i Have a 64bit or 32bit computer"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-22
Hello,

I started using ubuntu about 2 days ago on my laptop, I installed the ubuntu 64bit edition on a partition to duel boot with windows XP and i have been able to access the internet and play mp3 and simple things like that. How ever i have had a few problems including installing EasyUbuntu and Installing Flash Player 7 - 9. 

With EasyUbuntu it downloads the files then says "Fix broken Packages" and With flash it tells me i "do not have the right architecture"

I was Wondering weather this was because i am using the 64bit addition of ubuntu. 

i have always assumed that i have a 64bit processor because i have an "AMD Athlon 64" and i assumed that was what the the "64" ment.

but recently i have had a few problems like when i downloaded the 64bit version of "DAEMON Tools" for windows they did not work, but did work when i downloaded the 32bit version.

I would like yo know weather there is anyway i can find out if i have a 64bit or 32bit computer or if anyone can help me.

thank you very much.

---

### Post by DaveBorealis on 2006-10-22
Hello James,

If it still boots, fire up Ubuntu and type 'cat /proc/cpuinfo' and you should see the model name, among other things.  If this doesn't answer your question, then do a Google search on the model name and see what specs you find.

Best regards,
Dave

---

### Post by GStubbs43 on 2006-10-22
Even if you have a 64-bit computer, you should probably use the 32-bit Ubuntu, as a lot more programs will work with it and there will be less problems.

---

### Post by Jamesbowden on 2006-10-22
Firstly the model of my laptop is an Amilo A 1630. according to my google search it is Althlon 64 based (i already new that) and in some user reviews on tech sites they mention that it is 64 bit.
but i would still like to be certain.

Secondly would there be any draw backs to using the 32bit edition?



thanks for your help

---

### Post by dbott67 on 2006-10-22
> **Jamesbowden said:**
> the model of my laptop is an Amilo A 1630. according to my google search it is Althlon 64 based (i already new that) and in some user reviews on tech sites they mention that it is 64 bit.

but i would still like to be certain.

thanks for your help

The CPU is 64-bit, but as others have mentioned it's probably best to use the 32-bit version of Ubuntu.  The AMD cpu is capable of running both 32-bit and 64-bit operating systems, however, most hardware vendors do not have stable 64-bit drivers (which makes getting hardware working properly a major pain) and many software vendors have not ported their applications to 64-bit versions.

This is mostly due to the fact that there is little demand for 64-bit desktop computing and that the dominating OS (Windows) is still 32-bit (XP & soon to be released Vista).  So, 32-bit version of Ubuntu is the way to go, unless you want to squeeze every last bit of performance out of your computer and be on the leading edge.  You will need to be pretty self-sufficient in reading through forums & what-not to solve some of your issues.

-Dave

---

### Post by dbott67 on 2006-10-22
> **Jamesbowden said:**
> ... would there be any draw backs to using the 32bit edition?

PROS:
[LIST]
[*]Support for most hardware drivers & software packages
[*]Part of the mainstream
[/LIST]

CONS:
[LIST]
[*]Not being able to take full advantage of a 64-bit CPU
[/LIST]

Overall, the performance issue will be relatively minor compared to the frustration factor that you might face.

The i386 architecture is your friend.

-Dave

---

### Post by Jamesbowden on 2006-10-22
Alright so it looks like i'm gunna download the 32 bit version then. 

Thanks for all your help.

---

### Post by dbott67 on 2006-10-22
You're welcome.

---

### Post by gumbald on 2006-10-22
Just to add, you can only install 64-bit software on a relevant OS. Therefore you'll only be able to run 64-bit Windows programs on Windows x64, which I doubt you'll have.

---

