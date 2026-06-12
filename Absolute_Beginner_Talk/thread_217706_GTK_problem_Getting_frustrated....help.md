---
title: "GTK problem? Getting frustrated....help?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by richardq on 2006-07-17
Ok. I've reinstalled Dapper again (probably 4th time in the past week) to try and trace my problem better. I'm wondering if anybody's got any ideas. Here it is in a nutshell:

1. I do the Dapper install using the Alternate iso. - installation goes fine.

2. The gnome apps I try are all loading very slowly. Gedit takes 12 sec, Terminal takes 10 sec. etc..

3. Launching a second instance of the same app will be much quicker. So launching a terminal window once one remains open only takes 1 or 2 sec.

4. I then install the linux-686-smp package using Synaptic.

5. Apps are still launching slowly.

6. I setup and run prelink per the instructions on this forum.

7. All gnome apps launch FAST. Gedit launches almost instantly. - I'm now a happy camper.. temporarily...

8. I install ipodder, f-spot, and a few other things and then by the time I reboot the system things are launching after a 10second delay again.

9. XMMS launches quickly but GTK based apps seem to have the big delay.


Notes:

The ipodder installation seems to bring in the gtk libraries again. Maybe the benefits sought by installing the linux-686-smp package are being overwritten? It runs prelink after each installation procedure but this doesn't seem to help.

Reinstalling the linux-686-smp package and prelinking again doesn't seem to fix it.

The machine is quick enough - it's a P4-3Ghz with 1GB ram. 

I've seen apps launching fast on this system with my own eyes. But it seems like the linux-686-smp + prelink fix is only temporary until I install something that modifies the libraries again.

Is this a GTK related problem? I ran strace's on Gedit both when things were launching fast and launching slowly and they didn't look vastly different.

Also note, everything runs fine. It's just annoying to have that lag in launching apps. Once they're up, they seem to run fast enough. But putting a 10sec delay on all application launches becomes annoying quite quickly...

---

### Post by philippe_carlo on 2006-07-17
Is there a reason you are installing an SMP kernel. You do have only one processor, right?

---

### Post by richardq on 2006-07-17
I do have only one CPU however it has hyperthreading. I read that if you have an HT capable cpu then you should run the linux-686-smp package (personally I don't really know.. such is the life of a linux newbie ;)). 

Also, I tried the normal linux-686 package through several first attempts and installing this along with the prelink did nothing to improve my situation. However using the 686-smp package did. So I'm sticking with that if for no other reason than it's the only thing that got things launching quickly albeit temporarily.

---

### Post by philippe_carlo on 2006-07-17
I did  not know about the hyperthreading stuff, to be honest. It's a very weird problem. For some reason, it seems like loading dynamic libraries is taken way too much time.

---

### Post by richardq on 2006-07-17
> **philippe_carlo said:**
> I did  not know about the hyperthreading stuff, to be honest. It's a very weird problem. For some reason, it seems like loading dynamic libraries is taken way too much time.

Yeah. It seems as though it's only GTK based apps. But I don't really run many apps that aren't. XMMS was the only one I could think of that might not be GTK based and it launches quickly. I'd like to test it out a little more. Are there any other non-gtk apps that are in the default ubuntu install that I could test it with?

Also, is it possible that a package like ipodder could overwrite the gtk libraries that are installed with the linux-686-smp package? I am assuming that it would only overwrite these if they were newer than the ones on my system. And related to that, is it possible to step back a version on the libraries to check if the newest gtk libraries are the problem?

---

