---
title: "no flash player 8 for linux?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by iblastoff on 2006-06-13
so im building a website and it uses a tiny sprinkle of flash. i was working in windows and decided to boot to ubuntu just to see how it looks in linux. and to my dismay, none of the flash shows up! this was weird because sites like youtube with flash videos work just fine. i use macromedia flash 8 so im guessing by default it publishes them in the 'newest' (re: 9 months old now) format. so i went hunting for some version of flash player 8 for linux and there isnt one at all? 

is there a specific party working on porting flash player 8? if someone can point me towards a flash 8 for linux dev blog or something so i can know when things will hit linux that would be helpful. thank you

---

### Post by rbalfour on 2006-06-13
> 
 Flash Player 8 for Linux update
Emmy Huang, Product Manager of the Flash Player, explains what the plans concerning the Linux version of Flash Player 8 are. Instead of releasing a 8.0 version we will directly move to 8.5 on Linux. This will avoid even more delay after we ship Flash Player 8.5 for Windows and Mac. That will also make sure that the new virtual machine works using gcc from start. I see that as a big benefit as gcc is a more strict and standards compliant compiler than Visual Studio or CodeWarrior.

We have a few very good engineers working on the Linux version right now in parallel to the work we do for 8.5. 64bit versions will take a little longer, there are no definite plans just yet. Just recompiling will not work unlike what you might think. The main issue here is the x86 JIT in the virtual machine and the mark&sweep garbage collection which are not 64bit aware right now, work on 32bit pointers only. Adding and testing this is not a small task as anyone who ever worked on this type of low level infrastructure might be able to attest. I can really only ask for patience here, we are aware that we need to offer a solution as soon as possible.


Update

---

### Post by uzi09 on 2006-06-13
if you'd like, go to this website:
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

scroll down to the table, and you'll see what the latest relases are for each OS.

---

### Post by iblastoff on 2006-06-13
thank you! i guess i'll stick to publishing in flash 7 for now.

---

