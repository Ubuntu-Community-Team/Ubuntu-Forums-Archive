---
title: "Graphic Card?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Killer Cop on 2007-10-19
Hi.

I'm fairly new to Ubuntu and I'm very keen on learning more about Ubuntu and help Ubuntu and the community, so it can be a good competition to Windows.

I have tried to install Ubuntu 6.06 before by partitioning 1 harddisk, in 2 with Windows and Ubuntu 6.06. It was going very good with installing Ubuntu, but when I wanted to install the graphics driver I ran into problems. I'm a digital artist so I do need the graphic card to work, and work properly.

I found a thread in these forums where I could download the driver pack but installing it was *very* difficult. I don't know C++, or any other programming language, well alittle PHP and HTML but thats it. For me the instructions was all like chinese text and I did not understand anything at all.

So, I plan to buy a new harddisk for my new computer, so can install Ubuntu on that. But I first want to know if I can install my GeForce 8600GTS graphic card **easy and simple** without messing with coding (can I say, like Windows style?)?

---

### Post by CaptainInsaneO on 2007-10-19
Yes, there's a way.

I'm not sure if the new distro of Ubuntu supports that card right off the bat (probably, but I'm still running Feisty Fawn) but you can use ENVY to install your drivers easily. I've installed both an 8800gts and an 8800gtx using envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

P.S. There's nothing wrong with wanting to do things through a GUI. That's one of the beauties of Linux: there's hundreds of different ways to do something.

---

### Post by Killer Cop on 2007-10-19
Thank you for your reply, I will try installing a new harddisk when I can.

And another thing, you say there is hundreds of ways to do something. But I think that all the normal computer users out in the world either don't have the interest or time to learn any form of code to make something work. The best way for a normal computer user is to navigate through a simple, picture-text GUI interface who anyone can learn to use, and fast, and if the Ubuntu community can qonquer the normal main-stream computer users or a part of it the goal is as good as reached.

---

### Post by Linux_Man on 2007-10-19
The reason why we give instructions generally using the Command Line is because there are so many desktop environments (KDE, GNOME, XFCE) that it would take much longer to explain through the GUI, not to mention that most command line based utilities are more standard (For example, Ubuntu 7.10 would have it and 6.10 would have it and so would say Fedora) The reasons why graphic card drivers must be installed from the CLI is because it must be installed with X (The program that makes the GUI) isn't running. And Graphic Card installations are about the only thing in Ubuntu that needs to be done from the CLI, it just is much easier to type "sudo apt-get install *some program* then to explain how to do it from Synaptic, add-remove programs, aptitude ETC. Hope this helps explain it.

---

### Post by Killer Cop on 2007-10-19
Hmm, I really cant see how it should be more easy, and I had problems with it, and many other have problems I can see.

Wouldn't it be good if there was a small GUI program which made all these CLI commands, like Envy.

I think thats why Windows is so popular as it is, if I need to install a graphics driver, I simply run the .exe file I downloaded and if the computer needs any info the .exe program ask for it through GUI. That's needed to make Ubuntu more popular, I think. And that's why Envy is good it just need to be even more simple..

---

### Post by papuccino1 on 2007-10-19
What he's saying is that there are many diferent distros and only one terminal code. It's easier to have one standard.

---

### Post by Killer Cop on 2007-10-19
Yes, that is absolutely correct. But mainstream computer users don't care about distros, terminals, standards and enviroments or any other technical things.

They need simple friendly point and click interfaces, so they clearly understand what is going on..

---

### Post by lazyart on 2007-10-19
you can point and click your way through synaptic to find the nvidia driver.

I grew up on Commodore 64, TRS-80 and the like and typing commands is just what you did.  Why do some people still prefer to drive a stick shift when automatic transmission has been around for decades?  It's about control.

Even in Windows I prefer to use command line when possible.  It's quicker to hit with Windows key, followed by R, then type calc to launch the calculator app.  Otherwise it's click start, Programs (wait for menu to show), Accessories (wait for menu to show) then click on calculator.  When I'm troubleshooting and such, I drop to CMD as soon as I can. 
Ever try to give a user administrative rights on a Windows machine?  Point and click takes a good 30 seconds to get there. Right click My Computer> Manage>, Users and Groups> Administrators> Add>Enter user name>OK>OK>OK.  From the command line?```
NET LOCALGROUP ADMINISTRATORS /ADD username
``` and it's done.  Point and click is wonderful, and Ubuntu has plenty of it.  The command line is just so developed that you can do *anything* from it that you can in the GUI.  Don't hold that against Linux.  Windows isn't made that way, though Microsoft is adding robustness to the server side command line.
If you want to point and click, by all means, you can do that.  If you want to do it more efficiently, embrace the terminal.

---

### Post by CaptainInsaneO on 2007-10-20
Killer Cop, I wasn't trying to spur a large debate about GUI's vs. CLI. You just made the comment

> But I first want to know if I can install my GeForce 8600GTS graphic card easy and simple without messing with coding (can I say, like Windows style?)?

and I was trying to point out that "Windows style" for most people (and it seems you're in this group) means to use a GUI. Which is absolutely fine, there is no shame in using a GUI. I was commending you on your choice of using a method that works for you, and is familiar (i.e. "Windows style") because TBH, most people using Ubuntu today are former/current Windows users and, like you, want a quick and painless way to do things through a window.

There ARE many ways to do different things. I actually am beginning to prefer the command line more and more in recent months. But that's because it works for me. However, I myself use ENVY on a regular basis and I very enthusiastically recommend it for your needs as well.

Hope this helps clear some things up. :)

P.S. The reason there aren't more "point-and-click" drivers out there is because Linux in general is - for the most part - ignored by the major hardware corporations because it's an open source -read: "Free"- development. Therefore, there's no money to be made. In fact, ATI up until very, very recently ignored the entire Linux community when we were asking for graphic drivers. Now, they're actually coming out with some drivers that are worth something, and what do they have to say for it? They'd rather it "not be (their) fault" that gaming on Linux doesn't take off in the future (source: MaximumPC Holiday 2007 edition, pg. 8). Yeah sure. They probably just got tired of cleaning out their inbox.

---

### Post by aysiu on 2007-12-05
This is how I installed my Nvidia graphics driver--the process was entirely point-and-click:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

