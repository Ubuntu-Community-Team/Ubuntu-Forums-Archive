---
title: "bash script to calculate F@H unit completion time?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by brodiepearce on 2007-05-30
Hello,

I'm pretty new to bash scripting, the only work I've done in it is making minor adjustments and adaptations to pre-existing scripts.  One thing I have noticed about the console F@H client is that it does not display, nor output an estimated work unit completion time.  Nor can I find any scripts that will do so (correct me/link me if I'm wrong).

So, basically, what is needed (I think), is something that can cut various values from the FAHlog.txt file and manipulate them to perform calculations, then output a time.

E.g. 
[QUOTE=FAHlog.txt]
[08:44:34] Writing local files
[[color=red]08:44:34[/color]] Completed 172867 out of 4000000 steps  ([color=red]4[/color]%)
[09:23:05] Writing local files
[[color=red]09:23:05[/color]] Completed 200000 out of 4000000 steps  ([color=red]5[/color]%)
[/QUOTE]

For example, to calculate the estimated **average** completion time for this particular work unit, we would use the values highlighted in red (or alternately you could use the steps completed instead of the percentage):

So,  'Completion Time' = (100% - 5%) x (09:23:05 - 08:44:34)

That is, the remaining steps to be completed, multiplied by the time taken to complete one step.  Obviously the 'maths' involved is piss easy (though you would need a work around for the hr:min:sec. time format), I just have no idea how to put this into a script.  The problem is that the FAHlog.txt file is constantly updating, so you'd need to configure this thing to take the bottom most line and second line above it.  

I don't know how to use the 'cut' command or how to make a script perform calculations, this is why I need help mainly.  I can easily get it to output an arbitrary value using the 'echo' command going on other examples of scripts.  I'm hoping someone familiar with F@H reads this, otherwise a lot of it might seem like gobble-de-gook.  ;)

*edit*
A friend on IRC helped me out heaps and made a smallish perl script to calculate the remaining time.

---

