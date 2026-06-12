---
title: "Initial boot goes to the &quot;question folder&quot;"
date: 2013-04-06
forum: Apple Hardware Users
---

### Post by matthewvandertie on 2013-04-06
Hello, this is my first time entering the ubuntu world and my first post on this forum. I just installed ubuntu 12.10 on a Macbook 1,1 as a single OS. However, every time I start the laptop it goes to the "question folder" if I don't hold down alt and select windows. I am confused why it still does this even though there is no other OS on this laptop but ubuntu. Is there a way to change the initial boot sequence to automatically start by booting ubuntu?

Thanks for any help!

---

### Post by BenTin2 on 2013-04-06
I had this problem too, but on a desktop G5 - I was able to do a quickie fix of just changing (physically) which SATA chain my hd was on, but whilst poking around I ran into evidence of editing... whatever the initial boot script is (not xorg.conf), you may just need to edit one line of text in it to point it at the correct drive. There are others out there with this prob - wish I could help more, but don't despair yet ;)

---

### Post by BenTin2 on 2013-04-06
ok, sorry, I may have confused things - my G5 stuff uses "open firmware" which I think serves to confuse things a bit... dunno about your (intel?) architectured Macbook. If you want a really really simple thing to try, try installing 12.04 instead :)  Otherwise, wait for someone to reply that actually knows what the heck they're talking about (oops); but in the meantime, here's a little primer if you actually want to know what's going down. Or, not going. 

**[http://manpages.ubuntu.com/manpages/precise/en/man7/boot.7.html](http://manpages.ubuntu.com/manpages/precise/en/man7/boot.7.html)**

---

### Post by matthewvandertie on 2013-04-06
I will look into that primer and get more up to speed! Thanks for the help, it's not a huge deal to have to always use alt to boot up. It just is a hastle if i forget to hold alt down during booting because it brings me to the folder with a question mark and I have to restart..... but yea thanks for attempt!

---

### Post by matthewvandertie on 2013-04-12
After further analysis, I can now boot directlly into Ubuntu 12.10 with no problems. However, when I restart my computer, the folder with a question mark pops up and then the screen turns black. This wouldn't be a problem if some program downloads and upgrades require the system to be restarted. I am confused as to why manually shutting it off and on works perfectly but using restart results in the black screen described above?

Thanks again!

---

