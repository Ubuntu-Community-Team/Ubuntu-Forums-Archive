---
title: "Repositry and Synaptic package manager not recognising my internet connection."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by dfk789 on 2007-10-19
Hi, I've jsut done a fresh install of Ubuntu 7.10 completely overwriting whatever was on the drive previously. But now when i try to get any applications or packages it says i need a valid internet connection. Ive tried manually configuring my network but that made no change. Help quick please! :(

---

### Post by gubemton on 2007-10-19
Hi, I have the exact same problem. I've just installed 7.10 on a laptop and a desktop and neither can update or install new programs through synaptic or whatever. I can browse the web fine with Firefox so internet access is not the problem. Hopefully someone will quickly help me, dfk789 and probably many others with a solution.

---

### Post by 3ws on 2007-10-19
I'm having problems too. Not sure they are the same though. My problem is I can't seem to find anything to install. I've been looking for VLC but no results, eventhough I did the same thing on my work PC - Synaptic found it and installed it.

I also tried to watch an .avi but got a message saying no codecs, when i try to update i get a message saying 'I need a working internet connection'.

The connection is fine, now. Until an hour ago I had no internet connection, I set IPv6 value to 'true' and the problem went away. Don't know if it is related to this new problem.

---

### Post by gubemton on 2007-10-19
3ws, did you try applications > add/remove... and then set it to show "All Available" or "All Open Source" ? After I did that VLC got listed. But I can't install it. I get this again and again:

[IMG]http://img148.imageshack.us/img148/8020/screenshotki1.png[/IMG]

---

### Post by 3ws on 2007-10-19
Thanks Gubemton. That could be the reason why it isn't showing up, will give it a go later. I am a complete newcomer to Linux; yesterday was my first time installing and using.

I think i'll get the same error as you though - no connection. That's what I was getting with the codecs.

---

### Post by 3ws on 2007-10-19
Tried what was suggested above and still the same problem - the message about no internet connection.

---

### Post by dfk789 on 2007-10-19
Ok, well I seem to have fixed it for myself. Im not sure if this will work for you guys but here's where I think I went wrong. When i first installed it, I didnt enable a wireless connection. Now I've reinstalled, I enabled that. After the reboot now i'm able to get things from the repositry fine. Hope that helps you guys too. Have fun reinstalling! :)

---

### Post by 3ws on 2007-10-19
dfk789, that's not going to help a wired connection, is it? As i say, completely new to Linux!

---

### Post by dfk789 on 2007-10-19
Ah...hmm, well sorry about that. You're best off trying another fresh install anyway. Seems to have worked for me =/.  Literally nothing wrong with it now.

---

### Post by gubemton on 2007-10-20
Hi guys,
After doing this installation of VLC and other programs works fine :) : 

applications > add/remove... > Preferences > Software Sources > ubuntu software Tab:
- check: canonical supported & community-maintained
- uncheck: CD-rom

applications > add/remove... > Preferences > Software Sources > Third Party software Tab:
- check: archive.canonical.com/ubuntu gutsy partner

Try it and see if it works for you! The error message I got was very badly designed. "The list of applications is not available" isn't very helpful. More helpful would be an additional sentence: "you may need to enable more repositories in Software Sources (hyperlink) to install this application." Or even better: more of the repositories could have been enabled by default.

edit: I this does work for you, then please label this thread [solved]

---

### Post by 3ws on 2007-10-20
Well, it's going from bad to worse. I reinstalled (and seemed to have two installations of Ubuntu) and had the same problems i.e. no internet until I set Ipv6 to 'true'. But even then, I was still unable to download from the repositories.

I next used partition magic to delete the partition and format to FAT32. Now Ubuntu won't install. The installation gets to 92% and hangs. This has happened twice now.

I've been trying since Thursday evening to install. I really wanted this to work; sick of Microsoft. But I'm ready to give up.

---

### Post by 3ws on 2007-10-20
After 15 minutes of seemingly nothing, the installation has resumed. Though it was unable to download updates (as usual). I will see what happens when the installation completes.

---

