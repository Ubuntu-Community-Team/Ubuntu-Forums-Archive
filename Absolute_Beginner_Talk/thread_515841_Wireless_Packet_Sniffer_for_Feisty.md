---
title: "Wireless Packet Sniffer for Feisty"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-08-02
Anyone know where I can get a good packet sniffer and explain to me how to use it?

---

### Post by ukulele_ninja on 2007-08-02
bump

---

### Post by kavon89 on 2007-08-02
That is used for hacking, I'm pretty sure no one would suggest to you a program which hacks your neighbor's wireless network.

---

### Post by ukulele_ninja on 2007-08-02
Thats great except im using on my own network, thanks though... Does anyone know where I can get one?

---

### Post by bodhi.zazen on 2007-08-02
Try wireshark. It is in the repos.

kavon89: there are legitimate uses for these types of programs ...

---

### Post by ukulele_ninja on 2007-08-02
Thank you Bodhi, Wireshark works with wireless networks? I was under the impression it worked with LAN only..

---

### Post by bodhi.zazen on 2007-08-02
Wireshark claims to work with wireless.

[http://www.wireshark.org/faq.html#sec10](http://www.wireshark.org/faq.html#sec10)

---

### Post by Tyggna on 2007-08-02
airdump works well, if you don't mind using command line

---

### Post by ukulele_ninja on 2007-08-02
I dont think it will work with my setup, when I try to pick my interface I want to use I dont have any options to choose from. Maybe Im not doing it right but im thinking it wont work. Is there a really simple version of a sniffer I can get a hold of?

---

### Post by madkaw on 2007-08-03
I think Aircrack-ng is about the best suite for sniffing and other fun.  It's not simple, but the website has some great info and tutorials to get you started.  You will have to use the command line though, but don't let that scare you.  

Remember always ask permission if you are going to play with an AP that is not yours. :)

Madkaw

---

### Post by Chris S. on 2007-08-03
> **ukulele_ninja said:**
> I dont think it will work with my setup, when I try to pick my interface I want to use I dont have any options to choose from. Maybe Im not doing it right but im thinking it wont work. Is there a really simple version of a sniffer I can get a hold of?

You mean Wireshark?  Try running it as root.  When I installed it through the repos, it put two launchers in my main menu: one regular and one "as root".  Or, you could do it the easy way and "gksudo wireshark" I guess.

I'm pretty sure you can use Wireshark for wireless packet sniffing.  I remember reading about it, but you have to set your card up correctly, and I don't remember what the trick was.

---

### Post by ukulele_ninja on 2007-08-03
Running from root works! I was able to capture packets from my connection. What do I use to see a visualization of the packets I capture?

---

### Post by ukulele_ninja on 2007-08-04
Ive figured out how to capture packets from my own connection, but how do I do a capture on another connection on this network? I have another wireless laptop I want to set up a capture on and a desktop all that run on this network...

Also, what do I use to recompile my results from a capture to view it visually?

---

### Post by grepgav on 2007-08-04
wireshark should work, but you may have to run it as administrator to show the proper interface. BTW a wireless network is a LAN, unless it is like ISP backbone long distance wireless.

---

### Post by ukulele_ninja on 2007-08-04
How do I run it as admin? also how do i tell it to view other machines on my network and not just mine?

---

### Post by Chris S. on 2007-08-04
Running as admin is the same as running as root.

You won't be able to capture any packets from other computers on your network unless they are being sent to the computer doing the capturing.  It's just not possible (unless for some weird reason they are being routed through your computer).

However, the exception to this is wireless traffic, since it's all floating in the air.  I'm guessing you want to capture wireless traffic, right?  bodhi.zazen posted a link in this thread to a Wireshark FAQ that gives a brief explanation of doing this.  You more than likely need to put your card in "monitor mode", but I don't know the specifics.  Check out that link and see if it helps you.

Also, what do you mean by viewing the results visually?  That sounds interesting, but I don't understand what kind of visuals you want to see.

---

### Post by insyzygy on 2007-08-12
For capturing wireless traffic kismet is really nice. It gives lots of interesting information about
all the wifi networks around you and by default logs all the packets it sees. For this to work your card needs to support monitor mode.
Whether or not this is supported depends on the particular wifi card you have
Try

```
sudo iwconfig eth1 mode monitor
```
where you should replace eth1 by the name of your wifi device.
If that doesn't give an error your good to go, if it does you might be stuck. 
In some cases even though the driver that ubuntu uses doesn't support monitor mode
they can be patched to add this but its very card specfic. Kismets website lists all the cards
it currently works with. Note that usually putting the card in monitor mode totally messes up its actual use for connecting to the internet and often once you put it in monitor mode you will need to reset the card to get it working again for regular internet use. 
 

Once you have a bunch of captured packets ethereal is a great analysis tool. Kismet and ethereal are both in the repositories, kismet requires you to set up
its configuration file so it won't immediately work.

Obvious disclaimer: You shouldn't sniff wifi traffic from networks you don't own
as that probably counts as an illegal wiretap and if not is surely illegal for some reason. 

You might also take a look at [http://www.remote-exploit.org/backtrack.html]("http://www.remote-exploit.org/backtrack.html")
It is a linux livecd that is specifically designed for penetration testing and has all the wireless 
hacking tools available by default and is supposed to have many wifi cards by default set up for
sniffing.

---

