---
title: "Watching videos online in Fiesty"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Leximark on 2007-11-10
I've noticed a few people who've had a similar problem to mine.  I recently installed Feisty (I used to be running windows).  

I can watch videos on youtube, but when I try sites like crunchyroll (stays completely blank) or [http://www.canada.com/globaltv/index.html](http://www.canada.com/globaltv/index.html) (Looking up player) nothing loads.  I don't get video or sound.  I'm using firefox, and I have VLC Media Player and the firefox mediaplayerconnectivity thing.  I'm at a loss and I really want to watch Heroes.

---

### Post by Pumalite on 2007-11-10
Have you installed:

sudo apt-get install ubuntu-restricted-extras

What about adding Medibuntu to your sources.list and downloading all the codecs?:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by Leximark on 2007-11-10
Whahaaaa?
I'm going to guess no, because I don't know what you're talking about.  Thanks for the links.

---

### Post by Pumalite on 2007-11-10
Go ahead and do it then.

---

### Post by misfitpierce on 2007-11-10
install ubuntu restricted extras and all gstreamer codec plugins from add/remove programs... Search gstream.

---

### Post by Leximark on 2007-11-10
I'm having difficulty actually installing these things.  I'm sorry if it's frustrating, but I am really not a technologically savvy person.  
"Add Medibuntu to your sources.list" - how??
"as well as its GPG key to your keyring" - ?

It's telling me what to do but not how to do it.

---

### Post by Maestro23 on 2007-11-10
> **Leximark said:**
> I'm having difficulty actually installing these things.  I'm sorry if it's frustrating, but I am really not a technologically savvy person.  
"Add Medibuntu to your sources.list" - how??
"as well as its GPG key to your keyring" - ?

It's telling me what to do but not how to do it.

Those are commands to be used in a **terminal **(Apps>>Accessories>>Terminal).

You can copy/paste the commands if you want.

---

### Post by Leximark on 2007-11-10
Thanks Maestro, ^^

Ok, so when I try to install the ubuntu restricted extras I get an error message 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and when I try medibuntu it takes me to a configuration page in the terminal and I'm not sure what to do with it.

---

### Post by Maestro23 on 2007-11-10
> **Leximark said:**
> Thanks Maestro, ^^

Ok, so when I try to install the ubuntu restricted extras I get an error message 



and when I try medibuntu it takes me to a configuration page in the terminal and I'm not sure what to do with it.

In terminal:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade


Try again.

---

### Post by Pumalite on 2007-11-10
Run:
sudo dpkg --cofigure -a
sudo apt-get update
sudo apt-get upgrade

And report back.

---

### Post by Leximark on 2007-11-10
try which again?

---

### Post by Leximark on 2007-11-10
> **Pumalite said:**
> Run:
sudo dpkg --cofigure -a
sudo apt-get update
sudo apt-get upgrade

And report back.
> 
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
are the last three lines in the terminal.

---

### Post by Pumalite on 2007-11-10
If above doesn't work, you can then try:

sudo apt-get install -f

---

### Post by Leximark on 2007-11-10
I get a "Package configuration" screen in my terminal.

"Configuring sun-java6-jre"
and then a whole bunch of licencing stuff 
it's got <ok> at the bottom.  I don't know how to progress from here.

---

### Post by Maestro23 on 2007-11-10
> **Leximark said:**
> I get a "Package configuration" screen in my terminal.

"Configuring sun-java6-jre"
and then a whole bunch of licencing stuff 
it's got <ok> at the bottom.  I don't know how to progress from here.

Use the arrow keys are TAB to get to the OK. HIt Enter.

---

### Post by Leximark on 2007-11-10
hahahahaha, see what I mean when I say I'm no good with this stuff?

Anways:
> Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
107489 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
Preparing to replace sun-java6-bin 6-00-2ubuntu2 (using .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...
popped up.

---

