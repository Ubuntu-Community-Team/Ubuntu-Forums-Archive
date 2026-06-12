---
title: "Gnaural Problems"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by deez on 2007-03-31
Hello all.  I've tried to install Gnaural.  On the homepage, [http://gnaural.sourceforge.net/download/](http://gnaural.sourceforge.net/download/) , it says that it is native to Ubuntu, but I can't get it through apt-get.  

I downloaded the package from the Ubuntu site

Then the package installer tells me:

Error: dependency is not satisfiable, libatk1.0-0

I tried to apt-get this package and it says:

libatk1.0-0 is already the newest version.


Any ideas?

Thanks

---

### Post by deez on 2007-03-31
Is there anybody out there?

---

### Post by Maestro23 on 2007-03-31
Gnaural is in the repositories.  You might have to enable some extra ones.

Check here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Good luck.

---

### Post by deez on 2007-04-01
Hmmmm...I went through the process detailed in the link and still cannot find Gnaural in the Add/Remove Applications or through a terminal with apt-get.  Any suggestions?

I have all the sources checked and added to my respositories.

---

### Post by tommcd on 2007-04-01
The link from sourceforge says the package is available in fiesty:
[http://packages.ubuntu.com/feisty/sound/gnaural](http://packages.ubuntu.com/feisty/sound/gnaural)
But I don't see it under "sound" in edgy:
[http://packages.ubuntu.com/edgy/sound/](http://packages.ubuntu.com/edgy/sound/)
(I'm at work now so I can't check my synaptic repos).  In less than a month fiesty should be out. Easiest thing is to wait for fiesty and get it then.

---

### Post by deez on 2007-04-01
I'm not sure what Fiesty means.  Is that another distro I'll have to install, or another repository?  Thanks for your help.

---

### Post by tommcd on 2007-04-01
Ubuntu releases new versions every six months. The current one is "edgy" 6.10 . Also many people use "dapper LTS" 6.04. The LTS = long term support (3 years). Other versions are supported for 18 months.
The next version, "fiesty" 7.04, is due to be released areound April 20th or so.

---

### Post by deez on 2007-04-01
Thanks a lot for your replies.  Does changing to Fiesty entail an entire system overhaul?

---

### Post by tommcd on 2007-04-01
The short answer is...possibly.
When fiesty comes out you will be able to upgrade via terminal similar to this method to upgrade from dapper to edgy:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
Or you could just edit your /etc/apt/sources.list and change every entry of "edgy" to "fiesty" and do <sudo aptitude update> followed by <sudo aptitude upgrade>. Or you can upgrade from the fiesty CD as it says in the link I provided. Are you using dapper or edgy? If you are in dapper I would not try to upgrade from dapper to fiesty, you may have problems, and skipping versions is not recomended. When people upgraded from dapper to edgy, it went well for many people, but some people had problems they needed to fix.
As for me, I always do a clean install with the alternate CD when I upgrade. Best way to avoid problems imo. But that's just me. 
I would download a fiesty CD first when it comes out, then try to upgrade like in the link I provided. That way if it don't work you can just do a clean install with the CD.

---

### Post by Rick123 on 2007-10-31
> Gnaural is in the repositories. You might have to enable some extra ones.

Check here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Good luck.

Okay what it looks like... Gnaural is no longer a repository... this i find strange when it was the only program in brain wave technology that could be found in the repositories. I talk about the new ubuntu gutsy..
I dont know if they have forgotten this program... how and were do i tell my opinion were that i want them to add this program again to the  repositories??

---

### Post by tommcd on 2007-11-01
Gnaural is in the universe repo in Gutsy
[http://packages.ubuntu.com/gutsy/sound/](http://packages.ubuntu.com/gutsy/sound/)
Scroll down to find gnaural. Make sure you have the universe and multiverse repos enabled in synaptic. See this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
After enabling universe and multiverse hit the reload button on the top panel in synaptic and you can then search for and install gnaural.

---

