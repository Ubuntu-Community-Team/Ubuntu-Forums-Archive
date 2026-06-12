---
title: "Conflicting advice"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-21
[COLOR="Blue"][SIZE="4"]Hello all i have had ubuntu on my pc for a couple of days now along with xp, i am trying to find out if i need a firewall for unbutu some have said i dont need anti virus or firewall on ubuntu others say yes, if i do which is best and is there instructions how to install for this linux newbie (in plain english not gobbly gook) ubuntu seems to be working fine in these early days  need to get mp3 player or a plugin for amarok or similar will look in forums for this,as i have hard drive partitioned xp and ubuntu if someone did hack/access my ubuntu could they get at info on the xp portion ill finish this post on behalf of all newbies of my intelligence by apologising if some posts are repeats of some one elses i know it must be annoying for you experienced users but sometimes its easier for us to put things into our own words, many thanks once again in advance to the good people of unbutu forums you are gods children and much thought of ,skiddly[/SIZE][/COLOR]

---

### Post by macogw on 2007-02-21
iptables is a firewall that's built into the linux kernel.  it's the same firewall that's in hardware firewalls like routers (which are really just cheap linux boxes), so you already have a firewall.  since there are almost no viruses for linux and the ones that exist would require you to authorize their execution, virus scans are not needed. now, if you install things from places other than the official repos, you could be at risk because those programs haven't been confirmed as "safe" like the ones in the repos have.  for safety (unless you read the source of everything else before installing it to be sure it's not bad for you), you should only install things from the repos.  if you are also using windows, it might be good to have clamav on your ubuntu install so that you can scan and catch windows viruses to protect your windows computer.  it might actually work better scanning from within linux cuz some viruses can hide from your AV if they are running at the time (and they can't run without you being booted into Windows, so if you scan while in linux they can't run and hide)

---

### Post by batholith on 2007-02-21
a firewall can never really "hurt", I use iptables, which is the default installed firewall on ubuntu.  I used the following thread to set mine up...it was fairly well explained set-up...I did not have to customize it, it works for all my internet endeavors...(I didn't have to modify any port settings, etc).  It also passed all the port checking tests listed on my machine...

[[COLOR="DarkOrange"]http://www.ubuntuforums.org/showthread.php?t=159661[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=159661")


Some people use the GUI "Firestarter", which is a front-end to iptables, but I couldn't get that working properly, but the custom firewall explained in the above thread worked like a charm!

---

### Post by keith11 on 2007-02-21
Yes, a firewall may not hurt, BUT as you are a newbie and so am I and I find that with certain firewalls, you may end up reconfiguring your internet AFTER you have installed a firewall. This may create unnecessary trouble for you if you don't have time to invest in figuring out if there is a problem and then solving it. iptables works fine but at the end, it's your call.

---

