---
title: "Copy (as in Copy / Paste) isn't working..."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Cirrocco on 2007-06-20
Hi all,

when I select text and hit CTRL-C (or Edit -> Copy) it's not actually copying my selection.

for example: I will copy the above sentence and paste it here:
Å¸Å¸ 

I've installed glipper to see if it was copy or paste that was broken - and it seems to be Copy, because that crap I pasted above appears on the clipboard.

anyone see this before?  know how to fix it?

muchly appreciated.

Resolution:
removed xubuntu-desktop

---

### Post by LaRoza on 2007-06-20
If you close the application you are copying from, it won't copy.

If you want an easier way to copy, highlight what you want to copy, and then middle click where you want to paste. This works in browsers, the terminal, and other apps.

---

### Post by Cirrocco on 2007-06-20
now that's interesting.  highlight and middle click works.   Thank you.

*ahem* however...I didn't close the parent application.  as you see all I tried to do was CTRL-c some text in the post I was writing and CRTL-v it on the line below.

and that didn't and still doesn't work.
I'll do it again for good measure:
Å¸Å¸ 
see?  broken.

any ideas on that?
(I'm a big user of the left hand on my keyboard while mousing around.)

---

### Post by Cirrocco on 2007-06-20
incedentally: reseting the keyboard layout did nothing.
I've been looking for the keyboard shortcut reset function (exist?) but can't find it.

---

### Post by LaRoza on 2007-06-20
What happens if you right click and select copy and then right click and select paste? If this works, it could just be the application, or the keyboard.

---

### Post by molly_001 on 2007-06-20
Use Alt + E , followed by Alt + P , for pasting in most Gnome apps.

---

### Post by Cirrocco on 2007-06-20
no, ALT-E doesn't work either

and yes, i've tried Right-click->Copy, as well as Edit->Copy.

this isn't just text either.
I can't Copy and Paste files either - I can only drag and drop.

what the heck is going on?

---

### Post by Cirrocco on 2007-06-20
This is no longer a problem for me

sudo aptitude remove xubuntu-desktop
followed by a reboot

fixed.

I don't know why having Xubuntu was a problem - but it was the last thing I installed...

bug?

---

### Post by Cirrocco on 2007-06-20
I was too quick to blame Xubuntu...my bad.

my Copy functions start working the moment I turn off my Windows XP VirtualBox.

---

### Post by justtech on 2007-07-21
I'm having the same problem.  Feisty Fawn, P4 3.2ghz 2gb Ram.  Everything works fine for quite a while then it's almost like the "Clipboard" fills up.  I don't have a clipboard installed but maybe I should.

---

### Post by GV1pJTHl on 2007-07-24
> **Cirrocco said:**
> my Copy functions start working the moment I turn off my Windows XP VirtualBox.
My problem as well, thanks for posting. Was curious why the Bidirectional Clipboard function was not enabled by default in VirtualBox.

---

### Post by zerohalo on 2007-07-31
I was experiencing the exact same problem and it was driving me nuts. Thanks for posting the solution-- also solved it for me.

---

### Post by sfenton on 2007-12-06
I too was having the problem with Virtualbox and 7.10 Ubuntu. I just paused the Virtual box XP session and it works. I resumed the Virtualbox and it stopped working again.

---

