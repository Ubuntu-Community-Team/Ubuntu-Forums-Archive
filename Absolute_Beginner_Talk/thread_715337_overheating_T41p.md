---
title: "overheating T41p"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mescito on 2008-03-04
Hi, I just installed Ubuntu 7.10, and ever since my computer has been periodically overheating and then shutting down (giving me a message like "critical temperature of 88 c reached") and I'm not sure what the problem is or where to begin.

---

### Post by johnnyhop on 2008-03-04
I'd doubt the install of Ubuntu caused the problem.  If you're comfortable with opening the computer case, check to see if all fans (rear of power supply, possibly case, and especially the fan on the CPU heat sink) are turning.  Also make sure the CPU heat sink is clean.  They can clog with dust and cause overheating.  Hope this is helpful.

---

### Post by mescito on 2008-03-04
> **johnnyhop said:**
> I'd doubt the install of Ubuntu caused the problem.  If you're comfortable with opening the computer case, check to see if all fans (rear of power supply, possibly case, and especially the fan on the CPU heat sink) are turning.  Also make sure the CPU heat sink is clean.  They can clog with dust and cause overheating.  Hope this is helpful.

Prior to installing 7.10 I was running an older version and I never experienced anything like this

---

### Post by johnnyhop on 2008-03-08
mescito, I'm surprised someone with with a good knowledge of Ubuntu didn't reply by now.  My reply was based more on my experience with computers in general than with Ubuntu specifics.  I frequent this forum with Ubuntu/Kubuntu related questions to debug and get my system working properly.  When I read your problem I thought for once I could be helpful.  Let's not give up this path until its exhausted.  Have you tried opening a system monitor and watched for CPU (Central Processor Unit--Pentium or AMD chip) usage?  If the graph shows extended usage above 90% the CPU will warm up and relies on cooling by the fan and heat sink on the CPU.  Are you doing more multitasking now than before?  Is the overheating more prone to happen when specific application(s) are running?  After how many minutes?  A CPU when properly cooled should be should be able to handle a 100% load indefinitely but if the fan isn't turning or the heat sink is clogged with dust prolonged usage over 50% can be a problem.  As I'm typing this quick reply I'm listening to music in Amarok have two other applications open and the CPU usage is averaging 10-16% while spiking briefly to 100% when Amarok selects the next song and flashes that songs title at the top of the monitor screen.  I suggest you give processor usage an observation  I think the application you need to watch is System Monitor in Gnome it is System Guard in KDE (Kubuntu).  Sorry if I'm being long winded.

---

### Post by mescito on 2008-03-12
I haven't yet ruled out a hardware problem, fan or heatsink related, but this case isn't easy to open (or put back together) so I'm kinda putting that off. The machine, centrino 1700 mhz , 512 megs of ram, does seem to be stressing the processor more than it did under the previous release. Generally I'll have a few browser windows open, pidgin, nicotine, xmms, and a torrent or two. 
I also installed a thermal monitor that I found in a similar post. If I open a .swf file the temperature jumps about 15 degrees C, according to the monitor.

---

### Post by johnnyhop on 2008-03-13
I'm not qualified to say if the 7.10 release should load the processor more but consider it reasonable to say newer os tend to be made to take advantage of the the higher performance the industry is giving the os developers to work with.  Yep I've *&X#$#(expletives deleted) at computer cases many times as a repair tech.  Have you discovered a correlation between cpu load prolonged temperature rise and the shut down?  If the problem is dirt related it will slowly get worse.  Another hardware related possibility is the heat sink not being tightly secured tightly to the processor, I wouldn't consider this to be as likely but not impossible.  Bottom line, if the processor temperature reports warm to hot and the heat sink feels only cold to slightly warm to the touch, you have a cpu heat dissipation problem.  You won't discover it without enduring the agony of opening the case.  What thermal monitor are you using?  I couldn't find such an application with a quick search in Adept Manager--would like to check it out.

---

### Post by mescito on 2008-03-24
> **johnnyhop said:**
> I'm not qualified to say if the 7.10 release should load the processor more but consider it reasonable to say newer os tend to be made to take advantage of the the higher performance the industry is giving the os developers to work with.  Yep I've *&X#$#(expletives deleted) at computer cases many times as a repair tech.  Have you discovered a correlation between cpu load prolonged temperature rise and the shut down?  If the problem is dirt related it will slowly get worse.  Another hardware related possibility is the heat sink not being tightly secured tightly to the processor, I wouldn't consider this to be as likely but not impossible.  Bottom line, if the processor temperature reports warm to hot and the heat sink feels only cold to slightly warm to the touch, you have a cpu heat dissipation problem.  You won't discover it without enduring the agony of opening the case.  What thermal monitor are you using?  I couldn't find such an application with a quick search in Adept Manager--would like to check it out.


Well, when the monitor tells me the temp is in the 80s+(c), the bottom feels very warm, as does the air coming out of the fan port. It's a thin-line lap top as well, so disassembly will be a last resort. I heard that there was some sort of fan control glitch with the latest releases, though my source has proven to be somewhat unreliable in the past.

---

### Post by johnnyhop on 2008-03-29
I concurr, laptops can be a king size can of worms.  I don't like to open laptops without a service manual.  Have you checked to see if the bios monitors fan rpm?  If so and it has a dedicated processor heat sink fan try rebooting when its hot and see if the fan speed is up there, I'd figure at least 2,000 rpm.  The fact that the air is very warm out of the fan port proves some cooling down of hot components is occuring.  Is the fan at the port turning fast enough?  If its the only fan?  Is an air intake restricted?  Have any rubber "feet" fallen off not leaving enough space above the table for an air intake to pull enough air in?  Consider spacing the bottom up just a little from the table.  Stacking two pennies in all four corners should be sufficient.  Hope this helps.

---

### Post by johnnyhop on 2008-04-01
Mr. mescito FYI I happened to stumble over a forum thread with discussion on the subject of overheating since the install or update to 7.10.  One of the possible causes is related to the driver used with some ATI display adapters and running compiz.  If you have not done so search for related threads...good luck!

---

