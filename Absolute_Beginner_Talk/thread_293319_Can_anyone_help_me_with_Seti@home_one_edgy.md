---
title: "Can anyone help me with Seti@home one edgy"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by deep.tinker77 on 2006-11-05
I need help! I'm trying to install seti@home and I just can't figure out what I'm doing wrong. I've tried to install it using adept manager and by downloading the file it self and installing it using krusader file manager. It seems to install fine, but after I install, it tells me to run /home/*/Boinc/run_client and /home/*/Boinc/run_manager to run the GUI. I receive an error :

*@*:~/BOINC$ ./run_client
2006-11-04 18:34:12 [---] Starting BOINC client version 5.4.9 for i686-pc-linux-gnu
2006-11-04 18:34:12 [---] libcurl/7.15.3 OpenSSL/0.9.8a zlib/1.2.3
2006-11-04 18:34:12 [---] Data directory: /home/*/BOINC
2006-11-04 18:34:12 [---] Processor: 1 GenuineIntel Intel(R) Celeron(R) M processor 1.50GHz
2006-11-04 18:34:12 [---] Memory: 1.47 GB physical, 1.95 GB virtual
2006-11-04 18:34:12 [---] Disk: 32.98 GB total, 28.46 GB free
2006-11-04 18:34:12 [---] No general preferences found - using BOINC defaults
2006-11-04 18:34:12 [---] Local control only allowed
2006-11-04 18:34:12 [---] GUI RPC bind failed: -1
2006-11-04 18:34:12 [---] GUI RPC bind failed: -1
2006-11-04 18:34:13 [---] Local control only allowed
2006-11-04 18:34:13 [---] GUI RPC bind failed: -1
2006-11-04 18:34:13 [---] GUI RPC bind failed: -1
2006-11-04 18:34:14 [---] Local control only allowed
2006-11-04 18:34:14 [---] GUI RPC bind failed: -1
2006-11-04 18:34:14 [---] GUI RPC bind failed: -1
2006-11-04 18:34:15 [---] Local control only allowed
gstate.init() failed: -180

What am I doing wrong. I've read the documentation on the Seti homepage, I just don't understand. Please help. Thanks!
Edit/Delete Message

---

### Post by Ecthelion on 2006-11-05
> What am I doing wrong. I've read the documentation on the Seti homepage, I just don't understand. Please help. Thanks!

It would be usefull to know the link to that homepage... 

> Edit/Delete Message

What do you mean?
If you mean you solved the problem, please post the solution... There might be someone else whit the same...
Else... It confusing...

---

### Post by autocrosser on 2006-11-05
Just so you know--the repositories have a newer version of Boinc & I have the .deb location for Debian unstable--You would need to modify your apt sources.list 

The Wiki information page: [http://wiki.debian.org/BOINC](http://wiki.debian.org/BOINC)

Ask me for any other information you need---

---

### Post by deep.tinker77 on 2006-11-09
@ Ecthelion: The link that I am using is off of the Seti@home homepage in the fourms section. 

[http://setiathome.berkeley.edu/forum_thread.php?id=21571](http://setiathome.berkeley.edu/forum_thread.php?id=21571)

And I'm sorry about the Edit/delete entry. It was a mistake. Thank you.

---

### Post by deep.tinker77 on 2006-11-09
@ autocorsser: 

I went to the link, but it only tells me to use the distro available for edgy, kde, and that's the version that I cannot get to work. Thanks for the reply. I'll keep trying, only because I hate quitting anything after I have started.

---

### Post by autocrosser on 2006-11-09
All you need to do is:

If you are running [DebianUnstable]("http://wiki.debian.org/DebianUnstable") you should add the following lines to your /etc/apt/sources.list file:  

 # BOINC packages for Debian "sid" (unstable)
deb     [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main
deb-src [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main


This will get you the MOST current version of Boinc available & install it in a friendly .deb way--Sid unstable is running Boinc Client 5.4.11 & Seti App 5.13+cvs20060510-1(not the latest--but very stable)

---

### Post by deep.tinker77 on 2006-11-09
[QUOTE=Ecthelion;1718988]It would be usefull to know the link to that homepage... 

Sorry Ecthelion, here is the correct link. 

[http://boinc-wiki.ath.cx/index.php?title=Installing_The_BOINC_Client_Software_on_Linux](http://boinc-wiki.ath.cx/index.php?title=Installing_The_BOINC_Client_Software_on_Linux)

Thank you.

---

### Post by deep.tinker77 on 2006-11-09
[autocrosser]All you need to do is:

If you are running [DebianUnstable]("http://wiki.debian.org/DebianUnstable") you should add the following lines to your /etc/apt/sources.list file:  

I'm running edgy 6.10, KDE. Will this still apply?

---

### Post by autocrosser on 2006-11-09
Edgy is based on Debian unstabe--I'm using Edgy (and have been since Knot 1) & the Debian version is what I'm using. It should not matter which version of 6.10 you are using--Boinc is distro independent--I've been with SETI from 1999 & started using Boinc as soon as it went stable....My Boinc page is:

[http://www.boincstats.com/stats/boinc_user_graph.php?pr=bo&id=1ec9271415bd00a4ca08bc5a1a5b0702](http://www.boincstats.com/stats/boinc_user_graph.php?pr=bo&id=1ec9271415bd00a4ca08bc5a1a5b0702)

The last two years have been using Ubuntu & whatever the current version of SETI was at the time........I just moved to a Dual 3.2 unit a few months ago & after I got everything set-up, my stats went thru the roof;)

---

### Post by deep.tinker77 on 2006-11-11
Thanks auto, I will give it a shot tonight. The only things that are keeping windows on my laptop is Seti and my ipod. If I can get both of them to work correctly, I will be XP free!!!!

---

