---
title: "After installing ubuntu 6.06 what's next?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by rowster27 on 2006-10-20
just installed ubuntu 6.06 what's the next step? should i update the packages by using synaptic or just download and use automatix2? i just wanted to know the most simple and most efficient procedure to setup (best setup) ubuntu 6.06 on my desktop. 

im so sorry for asking this questions this will serve as a benefit for other users also.

thank you ubuntu and God bless you all.:)

---

### Post by adwait on 2006-10-20
Open up synaptic and update your system....

---

### Post by Kateikyoushi on 2006-10-20
Update the packages first then install easyubuntu or automatix if you feel like it. I think it is easy to install packages without those if look around and read a few docsm not mentioning the better understanding of the system.

---

### Post by moma on 2006-10-20
Finalize (fulfill and improve) your Ubuntu with Automatix.
Goto step 5) here [http://www.futuredesktop.org](http://www.futuredesktop.org)

.
PS. Flash Plugin v9 (beta) for Firefox:
[http://linux1.no/forum/viewtopic.php?p=33213#33213](http://linux1.no/forum/viewtopic.php?p=33213#33213)

---

### Post by rowster27 on 2006-10-20
what is the default sourcelist of ubuntu dapper?

---

### Post by migla on 2006-10-20
> **rowster27 said:**
> what is the default sourcelist of ubuntu dapper?

Open terminal and type
```
gedit /etc/apt/sources.list
```

(if you want to modify it, type gksudo at the beginning of that bit)

---

### Post by Perfect Storm on 2006-10-20
It's gksudo gedit.

or use nano.

---

### Post by migla on 2006-10-20
> **Artificial Intelligence said:**
> It's gksudo gedit.

or use nano.

Thanks.

---

### Post by rowster27 on 2006-10-21
i already updated my system using synaptic.

do i have to add extra repos AND dl automatix2 and use it? 
is it necessary to add extra repositories? (by the way what do you mean by uncomment? 
OR should i choose between adding repos and using automatix2?:confused:

---

### Post by Midway on 2006-10-21
I used Automatix2 for the first time a couple of days ago after a fresh install with updates.  Automatix will add the other repos for you.  It gives you a choice afterwards of keeping these repos (which I did) or reverting back to the standard repos.  What I noticed it did was enable all the repos in sources.lst plus added some Automatix ones.

BTW, I noticed that it automatically installed Flash Player 9 beta as well.

---

### Post by rowster27 on 2006-10-21
> **Midway said:**
> I used Automatix2 for the first time a couple of days ago after a fresh install with updates.  Automatix will add the other repos for you.  It gives you a choice afterwards of keeping these repos (which I did) or reverting back to the standard repos.  What I noticed it did was enable all the repos in sources.lst plus added some Automatix ones.

BTW, I noticed that it automatically installed Flash Player 9 beta as well.

so i dont have to use this code anymore?
gedit /etc/apt/sources.list

thank you for the info Midway and God bless.:)

---

### Post by Midway on 2006-10-22
I did not have to edit my sources.lst though another way is to open up Synaptic, select Settings and then Repositories.  There you can just check the boxes of the unused repos to enable them and then hit reload.  After Automatix runs (and if you click yes to keep the new repos) you will find every repo "checked" and an added "getautomatix" one. 

Good luck and welcome to Ubuntu! :)

---

