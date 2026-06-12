---
title: "Poor battery backup and power-mgmt"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-02-26
Hello all
I have 2 problems to discuss, please help:

1. I am using Gutsy amd64 on my laptop.
I have Gutsy installed on my internal HDD and Win XP installed on my external HDD. Whenever I wish to boot to XP, I simply plug in my external HDD during boot-up. While using XP, I get about 3-3.5 hrs of battery backup (9-Cell Li-ion battery). But when I use Gutsy (w/o the external HDD plugged in), I don't get more than 1 hrs 15 mins of backup. Here's a screenshot of my power-mgmt screen:

[http://i29.tinypic.com/2r5rxxw.jpg](http://i29.tinypic.com/2r5rxxw.jpg)

Also, I keep the brightness to the minimum, w/o any apps running, still it won't last more than an hour and 15mins.. 

2. Secondly, I have set my computer to automatically hibernate when battery is critically low. But it does nothing. The laptop stays on until the battery is completely discharged and the power suddenly goes off with a beep sound. Also, I have tried to set it to suspend on low power, but nothing happens.

What do I do? I know that there are some brightness applet related bugs of the power manager. Is this also a bug? Please help me out.

---

### Post by sayakb on 2008-02-26
Bump.

---

### Post by tango_ninja on 2008-02-26
heh you did yourself more harm than help with that bump, now it's not an unanswered thread :p

anyway, i have the same issue and can't seem to figure it out.... people are suggesting everything from monitoring which apps use the most power and making configuration changes to a bad battery (the latter of which I know is not the case).

take a look at this thread [http://ubuntuforums.org/showthread.php?t=707547](http://ubuntuforums.org/showthread.php?t=707547) you might find some of the power monitoring apps useful

---

### Post by sayakb on 2008-02-26
> **tango_ninja said:**
> heh you did yourself more harm than help with that bump, now it's not an unanswered thread :p 

Ouch.. didn't realize :D
Thanks for the link. I would try powertop.. :)

---

### Post by sayakb on 2008-02-26
Powertop gave me this suggestion:

> Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.

What do I do?

---

### Post by sayakb on 2008-02-26
I added this to my /boot/config-2.6.22.14.generic file. Restarted my computer, now battery backup has gone up to 2.2
Now, should I disable geyes and other active applets also?

---

### Post by tango_ninja on 2008-02-26
to be honest i'm having the same problems as you and i haven't solved them yet. i'm no expert on power mgmt in linux.

i would suppose that disabling any additional applets would help your power consumption, but by how much i have no idea. i can't imagine geyes decreasing your battery power by a half hour ;)

maybe someone else can offer some helpful advice?

---

### Post by sayakb on 2008-02-26
> **tango_ninja said:**
> to be honest i'm having the same problems as you and i haven't solved them yet. i'm no expert on power mgmt in linux.

i would suppose that disabling any additional applets would help your power consumption, but by how much i have no idea. i can't imagine geyes decreasing your battery power by a half hour ;)

maybe someone else can offer some helpful advice?

Well, the powertop was showing geyes in the list, so I thought it might be consuming power.. though that really sounds silly ;)

Anyway, thanks for your suggestions. I would be waiting for other opinions to come up (if any, though)

---

