---
title: "Changing CPU/Slowing Down Dosemu"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jamiehendrich on 2007-09-18
I really need some help here.  I removed Windows and have  put on Edgy Eft.  I am working with dosemu and my computer is running too fast to get into my program.  I should have purchased a computer that is running at 1.80 or 2 GHz but I didn't.  Mine is 3-something or other.  Water under the bridge.  I cannot afford a new computer. It was suggested that I  type sudo gedit /etc/dosemu/dosemu.conf and remove the hash mark in front of the CPU speed and change the speed to 66.0 which I have done.  Also, I changed the hogthrehold to "0" instead of "1" and removed that hashmark.  My computer is still running too fast and does not allow me to get into my old program.    Does anyone have any other suggestions on how to slow my computer down and change the speed of dosemu?     I would be really appreciative of any  assistance.  And since I know nothing about computers, please do so in a simplified fashion.  

Jamie

---

### Post by kelnage on 2007-09-18
Instead of using dosemu, you could consider trying [DosBox]("http://dosbox.sourceforge.net/") instead. Apparently, it actually emulates an old computer - including the processor, so everything is slowed down.

---

### Post by jamiehendrich on 2007-09-18
[B][/B  Thank you very much for responding.  However, it has to be dosemu.  I don't know the details because I am not familiar with computers.  I just know that with my software it has to be set up with dosemu.  Sure wish someone could tell me how to configure my Dell computer and slow it down from 3 MGhz to 1.8-2 maybe with a software comparable to slo-mo but one that works with edgy.  Thanks anyway.   It does not have cpu scaling but surely there is another way. 

Jamie

---

### Post by jamiehendrich on 2007-09-19
I mean Ghz in the above message,  not Mhz.  See how little I know about computers.

---

### Post by kelnage on 2007-09-19
Okay, one thing I need to know is your CPU type. Who made it? Is it Intel, AMD or otherwise?

If the processor supports changing the speed, you could probably use "powernowd". This should allow you to change the speed of your processor, but unfortunately, I've no experience of using it.

It's website can be found here: [http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html)

---

### Post by jamiehendrich on 2007-09-20
Hi again, UK.

It's intel, not  AMD -- which would have been the better course from what I have been instructed -- and  unfortunately it does not have cpu scaling capabilities.  I was advised yesterday by a software guru  that there is no Linux product that will slow it down.  I wish I could go into the "sudo gedit" and configure it differently, but someone would have to tell me how.   think I'm out of luck unfortunately.  Gosh, the thought of buying two more new computers because of my foolish error of purchasing a 3+ Ghz when I could have purchased 1.8 G to 2 Ghz originally  is  not a pleasant thought.  Oh, well.   Live and learn......the hard way naturally.    If you think of anything else that  will work, please advise.  I really appreciate your input.

Jamie

---

### Post by jamillikan on 2007-09-21
You have been told repeated your software will NOT function with the processor you have running at the frequency it does.  Accept it and MOVE ON!

Joe

---

### Post by jamiehendrich on 2007-09-25
Well, good morning, Joseph,  my own personal Edgy Eft expert.  Of course you've told me repeatedly that it won't work...if you call "twice" repeatedly.    However, is there anything wrong with getting a second opinion from all of the "other" computer experts out in the world?   You, of all people, surely are not intimating that you "know everything," are you?  

And just for the record, I have.................finally......... accepted your advice and purchased  two new computers...as you know.

I have moved on except for the following (which I'm working on but it's slow going):

A.  We can go to the moon but we cannot tell a computer to slow down.  I am really having difficulty accepting that concept.  I'm really struggling with it...even though I know nothing about computers....which I will concede.  

B.  Now I'm out all of this money.  

 
Jamie

PS  American Heritage College Dictionary:  "Patient"  1.  Bearing  or enduring pain, difficulty, provocation or ANNOYANCE  with calmness," Joseph!

PS/PS  I guess if I have to move on, sobeit.  

PS/PS/PS  Hope you have a glorious fall day.

PS/PS/PS/PS  I cannot believe you saw the post.  You need to stay off the internet.:):):)

---

### Post by jamiehendrich on 2007-09-26
This thread has run its course and should be closed.    Joseph Millikan is obviously correct that nothing will work to slow down the computer within my very specialized software.  He should know.   He was instrumental in developing same.     It would appear I should strive to  become a better listener.   My apologies for wasting everyone's time.    

Jamie

---

### Post by aBitLater on 2008-02-27
I happened to run across this thread while researching a key repeat issue in dosemu (w/ freedos).  First, I admit I'm certainly no expert, so this may not be helpful at all.  Second, I don't know what software package you're talking about... but,,,

can you run a looping program in DOS that USES the CPU and keeps it busy for an amount of time?  If this is at all possible, it would perhaps have to be incorporated by the author of the software... 

Even if that is possible, it's not elegant :)

---

