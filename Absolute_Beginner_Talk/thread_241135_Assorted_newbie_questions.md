---
title: "Assorted newbie questions"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Teamster on 2006-08-21
Question 1: I have a 5.1 speaker set, and I'd like to be able to use all 5 satts. How do I change it? I see no option in the system menues.

Question 2: How can I get Ubuntu 6.06 i386 installed OVER my 64-bit version? I'm tired of jumping through hoops to get niche programs for 64-bit.

Question 3: How can I check what version of Ubuntu I have? I think that Update Manager updated me to 6.06 without my knowing.

Thanks!

---

### Post by meng on 2006-08-21
Answer to 3:
lsb_release -a

---

### Post by Teamster on 2006-08-21
Ah thank you. So, one down, two to go.

---

### Post by Jjohn on 2006-08-21
Hi Teamster, 
I too was sick of the hoops with the 64 bit version and decided to overinstall the 386 arch instead. I made an error when allowing the partioner to auto partion I ended up with the 32bit, 64bit and winxp all ALONGSIDE each other. The bonus for me is that I did not lose any data and could delete the 64 bit disto at my leisure. I had a friend re arrange some folders for me so I could not bork anything important. Hope this helps.

---

### Post by Teamster on 2006-08-21
So wait... I don't really have enough room on my hard drive for that, is there  a way that I can get all my files ported over onto the i386?

---

### Post by VirtuAlex on 2006-08-21
> **Teamster said:**
> Question 1: I have a 5.1 speaker set, and I'd like to be able to use all 5 satts. How do I change it? I see no option in the system menues.
I doubt at this time you can get it working without going to command line. If I remember it right I followed this [http://alsa.opensrc.org/SurroundSound]("http://alsa.opensrc.org/SurroundSound") and it made my speakers live. Well, sometimes... Despite having very good speakers I do not play music on comp too often nowdays, so I skept messing with surround further for now.
> **Teamster said:**
> Question 2: How can I get Ubuntu 6.06 i386 installed OVER my 64-bit version? I'm tired of jumping through hoops to get niche programs for 64-bit.
Just reinstall and when it ask you for partitioning answer manual. Then just do nothing, cause everything is partitioned. You need only assign mount points and mark check boxes to reformat partitions.

---

### Post by VirtuAlex on 2006-08-21
> **Teamster said:**
> is there  a way that I can get all my files ported over onto the i386?
What exactly you want to be ported? Your home folder?

---

### Post by loserboy on 2006-08-21
e-mail all your files to yourself....  jk, just see how much room you need for all your crap then make an lil partition for it then reinstall clean over 64bit

edit: er 2 posts happened while i was typing this one

---

### Post by VirtuAlex on 2006-08-21
> **loserboy said:**
> er 2 posts happened while i was typing this one
man, you need to apt-get install tuxtype ;)

---

### Post by Teamster on 2006-08-22
What I really want is to have all my stuff like my IM settings, my bookmarks, my Thunderbird POP3 stuff, etc. Not as much files, as settings.

---

### Post by loserboy on 2006-08-22
? whats tuxtype :)

---

### Post by Teamster on 2006-08-22
Please, let's keep this thread on topic.

---

### Post by philipacamaniac on 2006-08-22
Backup your home directory. In other words, everything in /home/yourusername.

There are a lot of hidden folders in there, and that is where ALL your settings are stored (bookmarks, etc.). In Nautilus, go to View --> Show Hidden Files. Or on the command line, type
```
ls -al $HOME
```

Copy all that stuff to a CD, or an external drive.

---

### Post by VirtuAlex on 2006-08-22
> **Teamster said:**
> What I really want is to have all my stuff like my IM settings, my bookmarks, my Thunderbird POP3 stuff, etc. Not as much files, as settings.
The easiest way is to back up your home folder somewhere. All your settings and stuff are in hidden folders (their names start with dots). Then restore it after you install the system. You just would have to point your thunderbird to right location instead of creating new profile. Or put content of old profile to the new one. Either way.

---

### Post by Teamster on 2006-08-22
Ok, here's what I decided. I figure, all I really wanted was my Firefox bookmarks. Now, I can always re-bookmark those sites. So, I'm doing a fresh install.

Would the DVD that came with this month's issue of Linux magazine work? I got that magazine for the express reson of that DVD.

---

### Post by VirtuAlex on 2006-08-22
> **Teamster said:**
> Please, let's keep this thread on topic.
Relax :) Linux is fun. It's not like we're discussing Iraq war. Besides your topic is "Assorted newbie questions" :D

---

### Post by VirtuAlex on 2006-08-22
> **Teamster said:**
> Would the DVD that came with this month's issue of Linux magazine work? I got that magazine for the express reson of that DVD.
Why not? Check it for errors, there should be an option at boot time, and then go ahead - fresh start.

---

### Post by Teamster on 2006-08-22
Ok, now that I'm all ready and prepped, how do I tell the installation to overwrite the current Ubuntu partition, not the whole drive?

---

### Post by VirtuAlex on 2006-08-22
> **Teamster said:**
> Ok, now that I'm all ready and prepped, how do I tell the installation to overwrite the current Ubuntu partition, not the whole drive?
As I said above you choose manual partitioning. It will show you your drive. You should recognize your current partitions easily. Most likely ext3 partition is your root and swap is... well it is swap. So make note of their numbers like hda1 hda2 or something like that, and click next. It will ask you how to mount them.  So you mount your ext3 as / and mark the checkbox to reformat it. Do not reformat anything else.

---

### Post by Teamster on 2006-08-22
Ok, so here's the final deal. I am postponing this until I am concious. It's almost 2am here, and I can barely stay awake. Knowing that I can seriously mess up my computer, I'm going to wait until I can thing clearly.

Thanks for everyone's help!

---

### Post by Teamster on 2006-08-22
Ok, back awake, anyone care to give me a bit more detailed walkthrough? Please?

---

### Post by VirtuAlex on 2006-08-22
Maybe, if you post screenshot of Gnome Partition Editor, I can tell you exactly which partition should be mounted where. Otherwise it is so straightforward that I'm not sure why you need walktrhough to walk a straight line.

---

