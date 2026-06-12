---
title: "PPC: How do I go from the beta of Hardy to the release version?"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by VCF on 2008-04-25
I started up my iBook G3 this morning expecting there might be some upgrade to the release version but there was nothing (no upgrades at all available) and the security repositories are broken again.  The last time I had any upgrades was 5 days ago.  Should I just re-install from the live/alt CD I'm downloading now?
thanks,
VCF

---

### Post by avtolle on 2008-04-25
I installed the rc myself over last weekend, and haven't had any upgrades for a few days. I would think that if you installed the few upgrades there were (Monday were the last, IIRC) you would be up to date. 
To check what version you have (rc or whatever), in a terminal type ```

lsb_release -a 
```.
Mine returns 8.04, with no mention of beta, release candidate, so I presume it's final.

On the repositories, there is a change for ppc. Sorry, I don't have the link, but everything now is to "port" and not "archive" or whatever. You will need to edit your sources list file to reflect that. In the archived threads there is a post from Stream303 that discusses this.

Edit: http://www.xubuntu.org/news/hardy/ports is one place the repository change is linked.

---

### Post by VCF on 2008-04-25
> **avtolle said:**
> I installed the rc myself over last weekend, and haven't had any upgrades for a few days. I would think that if you installed the few upgrades there were (Monday were the last, IIRC) you would be up to date. 
To check what version you have (rc or whatever), in a terminal type ```

lsb_release -a 
```.
Mine returns 8.04, with no mention of beta, release candidate, so I presume it's final.

On the repositories, there is a change for ppc. Sorry, I don't have the link, but everything now is to "port" and not "archive" or whatever. You will need to edit your sources list file to reflect that. In the archived threads there is a post from Stream303 that discusses this.

Edit: [http://www.xubuntu.org/news/hardy/ports](http://www.xubuntu.org/news/hardy/ports) is one place the repository change is linked.

Thanks, I'll try the lsb command. You should try checking out whether your repos are ok with: sudo aptitude update   I changed the sources list to [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) as was recommended and I can't even get a hit on [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy Release.gpg  It may be because the servers are so busy with everybody trying to upgrade at once.  I'm hoping that somebody will post their sources list that actually works :)

---

