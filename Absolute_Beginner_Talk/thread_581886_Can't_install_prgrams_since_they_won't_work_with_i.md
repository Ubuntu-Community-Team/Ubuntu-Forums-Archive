---
title: "Can't install prgrams since they won't work with i386?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-10-19
K, I start up a fresh install of 7.10 since 704 is running slow because it's choked up with beryl and thousands of programs. Anywho, it starts out great but when I try to install things, nothing wants to work. For instance, nvidia-xgl-new doesn't feel like turning on, I go to synaptic to look for it and it's not there for some ungodly reason so I can't get video to work. Secondly, in add/remove programs, tons of programs that I used to use now don't work with i386 computers anymore, like KTorrent. That was the only torrent program I got to work the way I wanted it and now it doesn't run on i386. Why? I have no clue, Besides the partition editor sucks this time around since I can't see what I'm doing. I'm tempted to go back to 704 unless these things get sorted out fast.

---

### Post by Daveth on 2007-10-19
um, have you checked the integrity of the new version as it sounds rather corrupted to me, especially if key things like synaptic are really missing. Did you burn your own cd, or upgrade through the internet?

---

### Post by Yellowbelly on 2007-10-19
I burned it. Downloads were going painfully slow so I torrented, and I think it was like an ftp of ubuntu.com or something. Thousands of people downloaded it with plenty of seeders so I don't see how it could have gotten corrupted. Should I be on a 64 version?

This is what it says in add/remove: "AbiWord Word Processor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
after the program description. And there's a lot more than that too.

---

### Post by Yellowbelly on 2007-10-19
I tried to download ms truecore fonts or whatever that is but it said that the it doesn't exist anymore. I went back to restricted drivers to test that out and it said: 
The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by LowSky on 2007-10-19
something sound fishy about your install.

I think you should reinstall

---

### Post by Daveth on 2007-10-19
I'd give this a go first

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and if it fails, then as Lowsky notes, it smells of fish and you might want to start again.

---

### Post by wigglydiggly on 2007-10-19
Is Universe and Multiverse enabled under software souces?

---

### Post by sleepwalker on 2007-10-19
I had the same i386 errors until I updated. Then everything worked fine. I would try that.

---

### Post by itsthechuck on 2007-10-30
I am having exactly the same problem, any ideas?

---

### Post by oldos2er on 2007-10-30
Check your Software Sources; make sure everything is enabled. You also need the Medibuntu repository added: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by natille on 2007-11-12
Hi there, I'm getting a similar error where (almost) everything in Add/Remove Programs says:

"*Program* cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

I have attached the error message window.

---

### Post by ubnewbie2 on 2007-11-12
Yes I had that too.  Some major stuffup with the 7.10 release version it seems.

After enabling all the sources, the problem largely goes away, but not entirely.  I still can't install vmware from packages - it still gives this error.  I installed it from the tarball that the vmware home site supplies instead.

---

### Post by Yellowbelly on 2007-11-12
you have to reinstall. I had an error during the install thing and guessed it didn't matter. Tried it again and everything worked smoothly. I'm thinking I wrote the cd too fast during the burn maybe because I have these weird glitches some times.

---

### Post by natille on 2007-11-13
> **ubnewbie2 said:**
> Yes I had that too.  Some major stuffup with the 7.10 release version it seems.

After enabling all the sources, the problem largely goes away, but not entirely.  I still can't install vmware from packages - it still gives this error.  I installed it from the tarball that the vmware home site supplies instead.

How did you "enable all the sources"?

I decided to try reinstalling 7.10 since I'd already been dealing with another problem that I figured it'd be good to try to clear the system of.

---

### Post by jaybombalous on 2007-11-13
are u trying to install 64 bit versions on a 32 bit OS? Because thats the only way I know of to get this error. Why its trying to install 64 bit on a 32 bit OS is beyond me, maybe the repositories are messed up.


hmm

---

### Post by natille on 2007-11-13
> **jaybombalous said:**
> are u trying to install 64 bit versions on a 32 bit OS? Because thats the only way I know of to get this error. Why its trying to install 64 bit on a 32 bit OS is beyond me, maybe the repositories are messed up.


hmm

I personally am not. I downloaded the i386 iso and installed it. I haven't done anything that should tell the Add/Remove Programs to search for 64 bit versions of anything. Granted, I do have an AMD processor, but unless I were to install Ubuntu 64 bit, I don't see how it could possibly make such a huge mistake.

---

### Post by ubnewbie2 on 2007-11-13
> **jaybombalous said:**
> are u trying to install 64 bit versions on a 32 bit OS? Because thats the only way I know of to get this error. Why its trying to install 64 bit on a 32 bit OS is beyond me, maybe the repositories are messed up.


hmm

lot's of people have struck this problem with gutsy.  Yes either the repo's or they way they are configured is messed up.  I have a suspicion it all started when people were having trouble installing on the first day when the servers were so slow that many installs timed out when they were checking them (even installs from CD).

---

### Post by ubnewbie2 on 2007-11-13
> **natille said:**
> How did you "enable all the sources"?

I decided to try reinstalling 7.10 since I'd already been dealing with another problem that I figured it'd be good to try to clear the system of.

system>admin>software sources

tick everything on the first and second tab - and what you desire on the third

---

