---
title: "Installing a modem and then dialing the number."
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by danr on 2006-04-02
Hello everyone,

I’ve been trying to get on line with the computer I installed Ubuntu on,

The modem that was in the computer it would not detect, so I put it a different one and it found it using the "Autodetect" and it says "/dev/tty53" in the modem port box.

Does that sound right? 

I also entered all my dial-up info there.

And now for the really stupid question, how or where do I tell it to dial the number to get on line! lol

I found a couple of places to click “connect” but they don’t look right and nothing happens when I click them.

---

### Post by ferebee on 2006-04-02
Dial Up modems can be tricky but you can try going into
System>Administration>Networking 
and entering your ISP info there.
Once you do you can connect by clicking the Activate button, and hang up with Deactivate. If your modem is supported, this should get you connected, though you may have to play around with the settings to get it going.

If you can get online that way I recommend opening Synaptic and installing  Gnome-ppp. It's a simple dialer program.

Here's a listing of Modems known to be Linux compatible:
[http://free.hostdepartment.com/g/gromitkc/winmodem.html]("http://free.hostdepartment.com/g/gromitkc/winmodem.html")
Mind you, not all of them will be supported by every distro. 

And here is a page from the Ubuntu Wiki on Dial-Up Modems and Ubuntu:
[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

---

### Post by danr on 2006-04-02
Thanks so much for the response ferebee,

Oddly enough I did click the activate button and it didn’t do anything so I guess something is wrong.
I will check the modem against the list you provided and see if it’s listed, I was hoping that because it was found by the system it would work, must not be necessarily true!
 
I want to get on line with it, from what I understand I need to download many things to get it going right, just have to get it on line first to do it though.

Thanks again for the response and the links, Dan

---

### Post by ferebee on 2006-04-02
[QUOTE=danr]Thanks so much for the response ferebee,

Oddly enough I did click the activate button and it didn’t do anything so I guess something is wrong.
I will check the modem against the list you provided and see if it’s listed, I was hoping that because it was found by the system it would work, must not be necessarily true!
 
I want to get on line with it, from what I understand I need to download many things to get it going right, just have to get it on line first to do it though.

Thanks again for the response and the links, Dan[/QUOTE]

Sorry I  couldn't be more help.

I'd suggest maybe you could post the make and model of your modem;
it's possible another user may have had experience with it and could
confirm whether getting it going is possible, and how they
went about it if it was.

---

### Post by danr on 2006-04-02
Ok, here is a list of the modems I have on hand,

1-Aceex Corp dm-56v14 (this is the one that the system found with the “autodetect”
2-compaq series psb226 (this is the one that was not found with the “autodetect”
3-gateway part #6000767
4-zoomfax 56k model #2919l 
5-us robotics model #0584
 The rest I have not tried at this point, I don’t know how to tell if they are working or not! lol 

Any help that any of you could provide would be greatly appreciated, Dan

---

### Post by dvarsam on 2006-04-02
Hello!

I could NOT setup my Modem either...
So, I went & bought a Router.

However, your US Robotics modem, sounds a good one...
In the Windows world I could set a US Robotics Modem, fantastically!!!

NO drivers were required!!! (compared to ANY other brands I have used...)

So, I bet you should do some searching in google about it...
Maybe a search on "setup <usrmodel> in linux" could get you somewhere...

But, anyway, US Robotics, in my experience, sound a Very Good & Serious Company!
So If I were you, I would search on how to Setup that Modem with my Linux.

Good Luck!

---

### Post by danr on 2006-04-02
Thanks for the response dvarsam, I’ll check that one out and see what I can do with it.
If I ever do get one to work I will post witch one it is, and what I had to do to make it work.

---

### Post by Mark_in_Hollywood on 2006-04-02
I am assuming you aren't using a sofware (Win) modem. From the posts it seems as though you have at least one host or controller based modem.

If you are using Hoary Hedgehog (ver. 5.04), you may have to configure wvdial.conf manually.

See man wvdial.conf

Using gedit, or nano if you prefer:

change the baud rate to 115200

set your username and password

set your dial out telephone number.

If you have a working Windows, the modem icon in the control panel will somewhere have a line about INIT strings. Copy it (by hand onto paper). You may need to add it to the wvdial.conf file.

Save the file.

Open a terminal

sudo wvdial

This should establish a phone connection.

MINIMIZE the terminal (or console window, if you call it that).

Click on Firefox or your browser, if you have one.

Better still, run the Update Manager in System / Administration

Let us know if you try this, how it went, please.

---

