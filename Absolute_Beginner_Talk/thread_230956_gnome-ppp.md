---
title: "gnome-ppp ?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2006-08-06
Is gnome-ppp included?

I tried *sudo apt-get install gnome-ppp* but it wasn't found.

I'd settle for kppp.

I am trying to dial out to my ISP and I was able to do that with KPPP in RedHat 8. Just trying to do the same in Ubuntu.

Help!

---

### Post by Sutekh on 2006-08-06
[gnome-ppp](http://packages.ubuntu.com/dapper/net/gnome-ppp) isn't in the main repositories, it's in the **universe **repository.

Do you have any kind of internet connection available?  

Other option is [ppp](http://packages.ubuntu.com/dapper/base/ppp).  However it's only available from the Alternate CD, it's not on the LiveCD (Install CD)

Same for KPPP.  You'd still need a Kubuntu ALternate CD anyway.

---

### Post by ieee488 on 2006-08-06
I have internet connection but on my Windows desktop.
Trying to get Ubuntu to work on my Toshiba laptop.

But I did manage to get gnome-ppp by downloading to my Windows PC then copying the file over to the Ubuntuc laptop using a USB flash drive.

Now, it looks like gnome-ppp doesn't do CHAP authentication which won't work for my ISP. Very frustrating.

And Ubuntu doesn't seem to even recognize my PC Card modem because I don't even hear it dialing out. This PC Card modem works with Red Hat 8 so I was thinking it should work with Ubuntu since it isn't a Winmodem.

---

### Post by Sutekh on 2006-08-07
Hmm, well KPPP worked for you with RH8?  If it doesn't need to install too many KDE libs, then maybe it's worth a shot?

---

### Post by Cariboo1938 on 2006-08-10
> **ieee488 said:**
> And Ubuntu doesn't seem to even recognize my PC Card modem because I don't even hear it dialing out. This PC Card modem works with Red Hat 8 so I was thinking it should work with Ubuntu since it isn't a Winmodem.Try if your modem is detected:
>open terminal
>type command: *[COLOR="DarkOrange"]sudo wvdialconf/wvdial.conf[/COLOR]*
you get a list where you should find your modem
Remeber the port name you need this for configureing ppp
Hope it helps.
BTW there is a excellent DialupModemHowto:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

