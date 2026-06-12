---
title: "UGH. (Java problems)"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Royal_Pwner on 2007-12-08
I've tried installing java multiple times now.
I've downloading everything, made the symbolic link, restarted the browser, installed it, done the changing file type thing, everything.

It simply will not work.
Help, please. I just got an ubuntu computer and already it's hard to use. Help me.

---

### Post by meborc on 2007-12-08
try removing all java things you have installed up to now... enable all repos and install ubuntu-restricted-extras (be sure of the legal issues beforehand) this should install the sun jre as well as all the media codecs you will need

btw - what browser are you trying to get the java to work with?

---

### Post by rsambuca on 2007-12-08
What method have you been trying?  And what system are you running?  ie. 32 or 64 bit?

---

### Post by meborc on 2007-12-08
> **rsambuca said:**
> What method have you been trying?  And what system are you running?  ie. 32 or 64 bit?

that is a very good point - java under 64 has been difficult to get to work (but it is possible)

---

### Post by Royal_Pwner on 2007-12-08
I have been trying to get it to work with firefox.
It says it's installed and everything, but whenever I try to actually use it, it says it's not installed. I'm so confused.

---

### Post by rsambuca on 2007-12-08
We are trying to help you, but you are not giving us enough information to do so, nor are you answering our questions.

---

### Post by Royal_Pwner on 2007-12-08
Sorry.
I'm on 32-bit and my restricted stuff is enabled.
I don't know what's wrong.

---

### Post by rsambuca on 2007-12-08
Again, what method(s) have you tried to install it?  And can you post the output of the following command:  uname -m

---

### Post by Royal_Pwner on 2007-12-08
I've been using the manual method. The only method I know of.
And it says i686.

---

### Post by rsambuca on 2007-12-08
Installing packages manually in Ubuntu is really a last resort kind of thing.  I would just use the regular method first, although it may not work now because of your fiddling around.  First activate your Multiverse repositories.  Go to System - Administration - Software Sources.  Ensure that you have all of the boxes checked.

Then open a terminal and enter:

sudo apt-get install ubuntu-restricted-extras

That will install Java, Flash, and a bunch of codecs that you need.

---

### Post by Royal_Pwner on 2007-12-08
You = basically the most awesome person ever.
It worked.

---

### Post by rsambuca on 2007-12-08
Good stuff!  I would recommend trying not to install anything manually unless you really have to.  Try searching in the Synaptic Package Manager first (System - Adminstration - Synaptic Package Manager).  You will find 20,000+ packages in there that you can install with the click of a button.  It will install your desired program, plus take care of all of the dependencies for you.

---

### Post by Royal_Pwner on 2007-12-08
I tried that, but it said manual only.
Also, I have this now. I'm not sure what to do.
[IMG]http://i223.photobucket.com/albums/dd246/RoyalPwner_bucket/problem.png[/IMG]

---

### Post by rsambuca on 2007-12-08
> **Royal_Pwner said:**
> I tried that, but it said manual only.
Also, I have this now. I'm not sure what to do.
[IMG]http://i223.photobucket.com/albums/dd246/RoyalPwner_bucket/problem.png[/IMG]

Press OK (you may have to use the tab or arrow keys, I can't remember which).  The msttcorefonts are the standard MS fonts like times and arial.

---

### Post by Royal_Pwner on 2007-12-08
But do I need to take action about that like downloading the file it mentioned?

Btw, you're really helpful.

---

### Post by rsambuca on 2007-12-08
I don't remember doing it, but I just checked Synaptic and I do have it installed, so I obviously did install that package at some point.

---

### Post by Royal_Pwner on 2007-12-08
Well, I'll install it later if I need it, I guess.
How would one go about getting it?
sudo apt-get install x-ttcidfont-conf

right?

---

### Post by rsambuca on 2007-12-08
Yup.  Or select it in the Synaptic Package Manager and press Apply, if you prefer a GUI.

---

### Post by Royal_Pwner on 2007-12-08
Thanks.

---

