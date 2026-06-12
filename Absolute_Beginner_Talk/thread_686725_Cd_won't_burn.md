---
title: "Cd won't burn"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-02-03
When trying to burn, I keep getting the message "Reload a blank CD in the drive" but there already is. In fact it shows on the desktop as a blank CD. The the DVD RW drive works faultlessly in XP with the same CDs (Infinity 80min/730mb) and yes, the amount of data (718mb) is less than the capacity of the disk (730mb).

---

### Post by mmb1 on 2008-02-03
Despite the fact that it shows up as a blank disc, have you tried using another?

---

### Post by MarkX on 2008-02-03
> **mmb1 said:**
> Despite the fact that it shows up as a blank disc, have you tried using another?

Yes, I even opened a new pack of the same Infinity CDs, same non-result. I have used these with XP for years without a single problem.

---

### Post by mmb1 on 2008-02-03
Sorry, I've got no clue, but I'll bump this to see if you can some help from someone with a bit more expertise than I.

---

### Post by spiderbatdad on 2008-02-03
serpentine has several bugs related to burning dvd's. I realize you are trying to burn a cd with a dvd player. I had the same problem when I temporarily inserted a dvd drive into my machine and tried to burn a cd...Nautilus didn't work either. Maybe give Brasero a try. apparently actively developed, well maintained, and supported by the Ubuntu community.

---

### Post by MarkX on 2008-02-03
Ok, thanks everyone for responding so far.
I ended up having to waste a DVD (which burned OK) for something that should have been burnt to a very common make of CD.

 It's a pretty bad state when the default burner in Ubuntu won't work properly.

---

### Post by jan quark on 2008-02-03
try the burning application k3b it is the best I have used so far
it can be installed with

```
sudo apt-get install k3b
```

---

### Post by MarkX on 2008-02-03
> **jan quark said:**
> try the burning application k3b it is the best I have used so far
it can be installed with

```
sudo apt-get install k3b
```

Thanks for your help but: 
A) I thought anything beginning with "K" is only for use with KDE, not Gnome.
B) I avoid the command line as much as possible on principle because any OS that requires it is forever doomed to a tiny niche.

---

### Post by MarkX on 2008-02-03
Ugh... can anyone recommend a CD/DVD burning app that actually works, for Gnome, from the add-remove menu, please?
Should I remove Serpentine before I install a new burning app?

---

### Post by spiderbatdad on 2008-02-03
you can navigate to it... System>>Administration>>Synaptic Package Manager. I like to use the Search filter, as there are so many packages! Search k3b and bingo. Many kde apps run just fine in gnome. BTW. what's really sad is when someone gets awesome software, featuring the highest level of user customization available, for FREE and still complains that the software isn't good enough. Ubuntu isn't trying to compete for any niche. It is in a class all it's own.

---

### Post by MarkX on 2008-02-03
> **spiderbatdad said:**
> you can navigate to it... System>>Administration>>Synaptic Package Manager. I like to use the Search filter, as there are so many packages! Search k3b and bingo. Many kde apps run just fine in gnome. BTW. what's really sad is when someone gets awesome software, featuring the highest level of user customization available, for FREE and still complains that the software isn't good enough. Ubuntu isn't trying to compete for any niche. It is in a class all it's own.

Thanks for the above...but there's too much vagueness in "many KDE apps run just fine in Gnome", because there is no certainty that k3b actually does.
I won't argue with you about where Ubuntu "is", I don't need "awesome software with high levels of user customisation" I just want solid simple apps where fundamentals like CD/DVD burning actually work, life's too short.

---

### Post by spiderbatdad on 2008-02-03
I hear you. Linux may not be what you're looking for, unfortunately. As long as hardware is manufactured for use with proprietary drivers,  providing no support to open source,  Linux faces challenges and limitations. There are very few printers that work easily with Linux.  With Mac, there used to be only a few webcams that would work...You could try running OSX on your Windows pc and see what happens...(just kidding, of course.) Anyway, best of luck to you. There are computers designed and built for linux, IBM even makes a few. Asus EEE...and so on.

---

### Post by MarkX on 2008-02-03
> **spiderbatdad said:**
> I hear you. Linux may not be what you're looking for, unfortunately. As long as hardware is manufactured for use with proprietary drivers,  providing no support to open source,  Linux faces challenges and limitations. There are very few printers that work easily with Linux.  With Mac, there used to be only a few webcams that would work...You could try running OSX on your Windows pc and see what happens...(just kidding, of course.) Anyway, best of luck to you. There are computers designed and built for linux, IBM even makes a few. Asus EEE...and so on.

I've heard all the arguments, it's hardly surprising they didn't write drivers for something that needs a command line to maintain in everyday use, because such an OS will never make it to the ordinary household desktop. Proper GUI is only just starting to happen in Linux, no thanks to the keyboard afficionados who have held it back for decades.


 Anyway, all I need right now is something that actually works with  DVD/CD writers, most of which don't need proprietory drivers. What about Gnomebaker? Anyone tried it?

---

### Post by spiderbatdad on 2008-02-03
You haven't tried anything that has been offered. Why keep asking? Jan would not have suggested k3b if it didn't work in gnome. try gnomebaker if you want...or are you waiting to have someone else to bitch to when it doesn't do what you want. My final recommendation is to stop your annoying whining. What an infantile personality. Whaaaaa this doesn't work...whaaaaa that's not supposed to work...whaaaaa whaaaaaa.  To bad you can't return it to the store you bought it from.....You got it for free.

---

### Post by papuccino1 on 2008-02-03
> **MarkX said:**
> I've heard all the arguments, it's hardly surprising they didn't write drivers for something that needs a command line to maintain in everyday use, because such an OS will never make it to the ordinary household desktop. Proper GUI is only just starting to happen in Linux, no thanks to the keyboard afficionados who have held it back for decades.


 Anyway, all I need right now is something that actually works with  DVD/CD writers, most of which don't need proprietory drivers. What about Gnomebaker? Anyone tried it?



Well, unlike my roid'd out friend here I'll help ya out. 

First off, use K3b seriously. It's as easy as it gets, and it works. Try it out burning a CD, if doesn't work, then I give you another name. 


And as mentioned earlier so many KDE programs work under Gnome you'll be hard pressed to find some that don't.

Let me know how the burning went.

---

### Post by Roger Cook on 2008-02-03
I have the same problem, the way I have to do it is to wait until it flags for a new CD then open the drawer and insert a new cd when ir closes it does a read and works fine, Just a thought

---

### Post by MarkX on 2008-02-04
> **spiderbatdad said:**
> You haven't tried anything that has been offered. Why keep asking? Jan would not have suggested k3b if it didn't work in gnome. try gnomebaker if you want...or are you waiting to have someone else to bitch to when it doesn't do what you want. My final recommendation is to stop your annoying whining. What an infantile personality. Whaaaaa this doesn't work...whaaaaa that's not supposed to work...whaaaaa whaaaaaa.  To bad you can't return it to the store you bought it from.....You got it for free.

Most of it works fine and I'm dying to dump windows completely soon and get others to use Linux, but looking at the amount of posts about CDs/DVDs not burning and the lack of ideas  on how to fix it,  there's obviously something major wrong, don't you think? I've been trying to change over to Linux for about 8 years now on numerous computers and every time I do it first looks promising and then stuff like this happens.

---

### Post by MarkX on 2008-02-04
> **Roger Cook said:**
> I have the same problem, the way I have to do it is to wait until it flags for a new CD then open the drawer and insert a new cd when ir closes it does a read and works fine, Just a thought

Thanks for the suggestion but I did that and no joy.

---

### Post by spiderbatdad on 2008-02-04
Yes but I live with it and enjoy finding ways of fixing the problems. Without that attitude I would have left linux long ago. And have you even tried k3b yet?

---

### Post by orange2k on 2008-02-04
K3b is my favorite burning app, but sometimes I also use Brasero, Gnome Baker or the default no-name burning app in Nautilus.

---

### Post by MarkX on 2008-02-04
> **papuccino1 said:**
> Well, unlike my roid'd out friend here I'll help ya out. 

First off, use K3b seriously. It's as easy as it gets, and it works. Try it out burning a CD, if doesn't work, then I give you another name. 


And as mentioned earlier so many KDE programs work under Gnome you'll be hard pressed to find some that don't.

Let me know how the burning went.

Thanks!
I installed Gnomebaker last night but haven't had a chance to try it yet. If it doesn't work I'll go for K3b.

Serpentine won't remove from the add-remove menu so do I use the synaptic thingy? I'm kind of worried it'll remove or break other stuff.

---

### Post by MarkX on 2008-02-04
Interesting... Gnomebaker reads my CDs as 700mb when they are in fact advertised as 730mb (and I have burnt them close to that on XP).

---

