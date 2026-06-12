---
title: "Strange behavior in SCIM and Input method in Gutsy. Pls help!"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-12-29
Hi everyone.

I'm having a strange issue with my keyboard in Gutsy.  

My settings are:

Catalan Keyboard

And SCIM configuration to insert Korean alphabet when required (pressing a special combination)  in my case is SHIFT + SPACE  

Then, pressing CONTROL + ALT + SPACE   I return back to the normal settings (Catalan Keyboard)




But my problem is, that sometimes when I create a new folder in my desktop I can't write anything to change the name of that folder. I try typing but the cursor doesn't move...    

Then, in some programs like pidgin, I'm witting and it doesn't work. I have to right click in the witting area and choose INPUT METHOD and default is selected (not working), so I change it to SCIM Input Method and it works...    (but this happens only sometimes, not always)

Is really wired, but really annoying as well...   every time I have to change the input method in pidgin and other programs in order to write...  Then I can't rename folders in nautilus...


Anybody can tell me what this is??

Thank you in advance.  behaivor

---

### Post by Kosimo on 2007-12-29
Bump!  :(

---

### Post by CA_Warren on 2008-03-16
Rarely encouraging to find a 3-month old post on your problem that went unsolved...

Did anyone figure this out? I have the same issue:

Installed SCIM to get Chinese character input support, and programs now sporadically choose different input methods (i.e., 'X Input Method'), so that I have to right-click and change them back to 'Default' input method for the keyboard to work in that program.

What's more, it happens inconsistently - one minute a program will be letting me type just fine, the next the keyboard won't work in it. It's especially frustrating with programs such as FreeMind or the Konsole, since there is no right-click menu option to change input methods - I simply have to close the program.

Has anyone else had this issue, or have any ideas as to what may be going wrong? What info can I supply here that would make it easier for us to diagnose the issue?

Thanks in advance.


Kubuntu "Gutsy Gibbon" (fully updated)
SCIM 1.4.7
Compaq Presario x1000 / 1.3GHz Intel Centrino

---

### Post by Kosimo on 2008-03-16
> **CA_Warren said:**
> Rarely encouraging to find a 3-month old post on your problem that went unsolved...

Did anyone figure this out? I have the same issue:

Installed SCIM to get Chinese character input support, and programs now sporadically choose different input methods (i.e., 'X Input Method'), so that I have to right-click and change them back to 'Default' input method for the keyboard to work in that program.

What's more, it happens inconsistently - one minute a program will be letting me type just fine, the next the keyboard won't work in it. It's especially frustrating with programs such as FreeMind or the Konsole, since there is no right-click menu option to change input methods - I simply have to close the program.

Has anyone else had this issue, or have any ideas as to what may be going wrong? What info can I supply here that would make it easier for us to diagnose the issue?

Thanks in advance.


Kubuntu "Gutsy Gibbon" (fully updated)
SCIM 1.4.7
Compaq Presario x1000 / 1.3GHz Intel Centrino

As you see you're not alone on here, I'm having the same issue than you...

I Hope that in Hardy with a complete redesign input method panel will work better.

---

### Post by joe1212 on 2008-03-24
I am having the same issue when I configured SCIM for Japanese input. Randomly programs will not accept keystrokes and I have to right click the input box and change the input method from "X Input Method" to either Default or "SCIM Input Method". Does anyone have a quick fix or hack for this?

---

### Post by experience on 2008-03-31
I have the same problem too. And it's a little more weird, in freemind i can input text at first, then suddenly, I can't key in any text including english characters.

---

### Post by bopomofo on 2008-04-01
> **Kosimo said:**
> Hi everyone.

I'm having a strange issue with my keyboard in Gutsy.  

SCIM ...

But my problem is, that sometimes when I create a new folder in my desktop I can't write anything to change the name of that folder. I try typing but the cursor doesn't move...    


I have the same problem. If you observe the same behavior, open up a Terminal and type:

```
killall nautilus
```

My desktop lags for a few seconds after this while the Nautilus process restarts, but it fixes the problem you describe. Temporarily.

The problem seems to be due to some conflict between SCIM and GNOME/Nautilus. In addition, if I Iose the ability to type in, say, Firefox, I have to close all instances of FIrefox before I can type again.

---

### Post by drkjstr on 2008-04-08
> programs now sporadically choose different input methods (i.e., 'X Input Method'), so that I have to right-click and change them back to 'Default' input method for the keyboard to work in that program.

What's more, it happens inconsistently - one minute a program will be letting me type just fine, the next the keyboard won't work in it. It's especially frustrating with programs such as FreeMind or the Konsole, since there is no right-click menu option to change input methods - I simply have to close the program.


> if I lose the ability to type in, say, Firefox, I have to close all instances of Firefox before I can type again.

Both of these apply to myself. I have been just dealing with the right click workaround for nautilus, gprename, and others that allow it. It would be nice to have some kind of feedback on the issue being reviewed. It's tolerable, but still a hassle. Any other ideas?

---

### Post by ezphilosophy on 2008-04-11
[This]("http://ubuntuforums.org/showpost.php?p=3676161&postcount=6") should work for you.  Hope it helps!

---

### Post by drkjstr on 2008-04-13
That seems to have done the trick. I'll be sure to let you know otherwise.

---

### Post by daninkorea_ on 2008-04-23
> **ezphilosophy said:**
> [This]("http://ubuntuforums.org/showpost.php?p=3676161&postcount=6") should work for you.  Hope it helps!

That worked for me for that session, but now when I try to start up scim I get this message:

********@ubuntu:~$ scim -d
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.
********@ubuntu:~$ 

:(

---

### Post by tigerchan on 2008-05-03
Hope it works. And thanks. 
By the way, it seems that the scim-bridge has been replaced by scim-bridge-client-gtk or scim-bridge-client-qt, in the Hardy release at least.

---

### Post by Kosimo on 2008-05-04
Hello guys.

I'm in Hardy and SCIM problem is half fixed.
Now, I can switch between Korean and Catalan keyboard and it works practically everywhere. The only problem I'm having is inside Nautilus. You know, when clicking in some folder and then start typing a name to find exactly the folder you're looking for?  In some instances my keyboard doesn't works there, so, even if I type any letter doesn't do anything. 

Isn't a big issue but annoying....

---

