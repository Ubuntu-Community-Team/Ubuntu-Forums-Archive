---
title: "help setting up a dial-up connection"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by orangePnut on 2008-01-18
I have been following this [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) tutorial.

I have downloaded scanModem and did as directed and have the following links:

[http://orangepnut.xnapid.com/1stread.txt](http://orangepnut.xnapid.com/1stread.txt)
[http://orangepnut.xnapid.com/modemdata.txt](http://orangepnut.xnapid.com/modemdata.txt)
[http://orangepnut.xnapid.com/Conexant.txt](http://orangepnut.xnapid.com/Conexant.txt)

I have a Conexant modem and was wondering whether or not the Open Source drivers listed [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant) will work with Ubuntu 7.10.

Any help would be greatly appreciated.

---

### Post by Mark_in_Hollywood on 2008-01-18
I will try to help.

Open a terminal. Applications/Accessories/Terminal.

please try 

gksudo wvdialconf

and post the output here. That will tell us if wvdial can access your modem.

After that, **if** you get a message with wording like:

Found one modem bla blah blahh  at /etc/ttys0

then:

gksudo /etc/wvdial.conf

you will get a text file with only a few lines in it.

Remove the

     ;

from in front of the user name / password / telephone and put those lines in this order

phone number to dial
username (or maybe it's called user ID - I forget)
password

save this file. 

Open a tab in the terminal and type

wvdial

it should dial the phone and get you on the net.

---

### Post by orangePnut on 2008-01-18
Modem not found.
[http://orangepnut.xnapid.com/modem_not_found.PNG](http://orangepnut.xnapid.com/modem_not_found.PNG)

---

### Post by Mark_in_Hollywood on 2008-01-21
Sorry to take so long to get back to you. Football weekend.

I believe, but could be wrong that there are no "drivers" that can communicate with your modem. Even though the Linux community eventually conquered the HCF HSF driver copyright problem.

I went through this a lot and I doubt I can give much help, but I can relate what I did. I found an external modem, and serial cable, at a Goodwill or Salvation Army thrift shop. Cost was $10 or $15. 

Once plugged in, wvdialconf found the modem, set the ports, etc. Everything just worked.

I realize you have put $ out for your device and may have other reasons for wanting it especially, so all I can do is say thanks for your time reading this.

Best help I can give you from here on is: get on the mailing list at linmodems.org

[http://www.linmodems.org/](http://www.linmodems.org/)

be sure to include the words:

cogent experts

in the subject line of the email

---

