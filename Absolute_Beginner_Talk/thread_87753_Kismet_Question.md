---
title: "Kismet Question"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by uby on 2005-11-08
First let me say hello to everyone.  This is my first post...currently have just installed Breezy Badger and Kismet.  I have a 2wire wireless card (hermes) it is just like the Orinco Gold card I believe.

I get an error when trying to start kismet.  It says that I need to configure at least one packet source.  I have the kismet.conf file opened and says right in there that I have to change to the source I want use.  What exactly does this mean?

Also I booted with the Auditor CD running Kismet and it doesn't find my wireless card, so I doubt that Breezy Badger will find it.  How do I go about configuring my card for Kismet?

Thanks so much for any replies.

---

### Post by uby on 2005-11-08
Okay, I found out I have to put something there about my network card.  Don't know what yet, so help is still appreciated.

---

### Post by uby on 2005-11-08
Okay, I pretty much have it figured out....but....I need to download a patch for my orinoco driver, so I go to this link: [http://www.kismetwireless.net/code/orinoco-0.13e-rfmon-dragorn3.diff](http://www.kismetwireless.net/code/orinoco-0.13e-rfmon-dragorn3.diff)

It's a bunch of code.  How do I get this downloaded?  Do I need to paste that into something??

---

### Post by uby on 2005-11-08
Nevermind....wget command.  Seems like I figured everything out on my own...I shoud come here more often, it's making me smarter:D

---

### Post by Elitoh on 2005-11-09
well this is my first post too so ill say Hi  too. I actually have a question for Herot. 
What steps did you take to get kismet installed? Im having a hell of a time doing so. 
By steps I mean what Packages or Dependencies. 
Now the answer to your question. 
Im pretty sure the Directory that your looking for is /etc/kismet/ and there's a file there called kismet_drone.conf and kismet.conf. you have to edit both of those files what what ever drivers your using for youre wireless card. 
You'll see where it says source=prism,source,wlan0 or something close to it. You have to customize it to what you have.

---

