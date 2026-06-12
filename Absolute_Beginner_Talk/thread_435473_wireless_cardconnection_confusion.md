---
title: "wireless card/connection confusion"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Warhawk224 on 2007-05-06
Hi, I'm brand new to using ubuntu and linux in general, but I wanted to try it on my laptop. I got it to start up and run, but when I tried to configure my internet I got stuck. What I tried was opening the System and then Administration pulldowns where I found Network and networking tools. I looked at network and inside I found three options wireless, wired and modem. I wanted to do wireless, so I clicke on it, went into properties took off roaming mode and input my network name and password. After that I clicked the ok button and back on the other window clicked the checkmark box. Then I got out of the network window and ried firefox, but it didn't work, so I went to the documentation page and got confused there because it refers to the System > Administration > Networking window, which I couldn't find, and it talks about an enable this connection button.
What am I missing or what should I be trying to do to get my wireless connection to work?

Thanks

---

### Post by jargoman on 2007-05-07
System > Administration > network
it should say roaming mode enabled under wireless. 
or you should be able to highlight wireless then click properties then 
enable roaming checkmark

if you can't then...

what type of wireless card do you have?

Applications > Accessories > terminal
what's the result of typing (then your password) 

$ sudo ifconfig 

most cards don't work out of the box and you need to install windows drivers using ndiswrapper.
this is because the drivers are copyright and no open source drivers are available.

I can tell you more if I know your wireless cards name and model #

If this is unavailable then the name and the model of your computer

---

### Post by jargoman on 2007-05-07
I'll check this page tomorrow as it's now 2 am.

---

