---
title: "USR5610B modem not recognised"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Richard de Faria on 2007-01-17
I installed version 6.06LTS on my AMD64 Athlon based system.  Dual boot system -Windows Xp runs off one hard drive,Linux the other.
The modem is a US Robotics controller based modem model USR5610B (56K Performance Based Pro Modem (PCI Internal) which works fine in Windows.  I believe its connected at COMM3.
Linux won't detect the modem, even under Autodetect.
I have never used Linux before and am completly new at this. I am not the programming type. Would really like to use Linux and recommend to others if I can get dial up working.

Any step by step instructions would be much appreciated!:confused:

---

### Post by riven0 on 2007-01-18
[This post may help you some]("http://ubuntuforums.org/showpost.php?p=1916131&postcount=1"). I know US Robotics is not exactly Linux friendly though, so good luck. I haven't had a dial-up modem for years, so I can't personally help.

---

### Post by ieee488 on 2007-01-18
I haven't had to do those two things mentioned in the linked post.

I have an USR internal modem that works with Ubuntu, but it was not autodetected.

What I do with all the Linux distros, is
1) open Terminal window, type **sudo wvdialconf** and hit Enter
2) you can see Ubuntu go about trying to find a modem; it is apparent when it finds one;
note the ttyS#
3) install gnome-ppp and use that ttyS#

good luck

---

### Post by Richard de Faria on 2007-01-18
Thank you for taking the time to forward me your suggestions.  Once I get back home, I'll give them a try. I bought the USB Modem - controller based, and was told go go with the big brand name so I would have less difficulties!  Oh well,should be a learning experience!:)

---

### Post by ieee488 on 2007-01-18
Let us know how it works out. It is very helpful when people report back.
And if you find that it works with Linux the more people that know this the better.

---

### Post by Richard de Faria on 2007-01-18
Hey, I'm on the net using Ubuntu and through my dial up modem.  I can't believe it!

Hello ieee488 here is what I think I did

I went into Terminal
I typed "sudo wvdialconf"
It came back with "found modem /dev/ttyS4"
and "modem configuration written to /etc/wvdial.conf"
"ttys4<info>: speed 115200"  and then some other code.

I went into the Network Settings under applications
I entered the modem port as /dev/ttys4
I note that on the pull down menu there was no choice for ttys4 it only went to ttys3 - perhaps this is the problem for "autodetect" ?
It did not autodetect, but I went back I think 1 window and saw that there was an "activate" button once I highlighted the "modem" versus the "ethernet" choice.
Then I heard the modem activate (oh a sweet sound at that point).
Still no internet though.
Went back to Networking Tools in Application and under Network Device I changed the entry to the "modem interface (ppo)".
I then tried Firefox and it worked.

I hope I don't loose settings or something when I shut down, but regardless, by trial and error and your great starting tip, I think we have success!
Thanks.:D

---

### Post by ieee488 on 2007-01-18
Hey, that's great!  :) 
Love a success story.

By the way, is your modem really an USB or did you mean PCI?

---

### Post by Richard de Faria on 2007-01-19
No, not a USB but a USRobotics.  I'm not much of a typist!
Getting it working was a real relief!

---

### Post by LPCG on 2007-01-19
ok, well...since i have the same modem, and am having the same problem, ill just ask here.  keep in mind i have version 5.10...

i typed in sudo wvdialconf, but after asking me for the password it came up with **wvdialconf <configfile-name> (create/update a wvdial.conf file automatically)**...what am i supposed to do with this?  

after that, (because it only gives you the option of up to ttys3), i tried typing in ttys4, ttys5, etc. but nothing.  PLEASE dont tell me there is something i need to update, because the computer DOESNT HAVE INTERNET, and the whole point is that im trying to connect to the internet so i can DO the updating i probably need to do!  (i bought a book that came with a dvd of ubuntu, but it is maybe a year old...thats why i have version 5.10!)

---

### Post by ieee488 on 2007-01-19
I used to have 5.10. Works about the same.

Try typing **sudo wvdialconf /etc/wvdial.conf**
the information will be stored into */etc/wvdial.conf*  file

then open */etc/wvdial.conf* with gedit by typing **sudo gedit /etc/wvdial.conf**and take a look at what ttyS# it found

my prefer way is then download gnome-ppp in Windows and copy it to a USB flash drive and
take that USB flash drive to the PC with Ubuntu and install gnome-ppp
just type in /dev/ttyS#  in gnome-ppp; don't use Autodetect

other options are described in
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by LPCG on 2007-01-20
just out of curiosity...what is the sudo for?  i mean, whats the difference between sudo wvdialconf and wvdialconf?  or is that too broad a question to be explained in fairly simple terms...?

---

### Post by unisol on 2007-01-20
you are using a hardware modem right? i had used this particular model before in hoary and it showed up at ttyS14. after that it worked fine. i used the system/adminstration/networking app to run it. with ubuntu 606 0r 610 you should be able to use the modem lights applet. and sudo is a file permission command.

---

