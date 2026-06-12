---
title: "iphone 3GS - un-brick if stuck in recovery mode"
date: 2010-10-02
forum: Apple Hardware Users
---

### Post by brendanpiater on 2010-10-02
Morning All,

Just had some success restoring an iphone 3GS I managed to brick yesterday. Thought I'd share how to.

What you need:
Dual-boot to Windows (not all of the following applies then) or in my case...

Virtualbox (3.1.8-61349~Ubuntu~lucid - what I'm running)
Windows XP virtual machine (should work with Windows 7 too, but not tested)

So basically I ended up with a phone in "recovery mode" but it would not be seen by iTunes so I could not restore it or get it out of recovery mode.

I did the following:

1) Get Virtualbox ready to "see" your iphone and pass this through to your Windows VM.

I followed these instructions, as I had Virtualbox installed already I just had to do step 3, which is *critically* important.

[http://www.brighthub.com/hubfolio/matthew-casperson/articles/77025.aspx](http://www.brighthub.com/hubfolio/matthew-casperson/articles/77025.aspx)


2) Get the phone into a very raw update state, think it's called DFU state by following these instructions:
[http://www.youtube.com/watch?v=DOtq7M14zoE](http://www.youtube.com/watch?v=DOtq7M14zoE)

During this process, itunes will see the phone and ask if you want to recover it (it may take awhile for itunes to see the phone, took about 5 mins for me). 

3) Follow itunes instructions (takes about 15-20 mins to do it's thing)

Done! Happy days :)

Now I can give my mates phone back unharmed... *wipes sweat off brow* 

PS - if you get a 1601 error, check this out and try again

[http://support.apple.com/kb/TA38633?viewlocale=en_US](http://support.apple.com/kb/TA38633?viewlocale=en_US)

---

