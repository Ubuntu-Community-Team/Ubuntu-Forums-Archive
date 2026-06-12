---
title: "Pairing W850i using phone manager"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2007-05-31
I have installed phone manager and my bluetooth dongle had found my phone, when it trys to add ubuntu it asks for a pass code. I have tried the default bluetooth 0000 and my phones security code which didn't work. Does Phone Manager have a pass code?

Cheers

---

### Post by MikeJ112 on 2007-05-31
Have also tried 1234 which is in hcid.conf

---

### Post by Inxsible on 2007-05-31
Make sure that the security is auto and not user.

Look for a line ```
 security user;
```
Change it to ```
security auto;
```

and it will pair !!

---

### Post by MikeJ112 on 2007-05-31
Is this in hcid.conf?

---

### Post by MikeJ112 on 2007-05-31
Yeh i can see it now, what do I need to type into terminal to edit it, as its read only?

---

### Post by Inxsible on 2007-05-31
oh sorry..should've explained better
```

gksudo gedit /etc/bluetooth/hcid.conf
```

Change and save

---

### Post by MikeDX on 2007-05-31
gksudo gedit path/to/hcid.conf

that'll do it ;)

obviously replace path/to with the path to hdic.conf....

** edit 

somebody beat me to it! ah well...

---

### Post by MikeJ112 on 2007-05-31
Ok cool, i edited that, rebooted and connected the phone to ubuntu, and ubuntu is showing up as a paired device on my phone. Phone manager still wont connect tho :S?

---

### Post by Inxsible on 2007-05-31
> **MikeJ112 said:**
> Ok cool, i edited that, rebooted and connected the phone to ubuntu, and ubuntu is showing up as a paired device on my phone. Phone manager still wont connect tho :S?

When you say phone manager ...what do you mean ?

is that the name of the software ?

or are you using Wammu ?

---

### Post by MikeJ112 on 2007-05-31
Phone Manager is the name of the software yeh. Whats Wammu?

---

### Post by Inxsible on 2007-05-31
> **MikeJ112 said:**
> Phone Manager is the name of the software yeh. Whats Wammu?

Sorry, i have never used Phone Manager (never heard of it infact ;) )

Wammu is used to connect to your phone and make backups of all contacts, sms messages, calendars, todos etc.

I have my W810i connected thru Wammu.

What does Phone Manager do exactly? ..

hmmm...will have to research on it :)

---

### Post by MikeJ112 on 2007-05-31
Phone manager allows you to send and recieve SMS via bluetooth from the app. If Wammu does this I will probably download it!

---

### Post by Inxsible on 2007-05-31
> **MikeJ112 said:**
> Phone manager allows you to send and recieve SMS via bluetooth from the app. If Wammu does this I will probably download it!
 
Yes, I think Wammu does that.
 
[http://wammu.eu/](http://wammu.eu/)
 
```
sudo aptitude install wammu
```
 
Make sure you will require a couple more libraries along with it. If i remember correctly they are called python-bluez and gnome-bluetooth. If I am wrong, when you put in the above command it will tell you what else you will need and you can install those accordingly
 
```
sudo aptitude install wammu python-bluez gnome-bluetooth
```
 
 
BTW, I think this would be a great utility since, you wont have to struggle with the smaller keypads on the phone to compose SMSes..(they keep getting smaller and smaller :rolleyes: )
 
Or course Wammu can also be used to copy over your contacts todos calendars and other info from one phone to the other :)

---

### Post by MikeJ112 on 2007-05-31
Bringing this back up again, I can only seem to connect to my PC via the phone, I cant connect the PC to the phone (if that makes sense!)

---

### Post by MikeJ112 on 2007-06-01
Does anyone here have any experience with Bluetooth, still having the same problem :(

---

### Post by Inxsible on 2007-06-01
If you want to send a file from the computer to the phone, simply right click the file and select Send To

it will pull up a dialog and you can select your phone via bluetooth.

You should have the bluetooth file transfer app running to do this i think.

---

### Post by MikeJ112 on 2007-06-01
I can send a picture, sound etc to and from my PC using Bluetooth File Sharing ok. I'm unable to use Wammu tho or Phone manager. When I load Wammu and click search phone It doesnt find my device,  and when I try and add the PC as a device on my handset, i just get "Bluetooth connection failed"

---

