---
title: "wpa and aegis protocol?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-17
Please not this is *NOT* for the AEGIS anti-virus.

I am new (1 month) to Linux and Ubuntu.  I have posted already, and read many posts here and on the net about trying to get WPA to work with my 2WIRE 2701HG dsl modem/wireless router.  I have never been able to get wpa to work, even in Windows.

I sent an email to ATT/Yahoo tech support asking about this and they sent me a reply tonght htat says the following:

"If you would like to use WPA for your 2wire 2701HG wireless connection,
 please follow these steps:

1. Open you internet explorer browser.
2. Go to either one of these sites: [http://homeportal](http://homeportal) pr
 [http://192.168.1.254](http://192.168.1.254)
3. Click on [Wireless Settings].
4. In the [Wireless Security] section, click the drop down under
 [Authentication] choose [WPA-PSK] and select [Save].
5. On your computer, try to connect to the wireless connection.
  (Example: For Windows XP: Right-click the [Wireless Network Connection] icon
 and choose [View Available Wireless Networks].)
6. Check the protocols installed in the [Properties] window of the [LAN
 Connection].
7. Verify that [TCPIP] and [AEGIS] protocols are installed.

Note: AEGIS Protocol is automatically installed in Windows when
 installing the 2Wire Wireless G adapter.

8. Enable the [AEGIS protocol].

Note: This is different from the standard wireless connection process.
  With the 2Wire 2701HG and an 802.11G adapter using the default WEP,
 always disable the AEGIS protocol, along with the IEEE protocol/
 authentication.
"

Obviously tcp/ip is installed, and i'm using the wireless for this using WEP.  I have no idea what this stuff about AEGIS protocol means and hpw do I know if it is installed/active in Ubuntu??

Thanks!!:)

---

### Post by digital_sabotage on 2007-07-17
ok  ...think i know your fix  ...i'm on the 2wire 2700hge

instead of 'wpa-psk' ...choose 'wep-open' 


use custom encryption key ...make 10 digits (write down or remember) ...save

...now when you select your network name to connect to from the wireless list ...you will be prompted for a password  ...make sure wep is selected in the dropdown and enter your 10 digit password

...should be good to go ...hope this helps

---

### Post by anewguy on 2007-07-17
Well, I appreciate the reply!:)  However I have been using WEP-open, and wanted to try wpa as I have been told it is more secure than wep.  Perhaps it's just a waste of time?

Thanks again!:)

---

