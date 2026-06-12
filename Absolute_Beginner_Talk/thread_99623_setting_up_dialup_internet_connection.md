---
title: "setting up dialup internet connection"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by dtracer46 on 2005-12-05
I installed 5.10 yesterday-everything went real smooth-but when I went to set up my dialup internet connection I could't find any text or dialog box to put in my info-isp name, phone number, username, password etc. I found it real easy in Xandros and Linspire. Please guide me to the right place.
Thanks

---

### Post by Nequeo on 2005-12-05
Yeah, there's a program in there... but it isn't really advertised at all.

Try opening up a terminal (Applications--->Accessories--->Terminal) then type
'sudo pppconfig' from the command-prompt.

I've never used Ubuntu with a modem, so I can't help you with using the program itself. But I hope it's easy to use and understand.

[EDIT]

I just ran through the program with a test connection. Just read the instructions *very* carefully and you should be fine to set up your connection. But once you've finish the set-up, it doesn't tell you how to actually connect!

To connect to your ISP, stay in the terminal window and type 'sudo pon <name of your connection>'. So if you created a connection called 'iiNet' you'll need to type 'sudo pon iiNet' to connect. It's case sensitive, so get the caps right :) Also, when you're done, type 'sudo poff' to disconnect.

I'm sure there are graphical ways of doing this... But I'm afraid I'm not an expert with modems.

Cheers,

Good luck,

Cheers,

---

### Post by dtracer46 on 2005-12-05
Thanks I'll give it a try when I get home from work

---

### Post by Nequeo on 2005-12-05
Once you *do* get your internet connection up and running, you might also want to look into 'gkdial', for a graphical alternative to typing 'pon' and 'poff' all the time...

Or even 'diald', which is a program that sits in the back ground and calls up your modem connection when its needed. 

Both these programs are in Ubuntu's 'Universe' repository. If you know how to use Synpatic, all's well and good. If you don't, just let us know and we'll talk you through it.

Cheers,

---

### Post by Nequeo on 2005-12-05
More stuffs!

Also check out 'wvdial' (type 'man wvdial' from the terminal window), and gnome-ppp (an alternative to 'gkppp' that uses wvdial behind the scenes, rather than the pon/poff stuff).

Wvdial comes pre-installed, while gnome-ppp is in the Universe repository, and can be installed through synaptic once you have a working connection.

Between all those programs, you should hopefully find something that works! (Unless you have a 'winmodem'. But if your modem was working under other Linux distros, you're probably okay there.)

---

### Post by dtracer46 on 2005-12-06
I tried the sudo pppconfig when I got home from work last night. I thought I followed all the question ok, but no go. I guess I will try again and document where it stops working for me.
Thanks for all your help, at least I'm going in the right direction

---

