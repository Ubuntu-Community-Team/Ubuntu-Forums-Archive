---
title: "Keyring fury"
date: 2012-02-08
forum: Any Other OS
---

### Post by danceswithcats on 2012-02-08
Venting works!  I just tried entering my password with caps lock on and it worked!  I feel very silly, but will leave the thread up as a warning to youth.

I'd still like to know how to turn the keyring off.  It is incredibly annoying.





Hello, 

I installed Bodhi linux, which appears to be ubuntu with a different graphic setup, on a laptop yesterday, because Lubuntu was a bit too fussy on a small screen for my old eyes. It was a long day, but it all looks very pretty and seems to work nicely, even if it is a bit of a change from normal Ubuntu.

I don't care about 'security' as I don't do anything financial on the laptop, and I thought I had set it to just do as it was told without demanding passwords every five seconds, but I must have entered a password at some point, as the 'unlock keyring' demand is repeatedly popping up when I'm just trying to use my computer.

The password I assume I entered-my 'it doesn't matter' password, isn't recognised.  I know I didn't use any of the passwords that I put on important things, but I've tried them anyway with the same result.  Is it possible to simply turn the keyring off? I just don't need to have my thinking bothered by constant (every minute or so) interruptions.  It's as annoying as the windows paper clip, just to give an idea of the frustration.

To cap it all, I can't get the computer to enter boot menu, so that I can re-install.  FURY!!!

Thanks in advance.

Sorry about this.  Have to vent.

---

### Post by danceswithcats on 2012-02-08
THis is probably the most pointless thread ever.  However, I have found this in the Bodhi linux wiki.  Very helpful and recommended for anyone having the same troubles.


[I]Why do I have to enter a password to unlock the Network Manager Keyring?

Even though you have configured Bodhi Linux (at installation time) for auto-login, the Network Manager still asks you for your password at every boot to unlock the mysterious “keyring”. You can eliminate this hassle easily.

Delete the file(s) in /home/<username>/.gnome2/keyrings/

Log out, and then log in again (or reboot).

As Network Manager starts up, it will ask for your WEP/WPA key (which had been stored in the deleted file).

At the same time, another window pops up asking you to create a password for the default keyring. This time instead of creating that password, leave the fields blank and hit ENTER.
A warning about security pops up, which you can dismiss.

Now, when you start up, you will not be asked to enter the password for the default keyring.
[/I]

---

### Post by nothingspecial on 2012-02-08
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by sunewbie on 2012-02-09
nice tip thanks I have bodhi 1.3 installed along with Xubuntu 11.10 and I like it :)

---

### Post by markMDW on 2012-02-09
For what its worth I always have a dialog box pop up at bootup now, "_Unlock Login Keyring_".  It's been happening ever since I changed my login password in Ubuntu 10.04, and says,
> "enter password to unlock your login keyring.  The password you use to login to your computer no longer matches that of the login keyring.  ...  Password ________    [cancel] [ok]  "

anyhow, I simply enter my prior login password to open the keyring.  Everything then works including my wi-fi to dsl router.  

One other thing.  I had booted from live CD earlier today with Bodhi 1.2.1.  The wi-fi asks for my dsl router password.  I enter it but Bodhi attempts to connect without success.  Eventually it asks again but nothing works.   I like Bodhi.  It's amazingly innovative for such a light operating system.  I wish I new why I can't connect to my dsl with it though.   I also tried Lubuntu 11.10 from live CD today and had that same problem.  A friend with a Windows 7 laptop has had the problem as well. 

But my desktop with Ubuntu 10.04 installed, and my laptop with xubuntu 10.04 are both able to connect just fine.  I just have that annoyance with the keyring dialog asking for the old password for my desktop at bootup.    

I haven't tinkered, trying to figure out how to get my Ubuntu desktop to  accept my newest password automatically.  It's a small annoyance to have to  enter two passwords; there use to never by the Keyring  thing popping up.  

I suppose if I deleted the wi-fi connection from my network manager's "automatically connect" que, and then reestablish it and set it back up to "automatically connect" then the keyring manager wouldn't pop up again unless I changed my login password.  But I'm just afraid of the strange problem that I've experienced with Bodhi, Lubuntu and Windows7 and having that creep in to my clean Ubuntu install.  Then I might not be able to connect to wi-fi at all   #-o

---

