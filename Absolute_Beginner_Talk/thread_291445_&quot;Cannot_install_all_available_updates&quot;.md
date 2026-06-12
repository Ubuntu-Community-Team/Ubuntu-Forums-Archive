---
title: "&quot;Cannot install all available updates&quot; ?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by petersjm on 2006-11-02
Hi guys. For about two weeks (since about the same time I installed a patch to get Amarok to play flac, in case that's related) I keep getting this pop-up every time I try to update software:

> Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

Then it lists a dozen packages (build-essential, faac, faad, lame, and quite a few others). I've tried doing as the pop-up tells me, by doing a dist-upgrade in the terminal, but it tells me the packages will be "held back" and won't be updated. Same for Synaptic. Is there anything I can do to resolve this? Thanks :)

---

### Post by NeoLithium on 2006-11-02
I had a similar error with packages being held back, and I did this (each line is a seperate command:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade

```
And it installed the held back packages; not sure if that will help you; if not, post back :)

---

### Post by bulldog on 2006-11-02
Well basicly you know already what's wrong.
You have something installed which prevent you from updating your packages.

Only thing is to find out which package it is and then it's for you to decide what to do.

---

### Post by petersjm on 2006-11-02
> **NeoLithium said:**
> I had a similar error with packages being held back, and I did this...

Thanks, Neo. I tried that but it didn't work :(

[quote=Bulldog]Well basicly you know already what's wrong.
You have something installed which prevent you from updating your packages.[/quote]

Thanks, Bulldog. So I guess it's probably the flac patch for Amarok as it occured around the same time. I'll see if I can track it down, uninstall it, and try upgrading again. If that works, I guess I'll have to convert my flac files...

---

### Post by bulldog on 2006-11-02
> **petersjm said:**
> Thanks, Neo. I tried that but it didn't work :(



Thanks, Bulldog. So I guess it's probably the flac patch for Amarok as it occured around the same time. I'll see if I can track it down, uninstall it, and try upgrading again. If that works, I guess I'll have to convert my flac files...

Try ```
sudo aptitude update && sudo aptitude upgrade
```
and see if you get some error messages which can be helpfull to track down the problem.

---

### Post by petersjm on 2006-11-02
Thanks, Bulldog, but that gives me the same output, unfortunately. I located the "unofficial" patch I had installed for Amarok through Synaptic and tried to uninstall it, but it wants to uninstall Amarok and Totem as well... Maybe if I apt-get through the terminal instead of aptitude? I'll give it a go. Thanks for your help :D

---

### Post by petersjm on 2006-11-04
Okay, I managed to downgrade the package I thought was causing the problem described above, but it hasn't made a difference. Is there any way to figure out which package is causing the problem?

---

### Post by petersjm on 2006-11-06
Can anyone possibly help with this? Following on from the above, I tried a dist-upgrade again which gave the following output:

```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  build-essential dpkg-dev faac faad ffmpeg g++ lame libc6-dev libfaac0
  libfaad2-0 libgpod0 liblame0 libmp4v2-0 libxvidcore4 mjpegtools
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
```

So I then tried to upgrade the first on the list on its own (build-essential) with *sudo apt-get install build-essential*, expecting it to say something like "build-essential is already the newest version" or something. But this is what I got instead:

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
E: Broken packages
```

Any help resolving this would be eternally appreciated :)

---

### Post by bulldog on 2006-11-06
You should repair your broken packages with synaptic first.

---

