---
title: "How do I enable illuminated keyboard on Ubuntu?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by zyberican on 2007-11-08
Hi everyone!
I purchased a logisys kb608bk illuminated keyboard. Using XP it lights up. The light switch is also the Scroll Lock key. I'm using Ubuntu 7.10 and it won't illuminate. 
I have  KVM Switch which also uses the Scroll Lock to switch between the two computer, the KVM Switch works but the illuminate doesn't. 

I'm wondering if I'm out of luck or if there's something I can do to permanently enable my keyboard to illuminate when I press the Scroll Lock button?

Any help is greatly appreciated!!!
Thanks in advance!8-)

---

### Post by jordanmthomas on 2007-11-08
[https://answers.launchpad.net/ubuntu/+question/7456](https://answers.launchpad.net/ubuntu/+question/7456)
Not sure how helpful this will be, but it's all I could find.

If your scroll lock button doesn't work at all this might help.  If it already works as a scroll lock button, the link probably won't be of much use.

---

### Post by kvonb on 2007-11-08
-

---

### Post by Robocoastie on 2007-11-08
you need a Linux friendly one (IOW one that doesn't need software drivers) like the [Saitek Eclipse]("http://www.saitekusa.com/USA/prod/eclipse.htm") that one indicates that the LED's are merely a mechanical device and even adjustable on the keyboard.

---

### Post by zyberican on 2007-11-08
Thanks guys for the help but .....

jordanmthomas -- on the link u posted I'm the guy with the name "El Boricua"

kvonb ---- when I used Windows I did not need to install any drivers, it looks like it's hardware but there's a way to do this without modding the keyboard for more info see the link provided by jordan. 

What's on the link provided by jodan works but I can't seem to make it permanent. 

Robocoastie --- thanks for the reply but I believe there's another option to just buying a new keyboard!
-------------------------------------
On the link Jordan provided I'm the guy on the last reply by the name El Boricua, the fix on the link works but once I reboot I have to do it all over again. 
I did what the guy said in order to make it permanent but still not working so I'm wondering what I'm doing wrong so that's why I posted the question on Launchpad but since no one there replied yet, I thought ppl in this forum may know the answer!

Again, thank you guys for the help.
Any help is much appreciated!

---

### Post by Butthead on 2007-11-08
Hi Zyberican,

If you ever do get this figured out, please let me know, okay?

I have the same keyboard (plus the same no illumination issue :( ) as you.

I'd really appreciate it! :guitar:

---

### Post by kvonb on 2007-11-08
_-_

---

### Post by zyberican on 2007-11-08
Kvond...

When I look in my root folder there's no file named: .Xmodmap like the guy in launchpad says, he says  that if the file is not there to create it but I'm not sure if this file is just a text file with the following info in it: 

xmodmap: up to 3 keys per modifier, (keycodes in parentheses):

shift Shift_L (0x32), Shift_R (0x3e)
lock Caps_Lock (0x42)
control Control_L (0x25), Control_R (0x6d)
mod1 Alt_L (0x40), Alt_L (0x7d), Meta_L (0x9c)
mod2 Num_Lock (0x4d)
mod3 Scroll_Lock (0x4e)
mod4 Super_L (0x7f), Hyper_L (0x80)
mod5 Mode_switch (0x5d), ISO_Level3_Shift (0x7c)

or not?
When I go to the root folder I make sure that "Show Hidden Files" is on
I also go into the root folder as root. 

I tried creating a text file named: .Xmodmap and put the info above in it, save, I restart the PC and the same problem!

---

### Post by kvonb on 2007-11-09
-

---

### Post by zyberican on 2007-11-09
kvonb ---- 
Thanks a million for these easy to understand instructions!

I will try them today and let u all know the outcome!!! :)

---

### Post by Niniel on 2007-11-09
Btw, don't by the Saitek Eclipse.
At least not if you play games that require the keyboard. But heavy typing will yield the same results, it may just take a little longer

I have one, and it looks great at night, but the keys are coated, and after a while, the coating will wear off (ASD keys wend first). Saitek was very nice and replaced my initial keyboard, but of course that doesn't really help with this design flaw. The board as such is fine, so I keep using it, but it won't look pretty for too long (about 6 months in my case).

---

### Post by sliPrix on 2008-01-23
> **zyberican said:**
> Kvond...

When I look in my root folder there's no file named: .Xmodmap like the guy in launchpad says, he says  that if the file is not there to create it but I'm not sure if this file is just a text file with the following info in it: 

xmodmap: up to 3 keys per modifier, (keycodes in parentheses):

shift Shift_L (0x32), Shift_R (0x3e)
lock Caps_Lock (0x42)
control Control_L (0x25), Control_R (0x6d)
mod1 Alt_L (0x40), Alt_L (0x7d), Meta_L (0x9c)
mod2 Num_Lock (0x4d)
mod3 Scroll_Lock (0x4e)
mod4 Super_L (0x7f), Hyper_L (0x80)
mod5 Mode_switch (0x5d), ISO_Level3_Shift (0x7c)

or not?
When I go to the root folder I make sure that "Show Hidden Files" is on
I also go into the root folder as root. 

I tried creating a text file named: .Xmodmap and put the info above in it, save, I restart the PC and the same problem!

I am having the same problem.  I have created the file named .Xmodmap using gedit with the sudo command.  Could someone please show me exactly what the file needs to look like?  I'm not sure what exactly needs go into the file.

---

### Post by sliPrix on 2008-01-24
Ok so I figured it out but I don't know if this is a great solution so if its bad, let me know.  First off I'm on Gusty (7.10).  I took the idea of adding the command ```
xmodmap -pm
``` to see if I had any mod spots open and it so happens I had mod3 open.  So what I did instead of making a file called .Xmodmap, I just added a script to the startup sessions.  What I did was System > Prefrences > Sessions > Click "Add" 

Then I edited the following:

Name: xmodmap-start
Command: xmodmap -e 'add mod3 = Scroll_Lock'
Comment: Starts Xmodmap (Scroll_Lock)

Obviously if your mod3 isn't open, and another one is, replace mod3 with whichever mod is open in the "Command:" portion.   I hope this helps.

---

