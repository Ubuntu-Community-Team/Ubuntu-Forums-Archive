---
title: "[SOLVED] could not update help me!!!!!!!!!1"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by vinu76jsr on 2007-08-14
hi all
I desperately need ur help 
my synaptec packege manager did't work
I use feisty fawn and I m behind my college proxy
I hav all the settings fine and can browse through internet with mozilla
but whenever I tried synaptic it simply didn't do anything after I click install 
I hav checked all the repositories
it's OK if I could get the manual update 
but here lies the problem whenever I tried it
by writing
 
*sudo apt-get update in the terminal *

it shows error message like this

[I]
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
[/I]
I m counting on your response 
please help me!!!!!!!!!11

---

### Post by bwtranch on 2007-08-14
Try gedit /var/lib/dpkg/status

look for the bad entry, delete and save. Should work now.

---

### Post by vinu76jsr on 2007-08-14
well
 thanks for ur response 
I hav done what u suggest
and then also no luck 
it simply didn't work
I hav removed entries where status says 

purge ok not-installed

most of them were language packs
I want to mention that I skipped installation of language packs
maybe it'll help u to figure out the problem

---

### Post by vinu76jsr on 2007-08-14
hi I followed it again
and it works 
lots of thanks

---

### Post by Gnub_Daemon on 2007-08-14
also make sure that when you run update from terminal, you do not have any other package/update manager running at the same time.  That always gets me when I try to download/install something from terminal and, say, adept or synaptic is running.

---

