---
title: "I installed wrong version of Automatix"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by tk92 on 2006-10-28
I installed wrong version of Automatix.
I am using Dapper, but i installed, a version for Edgy.
How do i remove this softwere?
I tried looking add/remove program, but i couldnt find it on the list.
and When i try to run automatix, it says its wrong version, but do not gives me the instruction to remove it.

What commands, or things do i have to do??????

ps. I am rather more comfortable with GUI than commands

---

### Post by meng on 2006-10-28
Drop to the command line and type:
sudo apt-get remove automatix

I did read your ps, but some things are fairly straightforward - bear with me.

---

### Post by confused57 on 2006-10-28
You can also use Synaptic Package Manager to remove the Edgy automatix(2)...I had to do this when I upgraded from Breezy to Dapper(removed Breezy automatix).

Edit: meng is correct, you may need to remove(or change) the automatix entry in your sources.list, also...

---

### Post by tk92 on 2006-10-28
thanks for very quick reply !!
I will try once i finish some stuff on windows.

Thanks again!!!

---

### Post by meng on 2006-10-28
After you do that command you may want to (again from command-line) check your repository list with:
cat /etc/apt/sources.list

and see if it includes any references to automatix. If in doubt, post the output of that command here.

---

### Post by tk92 on 2006-10-28
well meng, i am planning to install the automaticx for dapper so i dont think i have to edit the sources.list file do i?

---

### Post by meng on 2006-10-28
Good point, except I don't know if the repository entry is different for dapper vs. edgy. Then again, I don't know if uninstalling automatix will revert your sources.list to the pre-automatix configuration. In any case, reinstalling the correct version of automatix will re-add the correct repository entry.

---

### Post by tk92 on 2006-10-28
thanks for the help, meng.
I am able to use automatix2 thanks to you!

---

### Post by tk92 on 2006-10-28
and does it usually take forever to install multimedia codecs?

---

### Post by meng on 2006-10-28
Hehe, I don't know - is it REALLY slow? Why not take the opportunity to go outside and kick a football?

---

### Post by tk92 on 2006-10-28
it was done rigt after i wrote the msg.
it was raining... so i had to read a boook T_T

---

### Post by tk92 on 2006-10-28
o meng, can i have ur msn ?
I figure that u would be a great help to me :)

---

### Post by meng on 2006-10-28
PMed

---

