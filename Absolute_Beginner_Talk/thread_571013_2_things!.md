---
title: "2 things!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by k3lt01 on 2007-10-08
Hi

Well maybe 3 things:) 1st I really like Ubuntu and would consider a total move to Linux for all my PCs if I can resolve a few minor but still niggly issues.

I have just installed Fiesty to my laptop and after 3 attempts with a new install each time I have net access with my IPN2220 wireless card. It took some time but I got ndiswrapper to work as the instructions say it should.

So to my 2nd point. Ubuntu isn't consistent with recognition of my wireless card. I got it running for the 1st time last night updated Ubuntu, had a chat to a mate over  Gaim (I like that program alot :) ) surfed the net for a little while and then turned my laptop off. Woke up this morning, started the laptop up and no wireless available, it didn't even recognise my card. Been working with ndiswrapper for about an hour, doing "sudo ifup wlan0" and get varying responses like no card and ignoring device. So what do I do to make this consistent? I need net access for work and my laptop goes everywhere with me.

Now to my 3rd thing. While installing some software last night and after updating Ubuntu I got a message saying /usr is 100% full. Now I cant install any more software. Checked the disk usage analyser and it says /usr is only 54.3% full at 1.7GB. When I installed Ubuntu I made my /usr folder 5GB so 1.7GB is not 54.3%. Does anyone have any idea what might be going on here? I need to install more software for work, and also more for my own personal interest, so I need it to be able to take more.

I am somewhat confused with these things so I would appreciate it if someone who has come across similar issues could give me a work around to correct them.

Thanks in advance.
Michael.

---

### Post by bobplano on 2007-10-08
well have you tried adding the module so it loads up at boot? i think the command is 
```
sudo ndiswrapper -m
```

also see what ndiswrapper -l says (that's an L not a one)

---

### Post by k3lt01 on 2007-10-08
Yes to both things, I get "module configuration already contains alias directive" to sudo ndiswrapper -m and to sudo ndiswrapper -l I get
neti2220 : driver installed
        device (17FE:2220) present

---

