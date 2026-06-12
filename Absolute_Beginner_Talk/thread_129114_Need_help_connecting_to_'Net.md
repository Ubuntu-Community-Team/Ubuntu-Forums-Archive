---
title: "Need help connecting to 'Net"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Chappy on 2006-02-12
I posted a post w/this same title nearly a month ago when I was fooling around w/the Ubuntu Live CD. Well, I got the CDs from Ubuntu and managed to install Ubuntu this eve. What is the 1st thing a newbie wants to do, connect to the net. After an hour or so of looking around I finally shut Ubuntu down and came here to ask.

Can someone please tell me step by step how to connect to the net? I am using a hardware modem that connects fine w/Xandros, so it should be ok in Ubuntu. Where do I go in Ubuntu to find the dialup/connect via Modem file? I looked under Networks, and everything that looked at all related to what I wanted. I found a box that asked me who I was calling, the number, my User ID and password, etc. I am sure that I was real close. My ISP has static IP and domain. In Windows and Xandros connecting to the net is ez. I am sure it is me, nit Ubuntu that is the problem. 

So, please, someone walk me thru this. Starting w/where I find what I need. Do I let the modem detect it's tty/dev thingie. (I already said I am a newbie, so go ahead and laugh. I'll get there eventually!)

Thnx in advance to those who help me w/this. I appreciate it. I have gotten alot of help from this forum so I know you guys will come thru.

God bless and take care,
Chappy
 		 	 		 		 		 		 			 				__________________

---

### Post by orlox on 2006-02-13
As far as I know, hardware modems are easily detected by ubuntu, so the problem might not be from hardware detection. I'm not sure if this will work (just tried it, and the modem dials up but fails at some point, probably because i made a mistake when entering the data...). Just enter a terminal and type:

sudo pppconfig

and create a new connection. At some part of this, It will ask you if it should try to autodetect your modem. Symply type yes, and if it fails and makes you manually enter your modem port, type /dev/modem. After making and saving the connection you just made, exit pppconfig, and in the terminal type:

pon <connection-name>

where "<connection-name>" should be replaced with the name of the connection you just made. in case your connection is named provider, you can simply type:

pon

to end the connection, simply tipe poff. If you want to see whats happening after "poning", type plog.

Hope this works with you. I went through hell to make my softmodem work so i'm not pretty sure if this will work for your hardware modem. If it dials at least (like it just did with me) you can rest assured that at least yours is not a hardware detection problem...

---

### Post by Bartender on 2006-02-13
Are you SURE it's a full hardware modem?  I'm almost positive that some externals still rely on Windows to do part of their work.  Can you supply a brand, model?
Have you followed the steps outlined in the Wiki?

[https://wiki.ubuntu.com/DialupModemHowto#head-cdd16131926f734c4736b833b907c8fb24478187](https://wiki.ubuntu.com/DialupModemHowto#head-cdd16131926f734c4736b833b907c8fb24478187)

---

### Post by Chappy on 2006-02-13
My modem is a USR Sportster 56K X2 Internal. It is fairly old, and goes into an ISA slot, so I am 100% sure it is not a winmodem. I bought it 7 or 8 yrs ago, long before software modems, nevermind winmodems, were available.

As I said, I have it working on Xandros. Xandros picked it right up when I asked it to "find modem", or whatever. Xandros sees it as a Standard 56K Modem, comm 6. But I can set it as a USR Sportster 56K (disable X2), and it will connect. Xandros seems just as fussy towards winmodems vs hardware modems. I had a winmodem in the machine and Xandros would not find it.  Nor could I get it to work. The difference between Xandros and Ubuntu is that Xandros has a Connect to Internet Wizard that lays it all out. I guess that is the attraction of Xandros (partly). There is no need to type in any commands or know any Linux, which, being a brand newbie, I don't.
 
Is there nowhere in Ubuntu where one can just fill in a "Connect to Internet" box? Something similar to Xandros?

Thnx for the above answers,

Chappy

---

### Post by ferebee on 2006-02-13
I'm no expert, but you could try this.
For connecting the first time, I go to System> Administration>Networking 
In the box you should see  'Modem Connection' and underneath that
'The interface ppp0 is inactive'

Click on 'Properties' to enter your  username 
and password for your isp,and the number you use to dial in. Be sure to click the enable this connection box.
Then click the Modem tab to enter the modem port. It gives you the option to auto detect here and this worked for me, 
but your mileage may vary. 

In the 'Options' tab check the first two boxes and click okay.

You should be able to then click on the 'activate' button in the main window to get connected, and 'deactivate' to hang up. 

I'd then go to either Synaptic under the Administration menu or
 Add Applications under the Applications menu and download and install GnomePPP. 
It's similar to kppp and gives you more options for configuration. 
After installing this you shouldn't need to use the
System>Administration>Networking method.

This worked for me, I hope it works for you.

---

### Post by Chappy on 2006-02-13
Thnx so much ferebee for the well written instructions. I'll let you know how I do after I try it. Are you saying that I will have to go thru the whole process you wrote each time I want to go online until I download and install Gnome PPP? I wish ubuntu had included that since I am a 100% new newbie, and have no idea how to install using Linux. I guess I will figure it out. Anyhow, just wanted to say thanx.
.

---

### Post by ferebee on 2006-02-13
[QUOTE=Chappy]Thnx so much ferebee for the well written instructions. I'll let you know how I do after I try it. Are you saying that I will have to go thru the whole process you wrote each time I want to go online until I download and install Gnome PPP? I wish ubuntu had included that since I am a 100% new newbie, and have no idea how to install using Linux. I guess I will figure it out. Anyhow, just wanted to say thanx.
.[/QUOTE]

I think that Networking should remember your settings from one session to the next, but Gnome PPP is more like a conventional dial up program. 
You might have to play with the settings to get it working properly, 
but then I had to do that in Windows too.

I'm thinking it wasn't included because Dial-Up seems to be going the way of
the dinosaur. That isn't so great for those of us who are  stuck with it though, is it?


Installing is easy when you use the Add Applications program.  
When you start it, it will take a minute or so to resolve dependancies, 
then when it is ready, you'll find a list not unlike your applications menu.
Expand the Internet menu, then expand the 'more programs' menu.
GnomePPP is there; check the box then 'apply'. The program 
is downloaded and installed automatically. 
You can download and install a lot of  software with Add Applications
or Synaptic, and both are pretty easy.

There's a good guide to Synaptic here:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

You'll probably come across some applications that you'll need to install
using the command line, though. There is a guide here:
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

---

