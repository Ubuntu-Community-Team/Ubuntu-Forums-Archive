---
title: "No carrier! message when I run wvdial."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by KMuchane on 2008-02-22
Hi!       
I have just managed to install drivers for my internal modem... The only problem now is that when I run wvdial I keep getting No Carrier! message, it keeps trying but just brings us that message, over and over. What am I missing?The ISP details seems to be in order.                          Thanks!

---

### Post by dstew on 2008-02-22
Maybe it is timing out before the ppp handshake is finished, or your modem is not supplying a carrier signal and wvdial is checking for it. Post the output of the command```
cat /etc/wvdial.conf
```

---

### Post by KMuchane on 2008-02-27
Hi!  
The contents of my /etc/wvdial.conf file are:    
[Dialer Default]         Init1 = ATZ                   Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0                    Carrier Check = no     Stupid mode = on       Modem  type = Analog Modem            Baud = 460800           New PPPD = yes          Modem = /dev/ttySHSF0            ISDN = 0                        Phone = *99***1#    Username = saf           Password = data                                   
I think I also need to add that the phone am using is a cellphone connected  to a USB port. That does not sound right ! Also, where do I get to input the ISP's fixed IP address?  I've been trying it under Network manual configuration but I cant get to save the location and apply!   Thanks in advance!

---

### Post by schmildo on 2008-02-27
LOL interesting!

It seems to be ignoring your request to not 'wait for dial tone'; You had: Carrier Check = no
  From memory the AT command equivalent of this is "x0". (some variations of this are ATX=0 etc...) Try to use the AT commands instead of the human readable ones you have there, (It might be a little harder to read but it will rule out other possible issues)


It looks like you're trying to use your mobile phone network as a service provider. The phone number that you will need to dial will depend on your handset. Judging by the number you are calling i'm assuming you're using a SonyEricsson handset.
  The phone number: *99***1# indicates that you may have already configured the APN (Access Point Name) in the handset's profile position one. (your phone may only have one data profile anyway) Check your handset's data configuration.

You'll be needing to change from analog to digital too, and the modem speed might not be appropriate; that'll depend on your service provider, and the particualar model of mobile phone you are using. You'll also need to ensure that your mobile phone account has data enabled, so ring  your mobile provider.

It might be best to ring your mobile provider, and ask for assistance. They wont know anything about linux, so grab a windows XP machine and get it working on that first, then when you've figured out how it works, google for some linux scripts.

The IP address should be automatically assigned to you via DHCP. Most mobile providers give you private addresses so if you wanted to host a website from your laptop you'd need to register with some funky redirection websites as well.

I used to setup these connections for a living whilst I was working for a company here in Australia, we did it all day every day, but very few of us were familiar with linux because we weren't required to support it...

To make matters worse, some mobile phones wont allow data connections via the USB cable, you might have to try using the infra-red or bluetooth if you have it.

If I were you i'd definitly get it working in windows before Ubuntu, because there will be alot more support out there for you. SonyEricsson's website even has configuration assistance and Vodafone too.

I wish you the best of luck, I'll try to help you out some more if you can get me more info, but I 'm not sure when next I'll be back on this site.
If you do get it working in Ubuntu, please post all the info you can so that others can have a look, I've only seen one or two people attempt what you are trying to do!

---

### Post by KMuchane on 2008-02-28
Hi!
Thanks for the input. You correctly assumed that I am using  my mobile service provide as my ISP. 
I already having a working internet connection - through a USB connected cellphone - on XP, actually it connected on the first attempt!               I am using a Motorola L6i cellphone and a HP 510 laptop. My phone is configured for data, infact I am writing this ,and will send it, from my cellphone!  
Lemme get working on the changes you proposed and see if I will succeed.                  The unfortunate thing is that we dont have a Linux   User's  Group here in Kenya, you are on your own!          Thanks!

---

### Post by KMuchane on 2008-02-29
Hi! 
I edited the /etc/wvdial.conf file and added x3 at the end of Init2 so that it can  dial without waiting, now the text scrolls blindingly fast and stops at Bad Init2  string and  then quits without connecting.                  I've tried playing around with the settings but I cant seem to to be getting closer to being connected!       Does anyone got any ideas?    Thanks!

---

### Post by KMuchane on 2008-03-01
Hallo!

When I run wvdial I get the following results:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: NO CARRIER
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#

And when I run pon,I get the following:

Feb 29 20:36:17 tchane chat[5943]: expect (OK)
Feb 29 20:36:17 tchane chat[5943]: ATZ^M^M
Feb 29 20:36:17 tchane chat[5943]: OK
Feb 29 20:36:17 tchane chat[5943]:  -- got it 
Feb 29 20:36:17 tchane chat[5943]: send (ATDTreplace_with_number*99***1#^M)
Feb 29 20:36:18 tchane chat[5943]: expect (CONNECT)
Feb 29 20:36:18 tchane chat[5943]: ^M
Feb 29 20:36:56 tchane pppd[5941]: Connect script failed
Feb 29 20:36:56 tchane chat[5943]: SIGTERM
Feb 29 20:36:57 tchane pppd[5941]: Exit.


So what I can I do? Can Someone please help.Thanks in advance!

---

### Post by KMuchane on 2008-03-06
Hi!   
I am still not connected! When I try to send emails from my Yahoo account to Linmodems their server keeps rejecting them.           Can someone please advise me on what  I should or should not do?           Thanks!

---

### Post by kri1987s on 2008-06-23
Try changing the phone number to *99#
username = 0
password = 0
that works on nokia 3110c on safaricom

---

