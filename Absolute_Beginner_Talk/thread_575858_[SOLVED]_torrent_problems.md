---
title: "[SOLVED] torrent problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
Hello new to Ktorrent
not so much to linux though i would say i still a noobie
i was useing rtorrent to do my downloading but i had a problem with it (I thought) but theres not really any community support on there site so when i tried getting help it didnt work.
So today i decided it was time to leave rtorrent for a new client. and ktorrent look good. but i am geting the same problem. Sad
So that leads me to beleive that i have miss confiured my system (ubuntu) or my network
Now for the problem when i start a torrent in ether client they do the same thing connect to the tracker and get a list of peers
then for maybe 10 min or 1 min depending every thing is good
all of a sudden peers start to vanish 1 by 1 or by 2s down to nothing then if i restart the torrent they all come back same ip's and everything...
really confusing
so any way help please Smile

---

### Post by Frak on 2007-10-14
The tracker may be weighing your sharing ratio to how much you download. Trackers are starting to do this for sharing issues.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
Hello frank,
i dont think that is the case because it doses it on files i am seeding 2
i am a member of a privet tracker and just reread their rules and stuff i dosent say they would do that becide my ratio is an 0.8 not awsome but not that bad they say the only penile below like .7 or .6 
i think it's my configuration or my network
but i really think its my setup
or maybe my internet provider  but i dout it any one know if d&e limits torrent trafic

---

### Post by Frak on 2007-10-14
> **<<joe>> said:**
> Hello frank,
i dont think that is the case because it doses it on files i am seeding 2
i am a member of a privet tracker and just reread their rules and stuff i dosent say they would do that becide my ratio is an 0.8 not awsome but not that bad they say the only penile below like .7 or .6 
i think it's my configuration or my network
but i really think its my setup
or maybe my internet provider  but i dout it any one know if d&e limits torrent trafic
what ISP do you have.

---

### Post by scapalexis888 on 2007-10-14
some isps do limit torrent applications. I once tried downloading torrents using verizon and i had a similar problem.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
My isp is D&E communications 
i dont think they limit

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
well i tryed another client just to see deluge same problem

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
Help i am so frustrated
I dont even know were to look for help on this

---

### Post by defrex on 2007-10-14
See if your ISP is on this list:

[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)

---

### Post by MatthewPlanchard on 2007-10-14
The only BitTorrent client I've ever used is Azureus. I had a similar problem for a while, though, and it ended up being a problem with my firewall blocking a port needed for the NAT.

Here's their Wiki Page on the issue:
[http://www.azureuswiki.com/index.php/NAT_problem]("http://www.azureuswiki.com/index.php/NAT_problem")

Basically it's a matter of making sure you've got certain ports open, which you can do through your firewall or router configuration settings.

---

### Post by ellgor on 2007-10-15
Hi,

What version of ktorrent are you using, if you are not sure which one you have click on the HELP button in the ktorrent window, then click on About Ktorrent, a window with the version number should be displayed, the current being 2.2.2.
If yours is 2.2.1 (or earlier) I would recommend changing to the newer version as a few bugs crept up in earlier versions.
The newest version is not available through the repositries so you will need to go to the KDE site and download from there, google KDE will get you there, hope this helps.

Regards, Ellgor.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-17
OH fiugred it out it was the nat problem

---

