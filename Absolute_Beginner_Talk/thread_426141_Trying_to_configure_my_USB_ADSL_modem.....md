---
title: "Trying to configure my USB ADSL modem...."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by =CrAzYG33K= on 2007-04-28
I have an Airtel Broadband connection.. using Yozan Tera100U DSL modem (branded Beetel - for Airtel)
This very model is based on the Conexant chipset as per this link :
[http://www.linuxquestions.org/hcl/showproduct.php/product/1730](http://www.linuxquestions.org/hcl/showproduct.php/product/1730)
As the driver CD provided is only for Win XP, I guess I'll have to go on a hunt..

OK, Now as per this blog/link:
[http://rajeshjayaprakash.in/conexant.html](http://rajeshjayaprakash.in/conexant.html)
I'm gonna start my journey .. :) 
This seems to be a good step-by-step informative link. 
Ok .. 
Problem :
> Locate the file CnxEtU.sys from your Windows setup CD for the driver and copy it to Linux.
The file CnxEtU.sys is not available in the provided Driver CD, nor in the WinXP CD nor in my 
<windows partition>/windows/system32/drivers/ folder.. :confused: 
So where do I go from here?
Any download driver link for this?

Cheers...


**EDIT:**
Posted here is the Search for ***.sys** in my modem driver CD :

[IMG]http://img205.imageshack.us/img205/7209/searchresultsat5.jpg[/IMG]

So .. Is the modem Conexant based at all?
Any other workaround for this rather than have the ** CnxEtU.sys**  file?

---

### Post by =CrAzYG33K= on 2007-04-28
uh ..Any pointers ??
OR
Any other totally different solution to this??

---

### Post by naveenroy on 2007-05-11
See if this helps by any chance...

[http://www.ubuntu-in.org/wiki/Broadband_Howto#Airtel_Broadband](http://www.ubuntu-in.org/wiki/Broadband_Howto#Airtel_Broadband)

---

### Post by lich 6222 on 2007-05-11
hi !
that what I did
I just ask the help Desk of  my  internent server
after 24 hour the send me a script to my e-mail
and another 24 hour to get it install
BTW i change my internet  server/provider  to one who support linux
  I  have a Astec  ADSL 2+ ....router 600E
[email]Schoulaker@gmail.com[/email]

eli

---

### Post by vigyani on 2007-09-29
I faced the same problem i.e. I had an old USB ADSL modem (Tera 100 U) from Beetel. Windows shows it as GlobeSpan Virata ADSL Modem.

I wanted to reuse it for BSNL Broadband Dataone connection under Ubuntu 7.04 (feisty).

I download the driver  (EciAdsl stable 0.12, 2007-08-13)  from [http://eciadsl.flashtux.org/download.php]("http://eciadsl.flashtux.org/download.php") for Ubuntu and installed it.

After installing I configured[http://eciadsl.flashtux.org/tutorial.php]("http://eciadsl.flashtux.org/tutorial.php") it using the following text based command:

sudo eciadsl-config-text

Following is the configuration for the modem (I could make it work after long struggle: I had to find out what are VID1; PID1 etc. Following settings work fine for me on HP NX6310 and Acer Aspire 4710 laptops.)

VID1=0f70
PID1=0001
VID2=0915
PID2=0002
MODE=VCM_RFC2364
VCI=35
VPI=0
FIRMWARE=/etc/eciadsl/firmware00.bin
SYNCH=/etc/eciadsl/synch02.bin
PPPD_USER=username_provided_by_BSNL
PPPD_PASSWD=
USE_DHCP=yes
USE_STATICIP=no
STATICIP=
GATEWAY=
MODEM=Other
MODEM_CHIPSET=GS7070
SYNCH_ALTIFACE=4
PPPOECI_ALTIFACE=4
PROVIDER=Other
DNS1=
DNS2=

It works fine for me. Modem disconnects after 24 hours. Hence I have to reconnect it after every 24 hours.

Do let me know if works for you.:)

regards
Vig

---

### Post by =CrAzYG33K= on 2007-11-09
> **vigyani said:**
> I faced the same problem i.e. I had an old USB ADSL modem (Tera 100 U) from Beetel. Windows shows it as GlobeSpan Virata ADSL Modem.

I wanted to reuse it for BSNL Broadband Dataone connection under Ubuntu 7.04 (feisty).

I download the driver  (EciAdsl stable 0.12, 2007-08-13)  from [http://eciadsl.flashtux.org/download.php]("http://eciadsl.flashtux.org/download.php") for Ubuntu and installed it.

After installing I configured[http://eciadsl.flashtux.org/tutorial.php]("http://eciadsl.flashtux.org/tutorial.php") it using the following text based command:

sudo eciadsl-config-text

Following is the configuration for the modem (I could make it work after long struggle: I had to find out what are VID1; PID1 etc. Following settings work fine for me on HP NX6310 and Acer Aspire 4710 laptops.)

VID1=0f70
PID1=0001
VID2=0915
PID2=0002
MODE=VCM_RFC2364
VCI=35
VPI=0
FIRMWARE=/etc/eciadsl/firmware00.bin
SYNCH=/etc/eciadsl/synch02.bin
PPPD_USER=username_provided_by_BSNL
PPPD_PASSWD=
USE_DHCP=yes
USE_STATICIP=no
STATICIP=
GATEWAY=
MODEM=Other
MODEM_CHIPSET=GS7070
SYNCH_ALTIFACE=4
PPPOECI_ALTIFACE=4
PROVIDER=Other
DNS1=
DNS2=

It works fine for me. Modem disconnects after 24 hours. Hence I have to reconnect it after every 24 hours.

Do let me know if works for you.:)

regards
Vig

Thanks for the heads up Vig :popcorn:
Ok - will try this later on....

---

