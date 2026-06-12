---
title: "Can I enlarge buffers/swap file"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Vesper007 on 2008-02-12
Hello to all the techies and helpful noobs....I have a concern; 

I've searched for answers using keywords; but nothing really helps me because i'm not sure what i'm doing and how to navigate and manipulate what needs to be done (without a 'paint by numbers system') 

when i launch Banshee or Totem or Mplayer there are times when the audio or video pauses like it's buffering. I am new to Linux and don't know how to find things in files. If i have the option to increase buffers for my audio and video could someone please walk me through this....

also; how do i make sure my Logitech  webcam is able to record..It was suggested (by an error message) that 'Snack" needs to be installed. I've done that, but i'm not sure how to check and ensure it's all set up correctly. 

Thank you in advance for your help.
100% Ubuntu
5% knowledge

---

### Post by ph1 on 2008-02-12
Being a webcam-deprived noob, I'm not sure what 'snack' is supposed to do, but you can learn more about it by checking its man pages.  Type

```
man snack
```

into a terminal window and check out what it says.  Also, quite often Ubuntu requires a reboot after installing new things, especially hardware-related things, so you might want to try that first.

---

### Post by Vesper007 on 2008-02-12
thanks ph1...did as you suggested.  ```
 man snack
```  but received error "no manual entry for Snack"

Any ideas on how to increase buffers or to set up recording from webcam using the built in mic? 

any help here will be muchly appreciated.

I like the Open Source but i feel like i always need to fill out an ID-10-T  form. Windoze was easier and I used it more (looking at files, opening multimedia programs, powerpoint. etc) but now i want to do ALL with Linux. Sometimes i won't post a question because i think others will believe that i've got no business using something i know very little about.  Well, there you have it. Neurotic to the core.

---

### Post by ph1 on 2008-02-19
Vesper007,  

I don't know much about using a webcam or setting the buffers, but you shouldn't be afraid to ask here--sometimes people amaze me because their first post ever is something insanely technically advanced!  One of the reasons people choose Ubuntu is that the community is helpful and welcoming of newcomers.  (We were all newcomers once, unless you're Linus and invented Linux....)  

As far as resolving your problem (if it persists), the best I can do is to refer you to other threads, which may or may not be helpful:
[on getting a webcam to work]("http://ubuntuforums.org/showthread.php?t=560462");
[on video errors from a webcam]("http://ubuntuforums.org/showthread.php?t=134938").

---

### Post by stevescripts on 2008-02-19
This probably wont help you with your problem, but just so you know,
Snack is a *very* capable audio toolkit:  [http://www.speech.kth.se/snack/](http://www.speech.kth.se/snack/)

I have used it in a couple of applications.

---

### Post by Vesper007 on 2008-02-20
Thanks *stevescripts* for your link to SNACK homepage.  Haven't time to read it yet, but will this week and I will try some of the coding.

I'll play in the sandbox for  a while and see what sticks. is there diagnostics (like ***'Hijack This'  or similar ****)* that can be run and posted on forums to be previewed by someone smart to tell me what belongs and what does not?  - -

Q. can i load my drivers for logitech onto a Linux system and get it's own GUI like the one i use to see on windoze?

---

### Post by stevescripts on 2008-02-20
> **Vesper007 said:**
> Thanks *stevescripts* for your link to SNACK homepage.  Haven't time to read it yet, but will this week and I will try some of the coding.

You are welcome, my pleasure! ;)
> 
I'll play in the sandbox for  a while and see what sticks. is there diagnostics (like ***'Hijack This'  or similar ****)* that can be run and posted on forums to be previewed by someone smart to tell me what belongs and what does not?  - -

I don't have a clue what Hijack This is ... not really sure what you want to diagnose, but there are many tools available on a Linux box.
> 
Q. can i load my drivers for logitech onto a Linux system and get it's own GUI like the one i use to see on windoze?
Windows drivers would be useless.  If there is an application that came with your logitech device, you could try running it under wine.

Your original problem, sounds like possibly network interruptions in the audio/video streams ... Other than that I cannot speculate.

If you are at all interested in coding audio applications, Snack is a great tool.

You can download a very simple mp3 player, created using tcl/tk and Snack from my website [http://www.stevescripts.com/software/tsp](http://www.stevescripts.com/software/tsp)

tsp (Tiny Sound Player) is just a little Snack demo hack that I put up a while back
while working on a larger project.  tsp.tcl, is the simple tcl script that puts
the Snack package to work.

tsp is a starpack, that is, a single file executable, that contains tcl/tk, Snack 
(and some other sutff) that *should* just run on any Linux box, whether or
not tcl/tk and Snack are installed. (Of course, if you already have tcl, tk and
Snack, just grab the little tcl file ;) )

tsp.exe is the same thing (a single file executable) for windows, just in case anybody is interested. (By the way, the windows binary was created on a Linux box)

Hope you find this useful.

Steve

---

