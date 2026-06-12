---
title: "Automatic Connection to Wireless Network"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Opera Rocks! on 2007-08-24
Hello,

Paul from Perth Australia here.  I have just decided to try Linux as I am sick and bloody tired of getting Viruses in XP.

Just a few questions:  

I am in Ubuntu at the moment and so far the only problem I can't solve is how to automatically connect to my home wireless network.

At the moment I manually enter my hex number to connect but I would rather not have to do this.

Any suggestions would be much appreciated!

Also, I installed firestarter firewall gui and modified some settings.  Do I need to have this program start at each boot or because it is just a gui can I just forget about it now?

I would be happy to provide more information if necessary.

Regards,

Paul (PS, Opera does rock! :))

---

### Post by walkerk on 2007-08-24
Give WICD a try. Check my signature.

---

### Post by Inxsible on 2007-08-24
another is nm-applet which is installed in Ubuntu by default. Wonder why it didnt kick start when you set up your wireless.

---

### Post by ajgreeny on 2007-08-24
No, you don't need firestarter at each boot up, only whenever you want to change settings.  In truth you probably don't really need it at all, though I know a lot of people feel happier with it on their machine.  It was always one of the first things I put on mine in the past, but for the past 18 months I haven't bothered with it at all.

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Hi Paul, welcome to ubuntu.
I'm surprised your wireless wasn't recognised automatically.
Yes, Opera rocks.
I used to run firestarter because of XP paranoia, but like ajgreeney I don't bother with it now.

good luck
ex freo boy[/FONT]

---

### Post by ntlam on 2007-08-24
my wireless sometimes does not work even it still says 75% signal strength.
I have an atheros card on my toshiba
do you know what problem it is. Is this a problem of my router or wireless setting?

---

### Post by Opera Rocks! on 2007-08-27
Thanks for the help.

I tried WICD but it didn't seem to like my computer and I couldn't connect :confused: (probably just me).

I've kind of made things easier for myself.  In the past when I first start Ubuntu, I firstly typed in my WEP Hex key and hit 'ok'.  

Then I got a message to 'enter pasword for the default keyring to unlock' and 'the application nm-applet wants access to the default keyring but it is locked'

I would just click 'deny' and I then would connect to the wireless network.

Last night what I tried to do was just put in a simple password.  Now, when I start Ubuntu, I get a prompt for the password, I type it and then connect without any trouble.

I hope this makes sense.  Is there a way of having the password automatically entered?

Also, I am struggling with the 'not needing Internet security' in Linux because I was always so paranoid in Windows.  I am trying though 8-[:neutral:

Cheers,

Paul.

---

### Post by ajgreeny on 2007-08-27
Just for your peace of mind go to:-
[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)
Here you can run the port scan facility.  Click on the "Common ports" button and see what is open, then try "All service ports".  If your machine is like mine there will be none open and all stealthed, ie no indication that there is a machine at the IP address.  Remember, I don't have a firewall configuration program on my machine at all, everything is just as ubuntu defaults left it on installation.

---

### Post by anewguy on 2007-08-27
You should check into PAM as well.  As long as your log on password and the keyring password are the same, PAM will automaticaly connect your wireless network at log in.  There are several posts, etc., about it on the forums.  I'd point you to the one I used, but it's been long enough now that I just don't remember.:)

---

### Post by pi3832 on 2007-08-28
> **Opera Rocks! said:**
> Thanks for the help.

I tried WICD but it didn't seem to like my computer and I couldn't connect :confused: (probably just me).

I've kind of made things easier for myself.  In the past when I first start Ubuntu, I firstly typed in my WEP Hex key and hit 'ok'.  

Then I got a message to 'enter pasword for the default keyring to unlock' and 'the application nm-applet wants access to the default keyring but it is locked'

I would just click 'deny' and I then would connect to the wireless network.

Last night what I tried to do was just put in a simple password.  Now, when I start Ubuntu, I get a prompt for the password, I type it and then connect without any trouble.

I hope this makes sense.  Is there a way of having the password automatically entered?




I haven't had to use it myself, but for the key-ring thing I was recommend to look at: [http://ubuntuforums.org/showthread.php?t=463639](http://ubuntuforums.org/showthread.php?t=463639)


Also, you do realize that WEP is [easy to crack]("http://www.wirelessdefence.org/Contents/AircrackMain.htm"), don't you?

---

### Post by anewguy on 2007-08-29
> **pi3832 said:**
> IAlso, you do realize that WEP is [easy to crack]("http://www.wirelessdefence.org/Contents/AircrackMain.htm"), don't you?

That's been a concern of mine as well.   I was never able to get WPA to work even under Windows.  Support said I needed to install AEGIS protocol.  Only thing I ever found on that was something I had to pay for, which I'm not going to do.  With this 2WIRE modem/router, I have turned on every possible combination of WPA type and key type and never got anywhere.  In Linux, the most it ever had gotten to is at least lighting up the wireless link light on the router, but Linux shows "attempting to join xxxxx network".  If I just change WPA to something else it never lights up the wireless link light.  The only way it ever works is to either leave it wide open or to turn on WEP.  Since WPA does light the link light, I assume that much is working, maybe even the key.  However, it just hangs on the "attempting to join xxxxx network" thing.  I suspect this might have something to do with this AEGIS protocol stuff I was told about. Do you know of someway to get this AEGIS protocol stuff for Ubuntu or have any other clue what might be going on?  Any help would be GREATLY appreciated!!:)

---

