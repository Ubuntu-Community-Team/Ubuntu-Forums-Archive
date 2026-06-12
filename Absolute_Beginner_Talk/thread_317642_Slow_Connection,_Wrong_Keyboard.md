---
title: "Slow Connection, Wrong Keyboard"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by klittzzer on 2006-12-12
I have Kubuntu Edgy on my laptop and think it is an excellent OS. I have a couple of issues that I can't seem to resolve, despite spending a fair amount of time looking for answers prior to posting this.

First: I have a 2.4ghz connection with Tiscali UK. I averaged around 300kbps downloads when I was using Windows but never get anything faster than 48kbps from the repositories or (I downloaded Thunderbird from Mozilla to see how fast that went from the net) internet. I have looked at loads of posts here and it seemed that disabling ivp6 in Aliases worked for most people so that is what I went ahead and disabled. 

Alas, it hasn't made the slightest bit of difference to my connection speeds.

I have always been helped out when I have posted here and would really appreciate any ideas or nudges in the right direction to solve this dilemma.

Second(and last): My keyboard layout (UK) was recognised in Ubuntu no probs. When I installed the KDE meta package, however, it reverted to US, which is a little awkward. I have had to put up with it before on an old Mac I had years ago but I shouldn't really have to these days should I?

I have tried booting into Gnome, system>preferences>keyboard> then 'add', selecting UK and ticking the box, but when I boot back into KDE, US key layout again.

eg when I want an '@', if I press shift and the key with '@' symbol I get     "

 


Again, any advice will be received with thanks. 


Peace all

Klittzzer

---

### Post by seijuro on 2006-12-12
If you go to "system settings" from your K menu and choose Regional & Accessibility there is an option there to enable keyboard layouts perhaps this might be what you are looking for. It's my understanding that disabling IPv6 in KDE is to speed up Konqueror I could be wrong on that. However as for Mozilla personally I use Swiftfox it runs considerably faster.

---

### Post by klittzzer on 2006-12-12
Thanks for the reply seijuro. I have found the keyboard bit, changed it, yet it appears to be the same. I will spend more time on it. Probably missed something knowing me.
As for speed thing. Thanks also for little bit of knowledge. I did notice that Konqueror was a bit faster after disabling ipv6 so you must be right. I can live with web pages taking a few secs to load; what I am trying to resolve is the download rate from the repositories. I get 49kbps max. Windows used to give me an average of 225kbps on a download from eg source forge or some such a site. I have read that it may be the repositories being in great demand. Is that so? What speeds do you get (if you are still about), or anyone else?
If the 49kbps max is all anyone else gets I will end my mission now. If, however, I am an exception, I will persist.

Thanks again seijuro for your time.

Peace Rules

Klittzzer

---

### Post by seijuro on 2006-12-12
Yeah they are under pretty heavy load when I installed Kubuntu it was like the second day dapper was out and the max speed I got from the repos that day was like 24kbps on a 10mbps cable line at a friend's house. Check some other places that normally run fast if it's only the repos that are slow its probably load issues. Something else you might look into if they Regional thing doesn't work is edit the xorg.conf file in /etc/X11
look for this section and see if the model and Layout match your hardware.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

```

I currently only have dialup at home so I average about 4-6kbps

---

### Post by klittzzer on 2006-12-13
Yeah, thanks seijuro, i reckon it must be the repositories, I can live with what I have I reckon. I am sorry I have been a while I have been out all day. I managed to sort out the keyboard thanks to your advice. I am getting the hang of this OS slowly. I like the way that it works having to input stuff to get things working. I can see how windows kind of detaches the user and creates an air of mystery that undermines the credibility of open source software, like 'it can't be any good 'cos it doesn't cost loads of money' if you get me. I am right glad I gave this a try. 

Take it easy

Peace Rules

klittzzer

---

