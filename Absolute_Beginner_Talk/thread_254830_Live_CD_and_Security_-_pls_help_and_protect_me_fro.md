---
title: "Live CD and Security - pls help and protect me from MIT students!!!!!"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by xoxog on 2006-09-10
I am about 15 minutes old to Linux. Have always used Windows. So I am a total newbie. I received a Ubuntu live CD in the mail yesterday and today I tried it. It works perfectly and I can connect to the internet and check my email without any problems.

Here is my situation:

I am surrounded by computer nerds and hackers since most of the apartment complex is populated by MIT engineering students. Hence security is of prime concern to me. I get around this problem by having two computers: one is always connected to the internet but has no data on it (only the Windows operating system). Then I have a second computer which has all my data but is always off-line and this computer can never be connected to the internet.  The MIT nerds always seem to hack into my internet computer and leave messages for me that they think are funny. The MIT students have terrified me and harassed me so much that the only time I connect to the internet is to check my email briefly once a day. Then someone suggested the Ubuntu live CD as a solution. 

I got rid of my internet computer and got myself a brand new machine with the Windows OS and installed a firewall. Then I ordered the Ubuntu live CD and tried it. It works fine as a live CD and I can check my email too. I have changed all my passwords.

Now that is the background. And here is my question: When I use Ubuntu live CD to check my email I don't seem to be behind a firewall. I therefore feel exposed. What can I do about it? How secure am I? Can the MIT students still hack into my machine or get my hotmail password even if my only mode of connecting to the internet is via the Ubuntu live CD? Pls help!

---

### Post by meng on 2006-09-10
Do you have an open wireless network that your neighbors are taking advantage of? Or possibly encrypted, but only WEP encrypted? I wonder if this is your primary weakness. Changing from Windows to Linux would improve your security, in my opinion, but you'd still be left with the weakness due to open or weakly encrypted wireless. Please clarify this, as there are things that can be done to strengthen your wireless security.

The sort of behavior your neighbors are engaging in is childish and illegal. Frankly, I would have taken steps to notify your neighbors, then the landlord, then the engineering faculty, and then the police, as a gradual escalation to try to stop this from happening.

---

### Post by xoxog on 2006-09-10
The apartment complex provides free wireless. It's like free utilities - wireless access is complimentary and included in the rent. Running the live CD means access to my machine is totally cut off, so it's got to be secure right? But when I connect to the internet using the Ubuntu live CD, I am not protected by a firewall, so can they still hack and get my hotmail password?

---

### Post by Solver on 2006-09-10
The first thing to understand about computer security is that there is no such thing as perfect security. As long as you are connected in any way at all, you can, theoretically, be hacked. The only question is, how difficult and time consuming that would be.

Windows is a pretty insecure OS, and even amateur hackers who don't really understand much about computers/networking can hack into many Windows systems. Switching to Ubuntu improves your security dramatically.

Ubuntu doesn't have a firewall by default simply because the Linux netcode is very much different. Basically, a clean Ubuntu system is at least as secure as Windows with a firewall. However, you can still opt to install a firewall or some extra security tools. Mind you, if you want to use Ubuntu, it's preferrable to install it, as opposed to using a live CD.

If you do install Ubuntu, get and install Automatix, too ([www.getautomatix.com)](www.getautomatix.com)). It will make Ubuntu more usable, and among its options there's also installation of extra security tools. Basically, with Ubuntu installed, regular updates and strong passwords, you are quite secure.

---

### Post by IYY on 2006-09-10
> Ubuntu doesn't have a firewall by default simply because the Linux netcode is very much different. Basically, a clean Ubuntu system is at least as secure as Windows with a firewall. However, you can still opt to install a firewall or some extra security tools. Mind you, if you want to use Ubuntu, it's preferrable to install it, as opposed to using a live CD.

This is incorrect. A default installtion of Ubuntu already has a powerful firewall installed. When you install Firestarter, you are just getting a GUI tool to configure this firewall.

However, if these hackers are using the WiFi system to get into your machine, even this may not be enough.

---

### Post by Solver on 2006-09-10
Ah, iptables. That one comes by default, my apologies - I just keep thinking it of something that gets my connection sharing working as opposed to a firewall.

---

### Post by NetworkGuy on 2006-09-10
To add to the post above.  Ubuntu, by default and unlike Windows, does not turn on any services that can be used by the outside world.  There is no Web Server or NetBios running on Ubuntu when you first install it, so your MIT "friends" should have nothing to connect to when they try to hack your computer.  But since your "friends" are probably sniffing the wireless network, I suggest you use https for all password transactions.  I believe you can use https when signing into hotmail and other web mail clients.  

> The sort of behavior your neighbors are engaging in is childish and illegal. Frankly, I would have taken steps to notify your neighbors, then the landlord, then the engineering faculty, and then the police, as a gradual escalation to try to stop this from happening. 
I agree with meng on this.  I'm sure your neighbors professors as well as MIT would not be very happy with their students illegally hacking computers.

---

### Post by meng on 2006-09-10
As other posters have said, given the communal wireless network, using Linux will be a more secure option for you than using Windows. I doubt your neighbors will have the brains to work out how to crack your system, in fact they're probably not particularly clever in the first place for cracking your Windows box.

However, if increased security is the only reason for you switching from Windows to Linux, you should be aware that getting used to Linux can be hard work. Often fun and rewarding, but occasionally requiring time and effort to learn new techniques and solve minor problems. You can get a lot of support in these forums as well as other places (Google becomes vitally important). I think that Linux is worth the effort required, but tastes vary.

If you decide this isn't for you, then you should stick with Windows, but employ strategies and install software that will reduce your risk. If you want to persevere with Linux, you will learn there are many other advantages. Either way, we're here to help.

---

### Post by Tomosaur on 2006-09-10
I don't think you'll have any problems if/when you make the switch. Sure, they can bounce around on your net connection since that appears to be you weakness, but net users are seen as 'nobod' by linux, and they will not be able to do anything. Added to this, all ports are, by default, hidden (appearing as closed to a would-be attacker). This generally means you cannot even be seen on the internet unless you are browsing or broadcasting.

Linux's way of doing things is just so much more secure than windows.

---

### Post by xoxog on 2006-09-11
Thanx for all responses. 

That https suggestion is great! 

I think I will stick to Live CD's before I completely switch from Linux to Windows because there is no one here locally to help me with Linux. After I get comfortable with the live cd, I will install linux on my machine.

I did google around a bit (like one of the posters suggested) and found out about two systems everyone seemed to suggest make internet surfing very secure: JAP and Tor. I posted on the Tor and JAP forums and spent hours figuring out how I could use JAP and Tor with a live CD. I found the following four very useful links:

[http://en.wikipedia.org/wiki/Security_focused_operating_system](http://en.wikipedia.org/wiki/Security_focused_operating_system)
[http://anon.inf.tu-dresden.de/operators/help/mixsetupLiveCD_en.html](http://anon.inf.tu-dresden.de/operators/help/mixsetupLiveCD_en.html)
[http://phantomix.ytternhagen.de/](http://phantomix.ytternhagen.de/)
[http://kaos.to/cms/](http://kaos.to/cms/)

Ubuntu is extremely easy to use - considering that I use it presently only to check my hotmail. But am I better off with one of the systems above from the security point of view? And if so, which one of the systems above would you suggest I use?

---

