---
title: "Kubuntu users , Please tell me how to connect to internet with external dial-up"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-07-20
Hope i made that title good enough...

Anyway , Could i please have a kubuntu user explain to me how to connect to the internet with an external dial-up modem..???

I bought a new one today ( **Creative Blaster v.92** ), and i can't figure out how to connect using **Kppp** in the K-Menu..!

The modem works in ubuntu dapper just fine...   Should that be logged or saved somewhere as **Known working hardware** somewhere here in the forum..???

Thanks everybody...:-D

---

### Post by jason.b.c on 2006-07-20
Here's the modem i've got now , Hey at least i can get on the internet with ubuntu now..

[Creative modem blaster v.92 external]("http://us.creative.com/products/product.asp?category=7&subcategory=40&product=258")

I tried and tried to figure it out on my own , But still don't understand how...   Oh .! And by the way , Please take note that i was trying this running as **"live"** CD..That dosen't matter dose it.??

---

### Post by jason.b.c on 2006-07-20
*Bump*

---

### Post by Handyman's Special on 2006-07-21
Hello Jason,

I am using an external modem. I am very new to Ubuntu & Linux in general but this is the one thing I have been able to learn how to do. I don't know if I do it right but it works everytime for me. Try this:

Click on System (on left at the top of the screen you will see Applications  Places   System - that is the System to click on)
Next click Administration and then Networking
(you will be asked to enter your password - do that)
A small window will open, titled "Network Settings"

Click on the empty space to the right of "Location," enter a name you wish to give the connection. (I use the name of my ISP, earthlink)

On the CONNECTIONS TAB: (I changed nothing on the GENERAL, DNS and HOSTS TABS)
> click on the red telephone (to highlight the Modem connection)
> Then click on Properties

Another little window opens with tabs,
On the GENERAL TAB:
>Click in the box next to Enable this connection (make it have a checkmark)
>enter the number needed to dial your connection
>enter you user name and password

On the MODEM TAB:
>Click Autodetect
>select Dial type
>Select the Volume (This has not yet worked for me, mine is still noisy)

On the OPTIONS TAB:
(I have a checkmark in each of the three options on this tab)

Click on OK

To activate the modem I 
1) go to Networking,
2) click the arrows on the Location and choose 'earthlink' (or whatever you name yours)
3) Click on the Red phone (it should say the interface ppp0 is not active) 
4) Click on the Activate button to the right.

Hope this helps,
Handyman's Special

---

### Post by jason.b.c on 2006-07-21
> **Handyman's Special said:**
> Hello Jason,

I am using an external modem. I am very new to Ubuntu & Linux in general but this is the one thing I have been able to learn how to do. I don't know if I do it right but it works everytime for me. Try this:  ...............


Hope this helps,
Handyman's Special

All that stuff is for **Ubuntu Dapper** , I know how to do it in that , What i need is how-to in **Kubuntu**.....:D 

Thanks.....

---

### Post by editrix on 2006-07-21
> **jason.b.c said:**
> Hope i made that title good enough...

Yes, you did. It's a paragon of how a title should work. :-)

I'll assume you've read the Dialup modem Howto
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

> **jason.b.c said:**
> i can't figure out how to connect using Kppp in the K-Menu

What, exactly, can't you figure out? Once you hit "Configure" in KPPP, what don't you understand?

---

### Post by jason.b.c on 2006-07-21
> **editrix said:**
> 



What, exactly, can't you figure out? Once you hit "Configure" in KPPP, what don't you understand?


Because then nothing happens..!!   

I'm told ( error message ) that the **modem is not found.!**  

It's an external serial modem and i can't seem to detect it...

---

### Post by Madmat on 2006-07-21
Jason,
I too am having a problem with an external modem on Kubuntu (6.06).
I had a modem inside and had the same problems with it and found that it was a winmodem and replaced it with a modem model recommended by a forum user.  External serial modem.  Best Data.
I configure the modem in KPPP just as you did (I guess), making sure that the address is correct - /dev/ttys0 for mine.
Then I would query the modem from one of the tabs in the configuration  screens.  At first it was not detected.  I then clicked OK and left and came back and requeried it and it was found.
I found the address by using 
  [SIZE="2"][FONT="Arial"]sudo wvdialconf /etc/wvdial.conf[/FONT][/SIZE]
Also, in the terminal you can type in
[SIZE="2"][FONT="Arial"]ifconfig[/FONT][/SIZE]
which will tell you all of the NICs found by the system (I think - man this and it will tell you more).
ifconfig does not find my modem in my system however, wvdialconf does.  I still have a problem making a connection, but at least it dials out.
I probably know less about linux than you, but I hope my problems have at least gotten you another step toward success.

---

### Post by editrix on 2006-07-22
> **jason.b.c said:**
> Because then nothing happens..!!   

I'm told ( error message ) that the **modem is not found.!**  

It's an external serial modem and i can't seem to detect it...

Ah. How frustrating.

I have to admit, the only problem I had with an external modem was that at first, I'd plugged the jack into the wrong socket--there are two at the back of my machine. And, please don't be insulted, but is the modem turned on? And is it securely screwed in? Also, have you tried it in Windows? It's possible (but not likely) the modem's defective.

Ordinarily, external modems just work, and I'm not expert enough to help you diagnose any software problem that could be going on. But keep trying. The problem is likely something minor--and obvious, once you find it.

---

### Post by Madmat on 2006-07-22
Jason,
If you are still having the same problem, I would like to encourage you that I am now online from my KDE machine.
I got some advice from zxee to use the terminal and type:  _sudo pppconfig_
This was a piece of cake, but I did need to know the address of the modem.  This is where the command:  _sudo wvdialconf  /etc/wvdial.conf_   was helpful.  It gives the address.
Anyway, after sudo pppconfig was finished I typed in: _pon provider_  and the modem dialed out, made a handshake and I was online.  Then, back to the KDE desktop and Konqueror to work.  Next, to install Firefox.
By the way, I used: pon provider  because I left the name of the provider field in pppconfig as provider instead of the name of my provider.  This I did because the instructions recommended it.
Good luck.

---

### Post by Matchless on 2006-07-22
Jason,
      Kppp works very well, but may be a bit tricky to configure first time. It is also required that your eth0 nic is also correctly set up as it can influence the working of kppp. I am assuming that you are not going to connect anything to the nic at first, set up Kpp then as follows:
**_Howto connect to the Internet with Kppp_**

Kpp is a very nice dialler, but can be a bit finicky to set up. if something small is not correctly done it fails and does not give you a very clear indication as to what happened. It could also affect you not logging in if the network card settings are incorrect. It is also important to reboot everytime a network setting was changed before testing!!  If you are going to use Kppp first go to the file /etc/ppp/peers/kppp-options 
and right click on it, Actions, Edit as root. Now remove the #noauth comment to change it to noauth and save.
Kppp uses the pppd, point to Point protocol daemon.

To use Kppp you first have to configure it properly and there are a few steps that has to be done carefully.

Configuring your modem:
Physically install your modem and the drivers if it is a USB or internal modem. External serial port modems do not require drivers. Most modems can be configured to work on Ubuntu. Howto's and Wikki's are available.
Open Kppp, select Configure and the Modems tab. 
Under the Device tab enter :
Modem name: The name of your modem
Modem device: select the device that is connected to your modem
                  /dev/ttyS0 is normally a serial modem connected to com1
                  /dev/modem is normally used for most internal modems as a symlink
Flow control: Hardware [CRTSCTS]
Line termination: CR
Connection speed: 115200
Uncheck Use lock file box
Set modem timeout to max – 120seconds
Click OK to save

Now go to the Modem tab
Check box Wait for dial tone before dialling
Busy wait set to 20 seconds
Modem volume to what you prefer

Now click on Modem Commands
In Initialisation string 2 type in the following:  ATQ0 V1 E1 S0=0 &C1 &D1 +FCLASS=0
Click OK

Now click on Query Modem
This is the most important test as it will show if Ubuntu recognises your modem on the device you specified and also confirms that the drivers have been correctly installed.
It will spit out a list of results that it gets from the modem if it can see it. If this fails first make sure that you have pointed to the correct device, or check that the correct drivers have been installed.
Close this

Now go to the Misc tab
pppd timeout set to max 60 seconds
check box Show clock on caption
check box Disconnect on X server shutdown
check box Minimise window on connect
leave the others  unchecked

Configuring your account:

Go to the Accounts tab and New and type in the name of your ISP
Now click Dial and Add and enter the number you dial to connect to your ISP
Also select PAP for Authentication and ensure that the store password boc is checked.
Click IP and check Dynamic IP address box.
Click Gateway and check Static gateway and enter gateway IP address 192.168.0.1 
Leave Assign the default route to this gateway box checked.
Click DNS and check box Automatic.
Leave box Disable existing DNS servers during connection unchecked

Now close everything and open Kppp to the initial login window and check that your ISP name shows as well as your modem. Now enter your login ID and password. Check box Show log window.
Now you are ready to dial out, but first you must ensure that your network card is correctly configured as well. For a standalone PC go to System Settings, Network settings and in Administrator mode ensure that the following settings are enabled. Dynamic/automatic IP DHCP, Default gateway – leave empty, Domain Name Server DNS – leave empty, Static Hosts leave as was installed by default.
Reboot your PC and go online and browse.

Please note that if you change your network card settings, such as when you want to do internet sharing and install Firestarter, then there is a change that has to be done on Kppp where you will have to install the DNS IP's provided by your ISP as well as a static gateway IP 192.168.0.1
You also have to change your network settings to a manual IP 192.168.0.1 and the default gateway leave empty. Set DNS to IP 192.168.0.1
Do not forget to reboot after any changes made to any network or modem settings.

---

