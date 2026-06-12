---
title: "Kbuntu vs. Madriva vs. Open Solaris vs. Simply MEPIS"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-03-13
Hello!

I am planning on giving my mom and dad the gift of Linux before I go off to college this summer, but I don't know what kind would work best with their computer.  When I go off to school, I will use Kbuntu but I don't know how well that will work for them.

Here is what I know about my hardware:
[LIST]
[*]Processor:  1993 mHz
[*]Printer:  hp Deskjet 3320 (drivers need to be compiled for Ubuntu)
[*]Memory:  256 Mb of RAM
[*]Modem:  Lucent Winmodem (I don't have a LiveCD so I can't run the tool to check the exact model right now)
[*]Disk Space:  ~50 GB
[*]Graphics Card:  Intell Extreme Graphics
[*]Floppy Drive:  1
[*]Microphone:  Small $20 model from Plantronics
[/LIST]

I've run the Ubuntu LiveCD before, but I had to unplug my computer after I clicked shutdown because it wouldn't reboot (other people have tried and didn't have that problem, so I don't know if that is significant).

I would like to run Kbuntu because it embodies everything I respect about Linux and free software, but I have **a small town dial-up connection**, and unless there is some clever way to get drivers for my Winmodem, I don't know how I can use Kbuntu or Ubuntu.  Even if the connection works, please bare in mind that my **download speed is about 10 MB per hour on Windows**.

The versions of Linux listed in the topic title are those that I wouldn't mind installing; every other version seems loathsome.  I would apperciate any feedback people could give me about my setup and possible solutions.  Thanks! =)

---

### Post by Cloudy on 2006-03-13
If you're living on campus when you go to college chance are you won't have to worry about dialup, I think..

---

### Post by az on 2006-03-13
All your hardware works out-of-the box with Ubuntu except the modem.  The printer uses hpijs which is included - why do you say you need to compile the driver?

The lucent winmodem driver was a little broken in breezy, maybe try the Dapper live cd and see if it works with your modem?

Mepis is proprietary and solaris won't support your modem in any way shape or form.  Mandriva is slow, but maybe things will work, too.

---

### Post by Darklighter137 on 2006-03-13
Cloudy - This is for my mom and dad, who have dial-up.

Azz - For the printer, I was just going with what the HP website said (it said it might need to be compiled, so I wasn't going to assume that it didn't).  Are you implying that the Dapper Live CD comes with the proper dial-up drivers?  Will Dapper itself have the drivers?  If not, in what way can I get them so that I will have internet?

---

### Post by shuttleworthwannabe on 2006-03-13
My experience with MEPIS 3.4-3 (latest release) has been very positive. It may even detect your winmodem, because it detected mine and worked on 2002 Model Fujitsu Lifebook laptop. It comes as a live CD that is installable on HDD, so it would not hurt to try it out. It comes with KDe and multimedia support just work our of the box. As far as I know, it has unparalleled hardware detection like no other distro.

So why am I not using MEPIS: My HP laptop power management was the problem, it would not allow me rebooting, rather shutdown only. Bit irritating, and also because I like the Ubuntu ethos and simplicity. Ubuntu documentation and support is the best out there.

Once you set up Ubuntu/Kubuntu for your parents, it will be a breeze (sorry unless you for dapper..it will just drake). Dapper is fast and uses very resources. It has all the necessary apps without any clutter. Printer id is excellent, and may your HP will be recognized and drivers suggested at installtion.

I am not sure about Mandriva..it reeks bloatware to me.
Anyway, good luck with the choices.
Best,
S

---

### Post by Darklighter137 on 2006-03-13
Thank you for your input!  I though Mandriva looked a bit like bloat-ware, but I couldn't be sure.  Since you are running Dapper, could you tell me if it comes with dial-up drivers? ^_^

---

### Post by daveisadork on 2006-03-13
I think the regular Ubuntu would be a better bet. Gnome usually proves to be a little bit more parent friendly IMO. I'm kind of in the same situation as you, my parents are on dial up, and I actually ended up getting them an external modem to use. It's actually a little faster and works out of the box.

---

### Post by Cloudy on 2006-03-13
[QUOTE=Darklighter137]Cloudy - This is for my mom and dad, who have dial-up.

Azz - For the printer, I was just going with what the HP website said (it said it might need to be compiled, so I wasn't going to assume that it didn't).  Are you implying that the Dapper Live CD comes with the proper dial-up drivers?  Will Dapper itself have the drivers?  If not, in what way can I get them so that I will have internet?[/QUOTE]

Oops, yeah, my bad. I missed that part.

---

### Post by meborc on 2006-03-13
if you are leaving the comp to your perents, may be it is better to use ubuntu instead of kubuntu (ofcourse assuming you chose *buntu)

i find gnome more easy to teach (to old people in particular)

---

### Post by shuttleworthwannabe on 2006-03-13
[QUOTE=Darklighter137]Thank you for your input!  I though Mandriva looked a bit like bloat-ware, but I couldn't be sure.  Since you are running Dapper, could you tell me if it comes with dial-up drivers? ^_^[/QUOTE]

I must admit, Ihave not trested the modems, but if you do a google search, someone somewhere has probably figured this out or has a system like yours that has been tested. linux for laptops/desktops isa good start.

I am using corporate LAN connection, so have very little need for dial-up. I am sorry for not being helpful.

regards,
S

---

### Post by Darklighter137 on 2006-03-13
Hmm, that Gnome advice seems good....

About this external modem business, will it work with my dial-up?  The local company provides its own software, but all it really does is feed the information in and provide error message boxes, nothing fancy.  What should I expect to pay for such a device?  Will it work with Windows, too? ^_^

---

### Post by arctic on 2006-03-13
[QUOTE=azz] Mandriva is slow, but maybe things will work, too.[/QUOTE]What the hell are you talking about? Did you actually use Mandriva lately? I doubt it.... [-(  I have two dual-boot systems. One a Laptop, the other a desktop. Both have Mandriva 2006. The Laptops has Dapper Drake, the desktop system has Breezy Badger and Mandriva is WAY faster than Ubuntu on both machines. (laptop: Mandriva boots in 46 seconds. Dapper boots in 96 seconds. desktop: Mandriva boots in 36 seconds, Breezy in 52 seconds). The only systems I have that beat Mandriva in terms of speed is Yoper 2.91 and a tweaked Fedora 4 box (a whopping 32 seconds).

Better make your homework before spreading things that are definitely not true. :rolleyes: 

About Mandriva and bloatware: This is a very relative thing. Mandriva comes with more stuff by default, but you can strip it down almost as much as you like and start with only a kernel in package selection. From 900 MB to 6GB for a desktop system, everything is possible. \\:D/

---

### Post by Swab on 2006-03-13
[QUOTE=Darklighter137]Hmm, that Gnome advice seems good....

About this external modem business, will it work with my dial-up?  The local company provides its own software, but all it really does is feed the information in and provide error message boxes, nothing fancy.  What should I expect to pay for such a device?  Will it work with Windows, too? ^_^[/QUOTE]

An external hardware modem will work in Windows and Linux with no problems.  It costs more than an internal software modem... I'm not in the US so I don't know exactly, maybe $40?

---

### Post by Klaidas on 2006-03-13
**Kubuntu vs Mandriva**:
I didn't really like Mandriva  when I used it. Even tho it was my first linux distro with easiest install. I'd choose (k)ubutu. 
**Open Solaris**:
I haven't used it, sorry.
**Simply MEPIS**:
I have only used it on a live cd. I didn't like it for graphics. 

In conclusion, I would choose Ubuntu or Kubuntu :)

---

### Post by Razorback on 2006-03-13
The external modem will more than likely work without a hitch.  I tried two internal modems with no luck.  Bought a Hayes external modem and it worked right off the bat and works fine in Windows and Linux.  I bought it for ~$25 used on ebay.

Here is a link to one like mine:

[http://cgi.ebay.com/HAYES-ACCURA-56K-33-6-EXT-FAX-MODEM-complete-setup_W0QQitemZ6857131285QQcategoryZ14920QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/HAYES-ACCURA-56K-33-6-EXT-FAX-MODEM-complete-setup_W0QQitemZ6857131285QQcategoryZ14920QQrdZ1QQcmdZViewItem)

---

### Post by az on 2006-03-13
For breezy, try the instructions for a lucent modem found here:
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

For Dapper, I beleive that may already have been taken care of by HAL, you should try the dapper live cd to see.

---

### Post by dermotti on 2006-03-13
I would say use Mepis. Its the easiest to reinstall of something goes wrong. You can also use the live CD to fix things if the system gets messed up.

Just remeber to turn of the ETCH respositoriese, they are screwed up l8ly.

---

### Post by Darklighter137 on 2006-03-13
Thanks guys. ^_^

---

