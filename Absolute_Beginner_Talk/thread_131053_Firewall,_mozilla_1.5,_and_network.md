---
title: "Firewall, mozilla 1.5, and network"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by rvener on 2006-02-15
Hi,

I cleaned my XP and installed Ubuntu and haven't felt this novice in a long time.

I have a cable modem and have Zonealarm on my other windows system.  I thought a first course of action was to add a firewall to the Ubuntu system.  I found Guarddog-2.4.0 and after a while, I figured out how to tar it, and then move it to the /usr/lib area, but then run out of gas.  I cannot seem to figure out how to run an install program, or start the application. Any firewall program would do.

My kids use AOL AIM.  It has an express mode that says it requires mozilla 1.4 or higher.  I downloaded mozilla 1.5 and am having similar problems installing.

Thirdly, I have a router and used to print to a printer connected to my windows system.  Is that still possible?  I think I set my windows system for a more secure network configuration so I will play with that too.  I can't seem to see the network from the Linux system.

Am having a blast though!

Any help would be greatly appreciated....

Thanks.

---

### Post by kaamos on 2006-02-15
Hello!

For the firewall, Firestarter is a popular one. You can install it with synaptic. [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by mustang on 2006-02-15
> I have a cable modem and have Zonealarm on my other windows system.  I thought a first course of action was to add a firewall to the Ubuntu system.  I found Guarddog-2.4.0 and after a while, I figured out how to tar it, and then move it to the /usr/lib area, but then run out of gas.  I cannot seem to figure out how to run an install program, or start the application. Any firewall program would do.

Hi rvener,

to install guarddog, you don't need to download the tar and extract from it. All you have to do is type the following in the terminal:

```
sudo apt-get install guarddog
```

This downloads and installs the .deb for you. Think of the .deb file as the Ubuntu .exe equivalent. 

Now if you're deadset about installing Guarddog, don't let me stop you but firestarter seems to be much more popular around the forums so I might suggest trying that out so that if you encounter problems, more people will be able to help you out. 

> My kids use AOL AIM.  It has an express mode that says it requires mozilla 1.4 or higher.  I downloaded mozilla 1.5 and am having similar problems installing.

It's telling me that too. Weird. Is is not possible to use a software client such as GAIM (which comes preinstalled)?

I'm not sure about the last question but I'm sure someone knows. 

Good to know you're having fun. Keep the questions coming!

---

### Post by rvener on 2006-02-15
Thanks for the help. Not at all married to Guarddog.  I tried the Synaptic way and I think I have to reconfigure my router to a static IP.  The instructions are a little cryptic, but it looks like after I make my router a static IP, I have to set that IP in the administrator network area.  I was having a little trouble where to set that.....

AOL AIM I don't think is compatible with anything else...  Sounds like AOL doesn't it.....

Thanks!

---

### Post by majikstreet on 2006-02-15
Just use GAIM.. it's on ubuntu by default.. Applications, Internet, GAIM Instant Messenger or similar... It works, trust me.

---

### Post by kompa on 2006-02-15
Sorry, a bit of OT: How do I set firestarter to start on boot?

What should I scan my system with and how frequently?

---

### Post by rvener on 2006-02-15
I tried sudo apt-get install firestarter and it can't find the package.

The Aynaptic shows Firestarter, but won't let me apply.  I set the router to static DNS and checked in Ubuntu and it shows them as the ISP addresses like the instructions.

Am I missing something?

Thanks.

---

### Post by rvener on 2006-02-15
Sorry, my search was listed on the left of Synaptic Package Manager, but it was not listed on the right.  So it was not finding it, so I couldn't mark it for installation......

---

### Post by rvener on 2006-02-16
Automatix rocks.......I installed Firefox 1.5 and Firestarter with no problems.  Am still having problems with the network though...

I got rid of the IBX protocol stuff and still no luck.. Any help would be appreciated....

Thanks.

---

