---
title: "Grub Error 21"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Tsega on 2007-02-04
Hey guys I'm completely new to this and I made a very huge mistake at work. I had two hard disks and I installed Ubunbtu 6.06 on one of them without any problem. Now I removed the hard disk(it belonged to another computer at home) formatted it and installed Windows Xp. Then came the problem, the computer at work has a GRUB Erro 21, I knew something like this could happen because I removed the hard disk but right now the other it has been formatted!

What is the best way to solve this problem? Please help out asap cause I need the PC for work tomorrow. 

If it might be of any help the computer at work has Windows Xp on it!

---

### Post by Mba7eth on 2007-02-04
Well if you remove the ubuntu hard disk, Of course it is the  problem. Any how since it is a fresh install yet. I really advise you to reinstall it again on ur non-home hard disk . 
Or if the hard disk you removed is not the one you installed on it ubunut the this is ur solution is to reinstall the grub. a lot of threads can be found in the forum. [check those out]("http://www.ubuntuforums.org/search.php?searchid=13937846")
Wish you the best
:) ):P

---

### Post by Mba7eth on 2007-02-04
I guess i got you wronge  :oops:  .... Sorry i'm a wake for 25 hours know :rolleyes: 
you want to get back ur windows :) 
OK you have to reinstall ur MBR and let it point to windows .... I believe alot you can find .... 
[here is one ]("http://www.ubuntuforums.org/showthread.php?t=351529")

Sorry again for misunderstanding  Cheers :D

---

### Post by Mr. Eddy on 2007-02-04
So the computer at work has only windows. If it is, you don't need grub anymore. The only thing you need to do is restore the mbr.

To do so, you need a XP CD. Reboot with the CD in the drive and let it fire all the way up. You'll have three choices. Select R for repair.

You'll be asked which windows installation you wish to repair, give it the answer, and then give the admin password.

Once at the prompt, type: FIXMBR

Answer yes, then type Exit. You should be able to boot into Windows at that point.

---

### Post by Tsega on 2007-02-04
Wow I love this!!!! That was really fast, thanks!!! Well first of all I removed the one with ubuntu on it and as far as I can see, I cannot install Ubuntu on my PC at work. So wat I need to do is remove GRUB completely from it. If you could tell me how to do that it would be really helpful.

By the way I'm not a Windows FAN and I'm really looking for ways to completely migrate to Linux (Ubuntu). I intend to do it step by step but it just so happens that I have to use Windows for work. 

Thanks Again!

---

### Post by Mr. Eddy on 2007-02-04
you can do that, the way I described the post above ;)

---

### Post by Tsega on 2007-02-04
Whew I'm trying to keep up with you guys! Thanks! I really like the reponses that you are giving me and I 'm jut trying it out right now and I will tell you the results after a few minutes.

---

### Post by Tsega on 2007-02-04
Yeepy IT'S DONE! Thanks man I really appriciate it. I hope I could be of any help but I'm afraid that would take some time. Anyways I love this forum and beleive me I will be here quite often and I would do whatever I can to help!

Ciao,
Tsega

---

### Post by Mr. Eddy on 2007-02-04
I'm a beginner too. And I could help you :). And it kicks to get appreciation for it .. :D. So you certainly can help people with problems your familiar with.

---

