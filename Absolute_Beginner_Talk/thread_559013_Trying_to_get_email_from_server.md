---
title: "Trying to get email from server"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by chebert on 2007-09-24
Hello everyone,
I just installed ubuntu and I am trying to log onto a server (windows based) but can't.  I installed the seemingly appropriate files from the web site on the server (citrix client).  I copied the Encoding]

InputEncoding=ISO8859_1



[WFClient]

ClientName=

ProxyFavorIEConnectionSetting=Yes

ProxyTimeout=30000

ProxyType=Auto

ProxyUseFQDN=Off

RemoveICAFile=yes

TransparentKeyPassthrough=Local

TransportReconnectEnabled=Off

Version=2

VirtualCOMPortEmulation=Off



[ApplicationServers]

Microsoft Outlook=



[Microsoft Outlook]

Address=;10;STA02;BA9023C39E8FBDCD0BB5928A5D0A947B

AutologonAllowed=ON

BrowserProtocol=HTTPonTCP

ClearPassword=6CA4DECC3F3864

ClientAudio=Off

DesiredColor=4

DesiredHRES=1024

DesiredVRES=768

Domain=\08AA20DCD900FC51

HTTPBrowserAddress=!

InitialProgram=#Microsoft Outlook

Launcher=WI

LongCommandLine=

ProxyTimeout=30000

ProxyType=Auto

SSLCiphers=all

SSLEnable=On

SSLProxyHost=sgserver1.ololrmc.com:443

SecureChannelProtocol=Detect

SessionsharingKey=4-basic-none-OLOLRMC-chebert-fmol1

TWIMode=On

TransportDriver=TCP/IP

Username=chebert

WinStationDriver=ICA 3.0



[Compress]

DriverNameWin16=pdcompw.dll

DriverNameWin32=pdcompn.dll



[EncRC5-0]

DriverNameWin16=pdc0w.dll

DriverNameWin32=pdc0n.dll



[EncRC5-128]

DriverNameWin16=pdc128w.dll

DriverNameWin32=pdc128n.dll



[EncRC5-40]

DriverNameWin16=pdc40w.dll

DriverNameWin32=pdc40n.dll



[EncRC5-56]

DriverNameWin16=pdc56w.dll

DriverNameWin32=pdc56n.dll

Don't know if this helps but I thought I try something.
Thanks for your help / advice.
chebert

---

### Post by kyphi on 2007-09-24
The way I get my mail from a server is to go via a programme called Mailwasher Pro.  This programme lets me see what mail I have and who it is from so that I can delete anything inappropriate before downloading it into Evolution.

If that is what you want to do, please reply and I will give you further information.

---

### Post by chebert on 2007-09-24
Thanks.
I appreciate this.  My problem is not being able to get to the mail (which is outlook that is on the server) after I am on the server.  The server has a link that one downloads the software but it does not install to my computer.  I just reinstalled ubuntu - 7.04.

---

### Post by kyphi on 2007-09-24
After having a look at the Help section in Evolution it seems that you may be able to access your mail server via Evolution.  Both Evolution and Thunderbird can do this, I believe.

The programme I use is a programme designed for Windows and I run it via Crossover but you can run it via Wine (which is the same).  Although several  Linux versions were being developed, this has now been abandoned since it runs on Wine.  Mailwasher is proprietary and closed source (cost 37 USD) and available from Firetrust.

Your server should be able to forward your mail irrespective of what operating system you use.  Perhaps you need to talk to your ISP.

---

### Post by kyphi on 2007-09-24
> After having a look at the Help section in Evolution it seems that you may be able to access your mail server via Evolution. Both Evolution and Thunderbird can do this, I believe.

The above was a rather silly statement.  Of course they can.

I have just accessed, from Ubuntu,  my server to check my mail.  Not a problem at all except for the rather convoluted way to access mail using this procedure.  No special programmes were necessary to do this.

Using Mailwasher, to reach the same objective, requires only one mouse click.

---

