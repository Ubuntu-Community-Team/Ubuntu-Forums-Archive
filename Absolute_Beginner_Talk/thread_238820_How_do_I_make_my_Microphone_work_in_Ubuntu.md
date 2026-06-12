---
title: "How do I make my Microphone work in Ubuntu?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-08-18
Hello all!

I have never bothered to work on making my Ubuntu Microphone really work...

Now it is time to go on & work on that too!

I have booted in Windows & made sure that the Microphone works!

So, that means that the wire is connected on the correct jack of my Tower...


From the Ubuntu Menu, when I select "**Applications\Sound & Video\Sound Recorder**", I am attempting to create a Recording, but when I decide to listen to my recording, nothing comes out from the Speakers...

I have also checked the "alsamixer" settings from the Terminal & it seems that the Microphone is activated!

Any ideas, on how I can fix this?


Thanks.

P.S.> Is there anything else I need to activate inside the "alsamixer"?

---

### Post by encompass on 2006-08-18
It could be your card in linux uses a different jack... look out for that one... it had me stumped for days... lots of ac97's do that.
As for you mike... press tab to see the capture settings... and yank'em up for now... then try to do a recording... make sure the mix is on full and that you mic boost is lit up.  I thing you press space bar to light them.
Hope this helps.

---

### Post by xpod on 2006-08-18
Have you tried just double clicking your volume icon and making sure your microphone is activated under the "capture" tab??

Is that the same thing as the settings via "alsamixer" in terminal???

Just a thought

EDIT:Sorry,just realised it`s the same thing(learn something new eveyday)

---

### Post by dvarsam on 2006-08-18
Hello again!

Thanks for your replies!

After your suggestions & a little "digging" from my side (to try to find out what is going on), I did the folowing:

1. Made sure that inside "**alsamixer**", my microphone is activated.

2. From the Menu, select "**Applications\Sound & Video\Sound Recorder**"

3. From the Menu, select "**File\Open Volume Control**"

4. Click on "**Capture**" Tab

5. Activate all options under "**Line-in**", "**Microphone**" & "**Capture**".


After changing these (too!), now the "**Sound Recorder**" seems to be working fine!!!


Thanks again!

P.S.> I am not sure which exact steps made it work correctly... Maybe in the Future I will look in it more closely...
Now I am just happy that it works!

---

### Post by ajesh on 2006-08-27
I think I know which one of your steps worked. 

I had the same problem and I had everything turned on except Capture. 

Once I saw your posting and enabled "capture", then I could start recording from my microphone.

What threw me off is that I did not know that there was a separate capture option to be enabled. I thought I just had to enable my microphone in the capture tab...apparently not. You will have to enable capture and it should show on your capture tab in the volume control.

---

### Post by RichPicker on 2007-01-18
I have done all those things, but still hear only Hiss when I record.:(

---

### Post by dvarsam on 2007-01-19
Hello!

[QUOTE=RichPicker]I have done all those things, but still hear only Hiss when I record.:([/QUOTE]

Is your microphone plugged in the right jack of your PC?
i.e. did you plug the microphone's chord/wire on the correct jack of your Mobo?

Good Luck!

---

### Post by monocongo on 2007-02-25
I also can't get my microphone to work.  I have made a little progress in that I can now hear something through my headphones when I talk through the microphone, and I can record myself when I use the sound recorder application.  However I can't record my voice when I use the Skype test call, and this is the only reason I need a microphone.

Any further suggestions will be appreciated, thanks in advance.

---

### Post by dvarsam on 2007-02-26
[QUOTE=monocongo]I also can't get my microphone to work.  I have made a little progress in that I can now hear something through my headphones when I talk through the microphone, and I can record myself when I use the sound recorder application.  However I can't record my voice when I use the Skype test call, and this is the only reason I need a microphone.

Any further suggestions will be appreciated, thanks in advance.[/QUOTE]

You probably have purchased a new Mobo!
And that Mobo includes the Intel HDA drivers...
Check your manual to verify that...

You might have to compile the Audio Drivers

---

### Post by monocongo on 2007-02-26
I resolved this problem by removing my ~/.Skype directory after Skype crashed on me (and it refused to stay up when I started it again, complaining about my audio device being misconfigured).  Once I did that and then restarted Skype my troubles were over and my microphone works now.

---

### Post by RichPicker on 2007-05-03
What was that about installing Drivers?

I had my mic working with Edgy, but not yet with Feisty. I have the mic plugged in, nothing is muted, capture is at max. I'm not sure what's going on. The only irregular thing is the Bad Device massages I get when I start kmix. I'm grasping at straws at this point. Haven't had the mic working since an Edgy update, and not since installing Feisty - maybe one month now. When I record my voice with Audacity, I hear static, and just barely my voice.   I'm puzzled.

Help.... ;-)

---

