---
title: "Normal bootup time?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-01-18
Hello. 

I have an AMD Athlon 2500+ xp (1,833 ghz), with 512 mb ram. I dual boot Windows XP and Ubuntu 6.06 LTS at two separate hard drives. The ubuntu drive is a hd of only 8 gb (and relatively old), while XP runs in a 16 gb partition of a 120 gb drive. I have optimised ubuntu using the k7 kernel, but it still takes me about 1,5 minutes to boot up, while the boot sequence in XP is much faster (40 seconds?). Both my OS are quite clean installs with just a little extra software.

My questions are: Is this normal? Should it take that much longer to boot up Ubuntu, or could this be a hard drive issue? Does Ubuntu normally boot up about as fast as XP, or is what I am experiencing normal?

But still, I only keep XP for my Lexmark 1100. Can`t make the scanner work under Ubuntu.


Hallvor

---

### Post by slimdog360 on 2007-01-18
The k7 kernel is old and became redundant once the 'generic' kernel came into place. That 40 seconds for Windows, is that from the time you press the power button to when you are able to use it after waiting for everything to laod up?

My Ubuntu takes a bit over a minute from power till when Im able to use it after everything has loaded.

---

### Post by jd65pl on 2007-01-18
Check the speeds of the two drives. In my experience Linux is quicker to boot that windows. 
You wont see any advantage by using the K7 kernel over the generic one. Try searching the forum for your scanner, also see the hardware compatibility list in the document storage facility

---

### Post by Hallvor on 2007-01-18
It might be a drive issue, since I expect the old 8 gb drive to be a lot slower. It is from the days when 8 gb for a hard drive was almost unheard of... :) *But how can I check the speed of the drive? The generic kernel - is that the same as !386 or whatever it is called?* 

My printer/scanner/fax is by the way one of those all-in-ones from Lexmark. Have searched the forums but others seem to have the same issues with the scanner. It locks up and make weird noises. Does not work at all.

---

### Post by Rui Pais on 2007-01-18
1,5 min seems a little long for your computer specifications...

Take a look at [bootchart]("http://www.bootchart.org/") that can help you track any problem... Its in repos, i think.

Maybe try to clean a bit the boot services too. Check some [tips here]("http://ubuntuforums.org/showthread.php?t=89491").

good luck.

---

