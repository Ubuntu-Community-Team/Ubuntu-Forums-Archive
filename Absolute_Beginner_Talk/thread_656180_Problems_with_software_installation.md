---
title: "Problems with software installation"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by vvule on 2008-01-02
I`am having a very strange problem when I try to Add any software!  After the choosing  software via Add/Remove and clicking on Apply, and after a few moment, apears a notification window which informs me that a software I`have choosed can`t be authenticated, even though i`ve choosed software from, let`s say, main repository. Nevertheless I click on install anyway, but then it don`t start to download!  And it`s so for every single program! Just to mention, my internet connection is working just fine! Can any one help  me

---

### Post by mmb1 on 2008-01-02
Do you get this problem in synaptic as well?

---

### Post by Repus on 2008-01-02
vvule, 

I had a problem with similar symptoms. Internet connection was fine but I couldn't update anything or add software. I received the same errors. 

For me, after insisting it couldn't be, it turned out to be my connection. My upstream proxy didn't like the way the packets were formed for updates and packages etc so it dropped them. If you have an upstream firewall, router, etc you may want to check that.

Good luck

---

### Post by vvule on 2008-01-02
Yes, apsolutelly the same problem in Synaptic

---

### Post by argie on 2008-01-02
I remember having this happen to me. It's likely that the keys that you have are corrupted. Go to System » Administration » Software Sources and get to the Authentication tab. Then try to Restore Default Keys. Switch your repositories around (if you're using the country repo, switch to the main repo and vice versa) then reload the repositories. That's what I had to do to make it go away.

EDIT: Ah, but it is likely that Repus is correct. I had to use a proxy at the time too. The proxy may have just corrected itself coincidentally at the same time as I did my stuff.

---

### Post by vvule on 2008-01-02
I`ve tried to change repository server, and to restore authentication key to defaults, but the things only became worse, the system came out with this:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

And also with this

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

And I`am connected through Proxy,and that just may be the cause!

---

### Post by Vadi on 2008-01-02
When you get that lock error, it means you have several package managers working - maybe apt-get in the terminal, synaptic, or add/remove. Close all but one you need, and try again.

---

### Post by SOULRiDER on 2008-01-02
Close all package managers running, if the problem is still there enter this intoa  terminal
```
 sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a 
```

---

### Post by vvule on 2008-01-02
For the time being, everything seems to be O.K. Right now I`am downloading updates for curently installed packages. After, I will try to download desired software! I`am not sure what the problem was, but anyway things seems to be fine at the moment (probably, there were some problems with proxy server) anyway thanks to everyone for the effort!

---

