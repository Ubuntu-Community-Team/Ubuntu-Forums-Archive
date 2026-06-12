---
title: "Firefox browser problem"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by MrChips on 2005-12-18
My browser will not open pages on the internet!  

I have configured my dial up modem to dial the ISP.
I can dial up the ISP and establish a connection.
But after this is done...

I open the firefox browser and it says it cannot find the google page (set as home page) or any other page for that matter.

What can I do to correct this?:confused:

---

### Post by cstudent on 2005-12-18
See if you can ping the Google site.

In the terminal enter:

ping -c 5 [www.google.com](www.google.com)

---

### Post by aysiu on 2005-12-18
First of all, see if it's a Firefox issue or an internet connection issue.

Can you open a terminal and type ```
sudo apt-get update
```? Does it work? If so, you have a Firefox problem. If not, you have an internet configuration problem.

---

### Post by MrChips on 2005-12-18
On both tries...only failure.:???: 

Terminal:  Typed in the google config
 I got back     unknown host [www.google.com](www.google.com)

Tried to get the updates and it failed to "fetch" the webpage at ubuntu.

So I guess my internet config is not right.

---

### Post by MrChips on 2005-12-18
After a little digging I think I may have an IRQ conflict.  The nvidia pci card and the modem are both sharing IRQ 16.  This may be my problem.

I'll be back....

---

### Post by bscbrit on 2005-12-18
At the command line, type the following:

ping -c5 64.21.33.9

and let us know the results please.

I think that this might simply be a case of there being no DNS set up.

---

### Post by MrChips on 2005-12-18
The results:

PING 64.21.33.9 (64.21.33.9) 56(84) bytes of data.

--- 64.21.33.9 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

I hope this sheds some light?  Maybe?

---

### Post by bscbrit on 2005-12-18
OK, you are not even getting out to the internet!  Please confirm that you dialled up a connection before running the ping command - if not, it was probably my fault for not making it clear.  If you were online when you 'ping'ed, you were not getting anywhere.  Have you got a firewall installed?

---

### Post by MrChips on 2005-12-18
Unless Ubuntu has a firewall on it I don't believe there is one active.
In sequence: 

I activated the modem
Waited for the number to dial and all the analog squelching afterwards to cease
Checked the phoneline for connectivity (reciever pick up-noise on line)
Then commanded the ping and got the above results

  PING 64.21.33.9 (64.21.33.9) 56(84) bytes of data.

--- 64.21.33.9 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

I am just at a loss....:???:

---

### Post by bscbrit on 2005-12-18
Is there any indication that you log-on has been accepted by your ISP.  The fact that the telephone dials and tries to connect does not necessarily mean that it has succeeded.  Is it an external modem (perhaps with some LEDs to let us know what is happening) or is it an internal modem?

There is no default firewall with Ubuntu.

---

### Post by MrChips on 2005-12-18
Internal, and there is no way for me to know (LEDs) if I have succeeded in logging in to my ISP.  Unless Modem Lights for Ubuntu does that, but of course I need an internet connection to get it.  You can see the frustration here...

But at least I know the modem works.  It came from another computer after I went through the winmodem song and dance.

---

### Post by bscbrit on 2005-12-18
Just tryng to think this one through - I don't use a dial up so I cannot even test some of my theories on a local machine.

How do you 'activate' the modem?

Have you read (and followed the instructions in) this link:

[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

Have you had this modem working previously? e.g. under Windows?  What make and model is it?  

Does it show up in System -> Administration - Networking ? And check the settings please.

ps. I'm going offline for an hour or two, but I will be back on later.

---

### Post by MrChips on 2005-12-18
Yes to all of your questions.

The model: US robotics 5610 56k faxmodem w/ 3com chipset

I activate the modem through the terminal command   sudo pon
This was configured through the pppconfig which I might note did not automatically detect the modem.

The only odd thing about the configuration in device manager is that the port is set at /dev/ttyS14.  That is way off from the line up it gives you to set up the modem.  I have reinstalled twice and Ubuntu keeps putting the modem on /dev/ttyS14.

I am going to give this a rest for a while as well.  I appreciate your help.:) 

I'll be back....

---

### Post by bscbrit on 2005-12-18
Well, I suppose that the fact you can hear your modem dialing out means that both it, and ubuntu, are content on /dev/tty14.
Under System -> Networking -> Modem Connection -> Properties -> Options, check that the modem is set as the default route to internet, and that you are using that appropriate nameservers.  Just out of interest, what is in your /etc/resolv.conf ?  You may need to ensure that the nameservers show up there which is where the computer will look for them - I am assuming that ticking the 'Use the internet server provider nameservers' option will do for you automatically. On the Network settings dialog, please check also that the modem is selected as the 'Default gateway device'.
To be honest, I am rapidly running out of ideas bacause each of the settings that I can think of we are checking, and finding them to be what I would expect.  But I am not a dial-up expert - I have a broadband modem/router and haven't done much with modems for quite some time.  However, we have a few things left to try, so lets not give up yet!

---

### Post by MrChips on 2005-12-18
There is nothing but fetchmail in etc/resolvconf.

The box in  'Use the internet server provider nameservers' is checked.

BUT Ubuntu will only allow me to select eth0 as my default gateway.  There is not a modem option here.

^^
Maybe that one is the prob.  Hopefully...

---

### Post by bscbrit on 2005-12-18
Well, it might be, But I haven't got a clue how to fix it.  I'm going to have to give this some thought unless someone else can jump in with help.

---

### Post by bscbrit on 2005-12-18
Have you got the DNS addresses for your ISP?  If not, who is your ISP?  My /etc/resolv.conf contains the following:

nameserver 195.244.192.66
nameserver 80.84.64.20
nameserver 195.244.192.6


I use name servers from 2 different locations - the chance of them both going down at the same time is negligible - and one of the locations has 2 separate servers.

---

### Post by MrChips on 2005-12-19
OK

I've gone back and redone everything which brings us to this point with the nameservers.  Now I have two IP's in resov.config but they do not match the IP's I connect to my ISP with Windows.  btw...the ISP is ATTworldnet.  And I did try replacing the IP's that worked w/ windows too.

But STILL no connection!!!

I'll tell ya,  I'm just about done with it...:confused: 
DSL will supposedly be available in my area soon and maybe I should just wait until then.  For now I'll just shoot through the network for a shared connection with Windows. 

I hope that goes well...:???: 

Thanks for your help bscbrit!! :)

---

### Post by linuxguiri on 2005-12-29
I've been having similar problems with dial-up/fireworks. For me the issue was that the 'default route to internet' option was checked under properties. Once that was checked, it seemed to work (I may have needed to reboot and dial-up before starting Fireworks too, I can't remember). I couldn't tell whether you had tried this option from reading your posts.

I'm not too happy with the dialer panel as there is not a quick, easy way to connect/disconnect. Right now, I'm trying to use gnome-ppp (as recommended in [DialUpModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems")) but I'm having the same issue as before with Fireworks thinking the computer is offline when it isn't. There doesn't seem to be a checkbox for setting the modem as the default route in gnome-ppp.

---

### Post by ladyeldawen on 2006-03-02
[QUOTE=linuxguiri]I've been having similar problems with dial-up/fireworks. For me the issue was that the 'default route to internet' option was checked under properties. Once that was checked, it seemed to work (I may have needed to reboot and dial-up before starting Fireworks too, I can't remember). I couldn't tell whether you had tried this option from reading your posts.

I'm not too happy with the dialer panel as there is not a quick, easy way to connect/disconnect. Right now, I'm trying to use gnome-ppp (as recommended in [DialUpModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems")) but I'm having the same issue as before with Fireworks thinking the computer is offline when it isn't. There doesn't seem to be a checkbox for setting the modem as the default route in gnome-ppp.[/QUOTE]


 Hey, I've been having the same problem with gnome-ppp. There is a way to set it as the default route, but it's not quite as warm and fuzzy as checking a box (alas.). Type in the following into the terminal:

$  sudo gedit $HOME/.wvdial.conf

 This is the wvdial file that gnome-ppp creates in your home folder. My problems were solved by editing the line

Stupid mode=ON

And you can solve the problem of being recognized as the default route by simply adding the line "defaultroute" . Save the file, and you should be good to go!

---

