---
title: "[SOLVED] Dual Monitor - Change menu appearing time on separate X screen HELP!"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by lobo-tuerto on 2008-01-09
Hello guys,


I recently installed Ubuntu on my laptop, I have a dual monitor setup, all working great as separated X screens.

The problem is that in one of the desktops whenever a click a menu or navigate one, the little window that hold the menu items seems to take a little bit more time to appear than in the other X screen.

I think there is something you can configure to change the menu appearing time, but I have been looking around and no luck yet.

Can anyone help with this issue? Thanks in advance.


Regards,
Adrián.


P.S. Yes this is a [duplicated post]("http://ubuntuforums.org/showthread.php?t=661875"), but I asked someone to move it to this thread with no luck on my part.

---

### Post by lian1238 on 2008-01-09
I'm not sure if you experiencing the fading effect? If so, run ccsm, System->Preferences->Advanced Desktop Effect Settings in the screen with the slow menu. Go to Animations, then the Open Animation tab and delete the line with "Fade 150 (type=Menu | ... etc".
Hope that helped. :)

---

### Post by lobo-tuerto on 2008-01-09
I tried your solution, but it only accelerated the fade effect, not the "appearing speed" of the menus or windows.

It's really strange because in the second X screen I'm not having this problem. And before I had a dual screen system set up, I wasn't experiencing this problem. :(

I think it is has to do, with the "render speed" of the windows in that screen, anyone knows anything about changing this?

---

### Post by lian1238 on 2008-01-10
I have never used a dual monitor system before, except on my laptop so I don't know how it works exactly. Can you try turning off each one and try using only one X screen?

---

### Post by fenian on 2008-01-10
I had this problem and I fixed it by following these instructions...

>  Originally Posted by [gtaluvit  ]("http://ubuntuforums.org/showthread.php?p=3426504#post3426504")
...
If I run compiz delayed 5 seconds as a session startup (and have it only replace my main screen), then I have compiz running on my main, and metacity on the secondary. Both seem to work fine without any menu issues.

So, I would suggest the following script to add to your session:

Code:

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &



---

### Post by lobo-tuerto on 2008-01-10
@lian1238: Well, I have a laptop too :)

@fenian: Thanks for your answer, but where exactly should I put that script in? I only have like 2 weeks using Ubuntu.

---

### Post by lobo-tuerto on 2008-01-10
> **AstalaVista said:**
> Based on TB2 idea of running separate instance of compiz for each screen, I saw a tip here on how to do that:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/comments/11)

Thus, this simple script works for me (add into Sessions> Startup Programs):

```
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

```

So, dual screen compiz, no more pop-up menu lag.
:guitar:

Seems like this is right fix for it, but how do you integrate that script with 3 commands to your Sessions -> Startup programs? when you add a new one, it only lets you write 1 line. Any help will be appreciated.


Regards,
Adrián.

---

### Post by lian1238 on 2008-01-10
You need to save the commands into a file with the extension .sh (e.g menulagfix.sh) (start the name with a dot to hide the file, Ctrl+H to show hidden files) and then right-click the file->properties, go to permissions tab then check "Allow executing file as program". This is the same as the command "chmod +x filename". You can test the script by running it; Alt+F2 and drag the file in. If that fixes your problem, you can run it on startup. You can now put it in sessions->startup programs. Just browse to the file, wherever you've kept it.

---

### Post by lobo-tuerto on 2008-01-10
Thanks for the instructions man, I will try it out, I will report back the results ;)

---

### Post by lobo-tuerto on 2008-01-10
It worked like a charm!

No more delays in any of my 2 monitors, thanks a lot guys :D
:popcorn:

---

### Post by lian1238 on 2008-01-11
Great! You should mark this thread as solved then. :)

---

### Post by lobo-tuerto on 2008-01-11
How do you do that?

I edited the title, but the new one isn't appearing when I see the topic in the thread list :(

---

### Post by Tteddo on 2008-01-11
It's under Thread Tools>>Mark This Thread as Solved

Cheers!

---

