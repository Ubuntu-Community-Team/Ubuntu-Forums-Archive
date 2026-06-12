---
title: "Dialing Out."
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Lonelynoob on 2007-03-11
I'm really afraid to do this because I passed the "I quit" line about 8 hours ago, but the vendetta is killing me that I simply must see something work at least once before I go slaughter the neighbours kids to make me feel better.   So hopefully someone can do something before my universe and my brain explodes.

I fear that this will not be an easy answer let alone an answer I even understand.

-Built in modem.
-It is detected and all appropriate dial numbers and passwords are punched in.

**Ahem**                           [I][B] How do I get it to dial?
[/B][/I]
Aw, dammit, I can see the tsunamically large answer already....   here it comes.....

---

### Post by Ocxic on 2007-03-11
look in add/remove applications there should be a few dialer apps in there to help you on your way

---

### Post by HereInOz on 2007-03-11
By what you have said, you already have a dialler application for this, but it is just not working.  Some internal modems can be very difficult.  One suggestion is that if you can get hold of an external modem, even on loan, hook it up and get it working, that will demonstrate that:

a)  You know what you are doing.
b)  That all is well with your phone connection.

Once you have done that, you can start to mess around with the internal modem.  Not much help, I know, but I have heard some heartache stories of internal modems and Linux.

---

### Post by Lonelynoob on 2007-03-11
I don't know if that's correct or not.. I've punched in the info into the "Network" areas..
 (like, the area where you would normally find the wireless router properties if I hadn't smashed the **** out of it at hour 23)...

But as far as having a "dial" or "connect" button to push, I see no such thing anywhere...

---

### Post by windozer on 2007-03-11
[click]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6")
Go down to "Alternative Way 1 (using wvdialconf & wvdial)"
I don't know what the $ in the commands there is supposed to do.. just leave it out if it doesn't work. And instead of typing:
sudo nano /etc/wvdial.conf
try:
sudo gedit /etc/wvdial.conf 
That will let you edit the file in a real text editor which is a bit easier than nano. For future reference, in nano where it says "^G Get Help  ^O WriteOut  ^R Read File" at the bottom means press ctrl + g for get help, ctrl + o to save etc.
Good luck with it.

---

