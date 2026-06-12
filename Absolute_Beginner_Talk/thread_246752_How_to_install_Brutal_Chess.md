---
title: "How to install Brutal Chess"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-08-29
It says just run from source code but I don't know how to do that.

---

### Post by meng on 2006-08-29
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
look at the final section

---

### Post by Narcoleptic_Insomniac on 2006-08-29
That doesnt work, when I press sudo aptitude install that thing-essential it says a bunch of jargon and at the end it says aborted

---

### Post by meng on 2006-08-29
It would be easier to help if you could show the output of that command. Bunch of jargon & aborted doesn't tell us much.

---

### Post by chuckyp on 2006-08-29
The package you are looking for in synaptic is build-essential 

Or you could just open a terminal and sudo apt-get install build-essential

If it fails please post the output.

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **meng said:**
> It would be easier to help if you could show the output of that command. Bunch of jargon & aborted doesn't tell us much.

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

Thats the entire message it gives me, sorry I didnt give it all to you the first time.

---

### Post by chuckyp on 2006-08-29
And what are you typing to get that error? 

Try 
sudo apt-get install build-essential

At a terminal window.

---

### Post by Narcoleptic_Insomniac on 2006-08-29
> **chuckyp said:**
> The package you are looking for in synaptic is build-essential 

Or you could just open a terminal and sudo apt-get install build-essential

If it fails please post the output.

It asks me to put the Ubuntu CD in and press enter, I do, and a window pops up saying "Ubuntu CD detected          You can start the package managaer application with it now" and I press "Start package manager", and then another window pops up saying "Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

So I'm stumped.

---

### Post by meng on 2006-08-29
In that case, just abort the terminal, reinsert the CD, start up Synaptic Package Manager, and select the package "build-essential" for installation. Then "Apply Changes".

Before you leave Synaptic, you will want to go to Repositories, uncheck the CD and check everything else. In future, you can install from repositories and it won't ask for the CD but instead will search the repositories.

---

