---
title: "[SOLVED] Can't play DVD"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2008-02-14
When i first insert a dvd into my drive totem pops up as usual but now its saying Could Not Read From Resource



what should i do?

try vlc...


then if i try to play it from there it just doesnt play



What do i do?







thanks

---

### Post by hyper_ch on 2008-02-14
next time please use a desriptive thread title and not a generic "need help" one.

---

### Post by khensucat on 2008-02-14
Firstly, is it only the one DVD? Does it also do this in Windows or another OS?

This may be a failing DVD drive. Can you clarify a little bit?

---

### Post by erginemr on 2008-02-14
> **hyper_ch said:**
> next time please use a desriptive thread title and not a generic "need help" one.

With no offense intended, I have noticed several times that you do not reply any threads with generic titles except with a warning, but are generally very helpful to other posters. I am wondering if this is a principle that you have taken?..

P.S. Unfortunately as far as I know, once you set the title, there is no way to change it.

---

### Post by Gigidy5 on 2008-02-14
It has been just fine and then like three hours ago it just ceased. i played dvds all the time using vlc.

Iv'e tried rebooting and reinstalling...
how do i update vlc?

thanks for your help
greatly appreciated



and to hyper
i did use a descriptive topic but it went unanswered, or even looked at for an hour so.., HELP!

---

### Post by khensucat on 2008-02-14
Ok. Has it ceased to play all optical media, or a specific (or a few specific) ones?

Have you installed VLC, and want to *update* it to the newest release, or are you wanting to *install* it for the first time?

And have you been able to try the DVD drive in another operating system (if that's an option?)

You said you "even tried re-installing", so I'm guessing the DVD drive works with CD's?

The more info you can provide, the better people can help you ;-)

---

### Post by Gigidy5 on 2008-02-14
1. i dont use cds very much


2.I have vlc installed and would just like to know the terminal lingo to update it


3. no other system except for ps2 and.... the dvd works in it

---

### Post by khensucat on 2008-02-14
Here is a good page that has information on tar, ./configure, make, and make install, the commands you'll use to compile and install the newest vlc from source, if the vlc version in Ubuntu isn't cutting it for you for some reason:

[http://fosswire.com/2007/09/20/unix-fundamentals-compiling-software-from-scratch/](http://fosswire.com/2007/09/20/unix-fundamentals-compiling-software-from-scratch/)

---

### Post by hyper_ch on 2008-02-14
> **erginemr said:**
> With no offense intended, I have noticed several times that you do not reply any threads with generic titles except with a warning, but are generally very helpful to other posters. I am wondering if this is a principle that you have taken?..

I just think it is not a good habit to write "noob here, need help". If you apply Kant's categorical imperative to this behaviour the result would be that every thread would be labelled like that. So if you want to help, you'll have to blindly go through each one without knowing anything about its content.

There are just things you don't know and when you see that, then you can skip that one and help others. In the end it's also time of those who are inclined to help that is wasted by such threads and I think that's not something that should be encouraged.

---

### Post by erginemr on 2008-02-14
> **hyper_ch said:**
> I just think it is not a good habit to write "noob here, need help". If you apply Kant's categorical imperative to this behaviour the result would be that every thread would be labelled like that. So if you want to help, you'll have to blindly go through each one without knowing anything about its content.

There are just things you don't know and when you see that, then you can skip that one and help others. In the end it's also time of those who are inclined to help that is wasted by such threads and I think that's not something that should be encouraged.

I understand... And respect your decision.

---

### Post by erginemr on 2008-02-14
> **Gigidy5 said:**
> 1. i dont use cds very much
2.I have vlc installed and would just like to know the terminal lingo to update it
3. no other system except for ps2 and.... the dvd works in it

Before messing up with installing source packages, I assume you have installed gstreamer multimedia plugins and the "libdvdcss2" package:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by erginemr on 2008-02-14
When you install the package "libdvdread3" from Synaptic, an installer has been extracted to your system: /usr/share/doc/libdvdread3/install-css.sh

You can also try running that script from a terminal to see if this puts an end to your troubles:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Perfect Storm on 2008-02-14
Title changed.

---

### Post by Gigidy5 on 2008-02-14
You erginemr are a genius thank you.

sorry hyper and A.I

---

### Post by erginemr on 2008-02-14
Thank you very much, I am honored. :oops:

But how exactly did you solve it, so that other users who will visit this thread later may benefit? And also, could you please mark your thread as SOLVED from the Thread Tools manu on top of this page?

---

### Post by samol on 2008-02-23
You can also try running that script from a terminal to see if this puts an end to your troubles:
Code:
sudo /usr/share/doc/libdvdread3/install-css.sh


I already had libdvdread3 installed but dvd's wouldn't play. 
I ran the above code and  dvd's now play. 
PROBLEM SOLVED for me....Thank you.:)

---

