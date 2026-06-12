---
title: "Quastion about canonical repository"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-03
Hi

I want to download Opera via Synaptic, so I added the Canonical repositorys in my list(at the end): 

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

When updating I dont get any error, but I cant find Opera in Synaptic. Am I missing something here?

In a post they recommende to run this in the terminal first: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup Lets say I need to restore the list, how do I do that(I have already made the backup)

So are the "repositorys" only a list of urls where the program synaptic can get software from? Just like adding "www.download.com". Is it possible to do somthing wrong here?


Thanks for help!


Thomas

---

### Post by jpeddicord on 2006-11-03
Try installing Opera directly from Applications > Add/Remove. That I *know* has it, even if Synaptic for some strange reason does not.

Any yes, repositories are like download sites. Your computer contacts the sites for lists of software, and when you want to install something, Synaptic or APT will download and install it all for you. Repositories just tell it where to look.

Jacob

---

### Post by Marsolin on 2006-11-03
The only difference that I see with mine is a / that I have after ubuntu. If that doesn't work you could try adding Opera's repo so you can get the latest version. The Canonical repo is still at 9.0.

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free

---

### Post by Oki on 2006-11-03
Thanks for your help!

I tried applications>add/remove but no Opera there? I dont need the latest, and was hoping to get it the easy way via synaptic. I know I could get it via Automatic2, but I think it is strange that it dont show up in the synaptic or add/remove application?

---

### Post by Oki on 2006-11-03
Could you pl post yours Marsolin?

---

### Post by Marsolin on 2006-11-03
> **Oki said:**
> Could you pl post yours Marsolin?

Here it is.

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

---

### Post by Oki on 2006-11-03
Thank you:-)

I copy/paste your line over the canonical that I had, but still the same - no opera under add/remove or Synaptic. Strange! 

Edit; I tried again in Synaptic but wrote "Opera browser" and it showed up:-D 

Thanks for your help!

---

