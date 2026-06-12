---
title: "What am I missing? (I need printer networking help)"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by gandalf458 on 2005-10-11
I thought Ubuntu was supposed to be for humans but 3 my postings to date have received not 1 reply. I may be new to Ubuntu and to Linux but I have plenty of experience with Windows and DOS. I have successfully installed Ubuntu direct from the CD on an old PC which I have connected via a VPN router to the Internet. I also have a Windas m/c and a network printer. I'm trying to get Ubuntu to recognise my network prinny without success. I've tried System > Administration > Printing > Global Settings > Detect LAN Printers but it still doesn't recognise my printer. I've tried Add Printer and entered the IP address and selected a generic LaserJet driver, but it seems to assume it's a Postscript printer - which it ain't. I've looked at several other threads and the contortious commands that are required have me quite lost. HP's website is equally confusing regarding Linux printer drivers. Is there some kind soul out there can help a chap in need?

---

### Post by Kapre on 2005-10-11
[QUOTE=gandalf458]I thought Ubuntu was supposed to be for humans but 3 my postings to date have received not 1 reply. I may be new to Ubuntu and to Linux but I have plenty of experience with Windows and DOS. I have successfully installed Ubuntu direct from the CD on an old PC which I have connected via a VPN router to the Internet. I also have a Windas m/c and a network printer. I'm trying to get Ubuntu to recognise my network prinny without success. I've tried System > Administration > Printing > Global Settings > Detect LAN Printers but it still doesn't recognise my printer. I've tried Add Printer and entered the IP address and selected a generic LaserJet driver, but it seems to assume it's a Postscript printer - which it ain't. I've looked at several other threads and the contortious commands that are required have me quite lost. HP's website is equally confusing regarding Linux printer drivers. Is there some kind soul out there can help a chap in need?[/QUOTE]

gandalf458 - Sorry that most of your post have not been answered right away. Maybe it just so happened that no one (who viewed your post) has encountered that kind of a problem. Others may already saw it and is now in the process of trying to solve your problem. Anyways, did you try looking at this [website]("http://www.linuxprinting.org")? Maybe you can find your answer there.

K

---

### Post by gandalf458 on 2005-10-11
K

Thanks, firstly for replying and secondly for the reference website - that should keep me quiet for a while!

G :-)>

---

### Post by wylfing on 2005-10-11
First, some tips for getting responses to your questions: 

(1) Don't write text in one big block. No one is going to bother reading that. Break things up into small paragraphs with whitespace between. It's sooo much easier to read and understand.

(2) Don't use "clever" words like *prinny* and *Windas*.

(3) Don't leave out the relevant specs. For example, we are left to infer that you have an HP printer, but we still have no idea what model. It makes a difference.

(4) *Most importantly*, don't chastise the people on the boards for not helping you as promptly as you'd like. How much did you pay for Ubuntu? How much did you pay for a support contract? I'm guessing zero. We are helping people with their problems on a volunteer basis.

========================================

Now, to the task at hand.

I don't particularly think linuxprinting.org is all that helpful. It was helpful a few years ago, when it was all a black art. But these days, printing to an HP printer should be a piece of cake. It seems like you did the right thing choosing Add Printer and typing in the IP address of the printer. So, some clarifying questions:

* What's the model of your printer?
* Can you print?

---

### Post by gandalf458 on 2005-10-11
Thanks for your tips.

The printer is an HP LaserJet 1022n and no, nothing prints. I've tried a test page and I've tried printing from Firefox.

---

### Post by aysiu on 2005-10-11
[QUOTE=gandalf458]I thought Ubuntu was supposed to be for humans but 3 my postings to date have received not 1 reply.[/quote] I'm missing the logic that says "A distribution for humans must have a free (i.e., volunteer) support system that will answer every single post and do so within two days." I challenge you to find any forum for any OS that has the general responsiveness of the Ubuntu forums. It may not have happened in your case, but I've generally gotten responses here within minutes. I did notice, though, that you posted only three threads--[one](http://www.ubuntuforums.org/showthread.php?t=60269) was answered twice; though, to that one you never responded back saying whether the responses were helpful or not. The other two were both about printing and not very specific.

Generally, when threads aren't answered, there are a number of reasons:

1. No one knows the answer. I don't answer threads about printers (or sound or gaming or a whole host of other things). You know why? Because my printer's always worked. My sound has always worked. And I don't game. Unless you have experience fixing something yourself, it can be difficult to fix it for other people.

2. You post at some unfortunate time when no users are on. Then, it gets lost in the shuffle. It happens. Some moderators, like me, go poking around looking for unanswered threads, but sometimes (because of reason #1) we still can't do much.

3. Your details are too vague.

I think you'll generally find people are helpful here, but please don't take them for granted. We're all volunteers here and other users. We aren't paid support, official support, or anything you should feel entitled to.

---

### Post by gandalf458 on 2005-10-11
I'm sorry if my post sounded like criticism. It was not intended to be - more of a cry for help - hence the subject title. I have also found why I didn't think I was getting responses when in fact - as it appears - I was. I didn't realise the notify by email box wasn't ticked by default. Mea culpa.

---

### Post by aysiu on 2005-10-11
No worries. I hope it all works out in the end.

---

### Post by gandalf458 on 2005-10-12
There seems to be so many options!

I've selected CUPS - is this the right option?

Then the IP address - do I just enter 192.168.1.50 or prefix it with ipp:// or http:// ?

I see someone else had some trouble but got the IP address wrong. He showed his "print configuration file" - how do I view mine?

Thanks

---

### Post by skirkpatrick on 2005-10-12
First let me say that even though I subscribe to a thread that I'm helping out on, it may still be several hours before I get back to the forums to reply so bear with me :)

Okay, is your printer being controlled by your Windows machine or does it have it's own network interface?

---

### Post by snowjunkie on 2005-10-12
I didn't look the model up but check that your HP Printer is not one of those "Windows" printers.  They shift a lot of the processing to the windows OS and therefore are not compatible with Linux (unless you find an experimental driver online).

Of course, you should be able to print to it if you share it from a window's machine.  I do this in fact at home.  I'm sorry I can't provide you with any How-To right now as I'm in work!

---

### Post by gandalf458 on 2005-10-12
I hope it's okay to reply to two messages at once.

The printer is connected to a 4-port VPN router - the 1022n is a network printer - on the Windows m/c the protocol is Raw as opposed to LPR if that means anything.

It's not a Windows only printer (with a bit of mapping I can print to it from a DOS app).

There is reference on the HP website to this model printing from Linux but I don't understand it and there's guy somewhere on Ubuntu forums who seems to have done it. [http://ubuntuforums.org/archive/index.php/t-63804.html]("http://ubuntuforums.org/archive/index.php/t-63804.html")

Thanks guys

---

### Post by wylfing on 2005-10-12
[QUOTE=gandalf458]There seems to be so many options!

I've selected CUPS - is this the right option?
[/QUOTE]

I think you want HP JetDirect.

> 
Then the IP address - do I just enter 192.168.1.50 or prefix it with ipp:// or http:// ?


I'm pretty sure just the IP numbers will do.

---

### Post by skirkpatrick on 2005-10-12
I think wylfing is correct.

---

### Post by gandalf458 on 2005-10-13
Yes! Thank you guys. Seems obvious when I look back but when no option makes sense I tend to choose the default.

The Ubuntu graphic has come out a bit manky when I printed the welcome web page from Firefox but I can play about with different drivers. At least I can print.

Thanks again.

---

### Post by Buggyflayer on 2005-12-08
After much frustration with trying the hpijs, cups, et al I found this thread and my HP1022n works on the LAN with HP Jetdirect too. Hooray!

I had tried modifying the Properties to HP Jetdirect earlier but it didn't work, I had to delete the previous "HP1022" and start from New Printer

Except that Ubuntu Breezy 5.10 tells me in the Print box that the State is "Printing: job-printing" even when its finished. This means I have to manually cancel the job after I've printed every time. Any ideas as to why it's not receiving the finished command from the printer?

Thanks

---

