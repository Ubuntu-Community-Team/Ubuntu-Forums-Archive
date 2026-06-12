---
title: "I'm new, need a few questions answered please."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by luke949 on 2007-04-11
Hi guys, im a newbie at the linux OS. Anyways, I just installed Ubunto 6.10 and I was wondering what things i should install for my hardware, like drivers and things. Here are my specs:

CPU: AMD Athlon 2800+
Video card: Nvida Geforce 5600
Sound Card: Sound Audigy 2
Memory: 512mb

btw I cannot hear anything from the speakers, so I searched for my sound card drivers for linux, but I had no luck.

so, should i keep searching for linux drivers? or should i be going at a different approach with linux? 

Thanks a ton.

---

### Post by jem7v on 2007-04-11
I'd install the proprietary NVidia drivers for your Geforce instead of the open-source ones, because you'll get better performance.  Instructions for that here: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

As for sound, it might actually be muted.  That would be the first thing to check!  (And make sure it's plugged into the right jack... those Audigies have lots of inputs and outputs!)  You can look in two places to see if it's muted or turned on...

1. Applications>Sound and Video>Volume Control
Go into Edit: Preferences and check off all the controls related to your speakers, then check if any of them are turned all the way down or muted.

2. System>Preferences>Sound
Just muck around with it and see if your card is even selected by default.  I know that if you also have an integrated onboard sound card (on your motherboard) it might have selected that card by default, and then all you have to do is tell it which card to use.
(I have an Audigy too, and it works fine without searching for extra drivers... the only time it didn't work was when I forgot to disable my onboard sound and Ubuntu decided to use it instead of the Audigy.)


P.S. This isn't really about drivers, but you should probably also install the restricted media codecs so you can read and watch most digital media...
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) tells you how.
P.P.S And Swiftfox is my browser of choice because it seems slightly faster than Firefox.
P.P.P.S. When searching for programs for Ubuntu, first enable all your software repositories (System>Administration>Software Sources, enable Universe and Multiverse) and then go through Applications>Add/Remove to find programs before you download and install things from the web.  The software in the Add/Remove list is secure and safe, whereas you never know with programs downloaded from some Joe Blow's website.  (Also, it's just so EASY to use the Add/Remove list!)

---

### Post by luke949 on 2007-04-11
so i wouldnt need to install any drivers for my sound card? ubuntu would automatically detect it? 

btw thanks for the video card help

---

### Post by j002 on 2007-04-11
Look here about 2/3rds the way down :

[https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html](https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html)

---

### Post by jem7v on 2007-04-11
No, you shouldn't have to install anything for your sound card.  Just make sure it's not muted and make sure Ubuntu is using your Audigy instead of any onboard sound your computer might have.  (Also, I edited my original post to include more advice.)

---

### Post by luke949 on 2007-04-11
Ok I went to system > Preferences > Sound. And none of the drop down menus have sound audigy in them.

---

### Post by jem7v on 2007-04-11
Not even under the Sounds tab of it? Because for some reason, that's the tab where you choose your sound card (rather than the Devices tab).

What options ARE there in the bottom drop-down (the Default Sound Card one) on the Sounds tab?

---

### Post by lamalex on 2007-04-12
try installing this program "asoundconf-gtk" it will show up under system > preference as default sound card, you may also want to run 'lspci' in the terminal and see if your audigy is being picked up at all.

---

### Post by luke949 on 2007-04-12
Well, I went to sounds tab and i went to the drop down menu and there voila, there was Audigy 2. I selected it and now I can listen to youtube videos!! thanks a lot for the help.

Although I am having trouble installing the proprietary NVidia drivers you linked me to. I followed it through and I went all the way through to the last step and pressed ctrl+alt+backspace a it just brings me back to the login window.
Any clue?

---

### Post by jem7v on 2007-04-12
Ctrl+Alt+Backspace is Supposed to restart your X server and bring you to the login window! If the driver was broken you probably wouldn't get to there at all!

Try this to see if your 3d rendering is working now:
```
glxinfo | grep rendering
```
If it's working, it should say "direct rendering: Yes"

---

### Post by luke949 on 2007-04-12
direct rendering: Yes
 thats a good thing, right?

---

### Post by jem7v on 2007-04-12
Yeah, that means the proprietary driver is working.

---

### Post by luke949 on 2007-04-12
awesome thanks a lot for your help!

now to install wine >.>

---

### Post by jem7v on 2007-04-12
Oh, by the way.  You'll need to reinstall that NVidia driver any time you get a kernel or "restricted module" update in the update manager.  Update the stuff, eh?  And then reinstall the NVidia driver.  Or else things can get weird.

---

### Post by luke949 on 2007-04-12
oh ok thanks for the heads up!

---

### Post by luke949 on 2007-04-12
Hi again, well I encountered another problem, I can't seem to get my microphone to work. It is connected to my Audigy 2 sound card and I even tested it with the Sound Recorder application.

Any ideas as to why it's not working?
thanks.

---

### Post by jem7v on 2007-04-12
Did you go to Applications>Sound & Video>Volume Control, and go to the Capture tab?  Go into the Edit>Preferences there and make sure Microphone Capture is checked off, and maybe the Mic Boost +20dB.  That's the first place I'd suggest checking.

---

### Post by luke949 on 2007-04-12
I don't have the application Volume Control under Applications>Sound & Video>Volume Control.

wierd

---

### Post by jem7v on 2007-04-12
Right-click on your Applications menu and choose Edit Menus.  Go into the Sound & Video subsection and enable that menu entry.

---

