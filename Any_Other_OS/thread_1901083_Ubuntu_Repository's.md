---
title: "Ubuntu Repository's"
date: 2011-12-27
forum: Any Other OS
---

### Post by Maky on 2011-12-27
Hi people.  
I currently have BackTrack4 fully installed on my computer. The operating system is built on the Ubuntu system. 
I hope I'm o.k posting on this forum as I have just been given "infraction points" for asking about backtrack4 at their forum because backtrack 5 is out now. 
Basicaly, I cant do any apt-get updates anymore as the Offensive Security repository's have been closed for BackTrack4 users. 
I am hoping that I am able to add the ubuntu repository's to my sources.list file and carry on from there. 
I was hoping that someone on here could advise me as to if this is possible or not. 
Will the packages I receive be compatible with my distro? I think they should right? BackTrack4 uses Ubuntu right. 
As far as I remember from when I had a copy of Ubuntu, The apt-get process will download anything the package depends on right? It checks to make sure it has what it needs?

---

### Post by snowpine on 2011-12-27
The Backtrack people are correct and you should listen to their advice. Backtrack 4 is based on an older version of Ubuntu that has reached its "end of life" and is completely unsupported.

---

### Post by collisionystm on 2011-12-27
> **Maky said:**
> Hi people.  I currently have BackTrack4 fully installed on my computer. The operating system is built on the Ubuntu system. I hope I'm o.k posting on this forum as I have just been given &quot;infraction points&quot; for asking about backtrack4 at their forum because backtrack 5 is out now. Basicaly, I cant do any apt-get updates anymore as the Offensive Security repository's have been closed for BackTrack4 users. I am hoping that I am able to add the ubuntu repository's to my sources.list file and carry on from there. I was hoping that someone on here could advise me as to if this is possible or not. Will the packages I receive be compatible with my distro? I think they should right? BackTrack4 uses Ubuntu right. As far as I remember from when I had a copy of Ubuntu, The apt-get process will download anything the package depends on right? It checks to make sure it has what it needs?

Add the 10.04 repo

You should be okay.

---

### Post by overdrank on 2011-12-27
Moved to Other OS/Distro Talk

---

### Post by Maky on 2011-12-27
Add the 10.04 repo? Is this an ubuntu repository or the repositorys for BackTrack 5?
I have been completely cut off installing this distro. I am having to manually update everything. 
You cant call it dead just because its unsupported by the people who created it. I'll bet you there are plenty of people still using it because of bugs in Back Track 5. I'm considering downloading the latest ubuntu and custom packaging to get what I want from backtrack into it.  
Anyone on here managed to get a decent pen testing environment on ubuntu?

---

### Post by collisionystm on 2011-12-27
cat /etc/apt/sources.list

post the output please

---

### Post by Maky on 2011-12-27
deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse
#deb [http://archive.offensive-security.com/repotest/](http://archive.offensive-security.com/repotest/) ./   # BackTrack Devel Repository

these repos are dead since release of BackTrack5

And thanks for your time [collisionystm]("http://ubuntuforums.org/member.php?u=1249225")

---

### Post by collisionystm on 2011-12-27
this should work

sudo add-apt-repository 'deb [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution main microverse non-free testing'

this apparently is the repo for backtrack 5. 4 is using pwnsauce and 5 is using revolution


do a sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by Maky on 2011-12-27
I should be able to just add that repository to the sources.list right?

Well I allready found the Backtrack 5 repos but I cant figure out how to add the key i downloaded for the synaptic package manager.

GpG key? 

I have it in my root folder but The console commands I have tried wont except it

W: GPG error: [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AB6DA34B475A6B7F

---

### Post by Maky on 2011-12-27
Thanks for your time I figured it out.

---

