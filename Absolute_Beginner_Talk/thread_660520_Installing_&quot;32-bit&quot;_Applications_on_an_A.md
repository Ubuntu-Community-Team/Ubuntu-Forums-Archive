---
title: "Installing &quot;32-bit&quot; Applications on an AMD64 Ubuntu machine..?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by brucewagner on 2008-01-06
Yes, I am a total newbie.   Sorry.   :)

I am so confused about this....

Can i install "32-bit" Applications on an AMD64 Ubuntu machine..?

Is that a bad thing...?

In Add/Remove Programs.... and in Automatix...    There are applications listed as (32-bit), and there are some listed as (64-bit)....

I assumed that that meant I could only install the ones labelled 64-bit....  since I am on an AMD64 bit computer, and version of Ubuntu...

No?

I just installed Skype (32-bit) from Automatix....  and it SEEMS to work fine!   What's up with that?

Does this mean that I can install WINE using Automatix....  and it will work too....!?!?!?   :)

---

### Post by Moop on 2008-01-06
Yes you can run 32bit apps on a 64bit OS and it's not a bad thing. Sometimes it's the only thing. I don't think there is a 64bit Skype.

---

### Post by brucewagner on 2008-01-07
It's not true the other way around though, eh...?

You CAN run 32-bit apps on a 64-bit machine...  

But

You can NOT run 64-bit apps on a 32-bit machine...

Correct?

---

### Post by dcstar on 2008-01-07
> **brucewagner said:**
> It's not true the other way around though, eh...?

You CAN run 32-bit apps on a 64-bit machine...  

But

You can NOT run 64-bit apps on a 32-bit machine...

Correct?

Yes.

---

### Post by brucewagner on 2008-01-08
I am using an AMD64 ubuntu platform. 

There are some "plug-ins" listed on Automatix "for 64bit Forefox".

How do I know if I am running 64bit Firefox or not?

Am I correct in assuming that plugins for 64bit Firefix will NOT work if I am using 32bit Firefox?

---

### Post by flamelab on 2008-01-08
Throw Automatix away immediately , use only Synaptic , it is a great program .

If you have Gutsy 64 installed , ALL the programs that are downloaded from the repos are 64 bit ( amd64 to be correct ) .

---

### Post by brucewagner on 2008-01-10
This is so confusing...

Over in this thread ( [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) ), I read this....

"Step 3. IF you installed the Ubuntu 64-bit Operating System and have not installed the necessary files that allow you to run 32-bit programs, you will need to open a terminal window and paste: sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 All 32-bit users should skip this step."

DOES that mean that these programs must be installed before you can run 32-bit apps on a 64-bit version of Ubuntu...?

I'm not sure if I should even be running a 64-bit version of Ubuntu...  If the capability of running 32-bits apps is not built-in....   And if some of these Java/FlashPlayer/Divx/DVD issues would be easier to solve on the 32-bit version...   I don't know which way to go.

---

### Post by Golem XIV on 2008-01-10
I think that the problem is that in a 64-bit system the libraries (if you're a Windows user, think DLLs) are in 64-bit format.  The 32-bit programs look for 32-bit libraries and complain if they can't find them.  So, you have to install additional 32-bit libraries that the 32-bit programs need - no more, no less.

The problems that I could see with 64-bit systems are usually related to drivers and not applications.  Most apps that run in Ubuntu have been compiled separately for 32-bit and 64-bit platforms and your default repositories should reflect this.

I have  installed the Skype beta (32-bit only) on a 64-bit HP laptop using this how-to:
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

and it works flawlessly.

---

