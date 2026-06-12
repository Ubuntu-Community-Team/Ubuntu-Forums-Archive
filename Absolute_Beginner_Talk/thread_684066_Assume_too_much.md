---
title: "Assume too much"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by edoepke on 2008-01-31
I am an absolute beginner and I installed Ubuntu for the first time. I am using an nVidia gForce 6200 video card. My 32" flat panel monitor only has DVI, Component, composite and svga inputs. I have spent the last three days reading and browsing everywhere for help on installing the driver on my system. I can output to Component video using an adapter and that's all.  My video card has vga and DVI only. If I navigate to the nVidia site I can download the driver, I think. Since the resolution is so poor I cannot read the information on the page. Having finally downloaded the driver I cannot get it installed because all the notes in these forums simple say "type this command and everything will work". Type where? Where do I find it? How do I get there (I'm a newbie, remember). I have pages and pages that I have printed and none of them explain anything simply. It always assumes you have some knowledge of Linux. If I can't see the screen then I can't learn how to use the Linux operating system.

Can anyone help?????

TIA

---

### Post by emarkd on 2008-01-31
When someone tells you to type a command, they're referring to the terminal.  Applications > Accessories > Terminal.

Have you tried enbaling the restricted drivers for your card?  Check System > Administration > Restricted Drivers Manager.  If that doesn't work, some people have good results using [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by The Cog on 2008-01-31
The command is entered into a console window - Applications->Accesssories->Terminal. Many of theses commands need admin (root) priviledge which you can get with the command **sudo -i** which changes your $ prompt into a # prompt as an indication you are now root.

Have you installed the nvidia drivers from the repositories? I would do this first. Use the commands
[B]sudo aptitude update
sudo aptitude install nvidia-glx-new[/B]
the sudo bit borrows root priviledge for the one command.

---

