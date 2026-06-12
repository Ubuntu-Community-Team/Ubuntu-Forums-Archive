---
title: "Windows wont install on NTFS 195GB partition"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-19
Okay soo iv decided to go back to windows ... 
but since i have COMPLETTLY destroyed my hdd and installed Ubuntu on it ( no dual boot ) now i cnat install windows 
because its not a NTFS file or w.e  .. but rather ext3 or somthing like that

so i searched around and learned about gpart ... i installed it .. 
but sadly it didnt work .. why ? .. well it just said " scanning for devices " for ever and never opened .. 

so i did the alternative ... downladed the gpard live cd .. 
went into the hdd .. 
 .. there was 3 partition .. donno why 

ext3 (ubuntu )
swap ubuntu .. 
expanded ( donno what this is but just ignored it ) 

so i made a new partion and formated to NTFS file  ... which is 195 GB ... 

when i put the windows vista bassic vista cd .. go threw the set up .. 
and when the partition selection comes ... 

this is what it says for my 3 paritions 

ext3- This is not a NTFS partition .. windows cant install here ( understandable ) 
ext3 - im guessing this is the swap partition .. ... and it ALso had the same error masg as the other ext3 

then i have my 195 GB  NSTF File 
the error i get is 
"windows is unable to find system volum that meets its criteria for installation ... "

okay soo i dont know waht the hell that means .. and im really stuck ... 

theres an ss of me tryna mount ubuntu to the 195 gb so i can try to RE CREATE another partition and try agian .. but i get that error masg ... 


"

---

### Post by GuitarRocker2562 on 2008-04-19
Can't you format you drive with vista?

---

### Post by nicedude on 2008-04-20
This is most likely occuring because it doesn't like the way Gparted Live CD formated the NTFS partition and won't use it, LOL Vista rocks. But to go back to being helpful if I can contain myself long enough, The way I understand your situation is that there are no files you need to keep on this HDD if thats the case just download Dban boot-n-nuke (you can just google that and find easy) its only a few megabytes I think, then burn the iso to a disk and stick that in your machine and boot, when the text based menu comes up just follow the directions and set the settings for 1 pass with zero's - no verify and it will not take that long once you start it before you have a blank hard drive which Vista will install to. I have had this problem with messed up hard drives and XP many times and boot-n-nuke has never let me down in 100's of uses. By the way thats not Linux's fault as take a Vista HDD and see if Ubuntu install disk will just delete partitions off of that because I am sure it will.

---

### Post by anewguy on 2008-04-20
If you're installing Vista from scratch, why not just run gparted from the LiveCd and REMOVE all partitions?  That way it looks like a blank disk for Windows.

---

### Post by indiecast on 2008-04-20
1. Vista is a curse to the world. But I respect your descisions.

2. 

windows doesn't like partitions formatted by gparted for windows

since you want to replace ubuntu, simply use the vista installer to delete all partitions on ur HDD and reformat the entire HDD to NTFS.  this should hopefully solve all of your installation problems...the ones you will encounter with vista will me much worse tho


3. some vista stuff:

a.  when you start having major problems, look up the UAC, or User Account Control.  my dad has vista and it's been kicking his butt since the very beginning.

b.  
waste
of
system
resources


...thats just my opinion though, if you have success, i'd like to know as i am willing to change my opinions. hope this helps,

indiecast

---

### Post by indiecast on 2008-04-20
> **anewguy said:**
> If you're installing Vista from scratch, why not just run gparted from the LiveCd and REMOVE all partitions?  That way it looks like a blank disk for Windows.



you should be able to do this from the windows installation disc

---

