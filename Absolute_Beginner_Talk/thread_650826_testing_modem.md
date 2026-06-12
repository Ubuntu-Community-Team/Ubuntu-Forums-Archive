---
title: "testing modem"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-26
Hi, 

I just installed HSFmodem driver from linuxant. 

I want to try whether the modem is working or not.

How can I test that the modem can dial???  How can I test whether the modem is working or not?

If it does, I'd like to buy a license and try fax.. 

Cheers,

---

### Post by Irihapeti on 2007-12-27
Here's how I got my hsfmodem to connect:

Open a terminal and type "sudo pppconfig" (without the quotes).

Then go through all the configuration options. I suggest you select "dynamic DNS" unless you know you need to do something else.

Also, select "no" when it asks if you want your modem autmatically detected. It's not very good at that. Using /dev/modem should work. If it doesn't, typing "sudo hsfconfig --dumpdiag" will tell you what device your modem is, along with a whole lot of other stuff.

If you've kept "provider" as the name for your logon profile, you should then be able to connect by typing "pon" in a terminal. Then type "plog", once you've connect, and you'll get information about your IP address, DNS address and so on.  

You should then be able to connect to a website with a browser, though it will be a bit sluggish at only 14.4k. Type "poff" in the terminal to disconnect.

Once you've got this working, you can look for a GUI dialup tool if you wish.

---

