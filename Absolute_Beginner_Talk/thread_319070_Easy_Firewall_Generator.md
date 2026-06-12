---
title: "Easy Firewall Generator"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by ityro on 2006-12-15
I now have three weeks experience with Ubuntu ver 6.06 LTS on a standalone HP notebook. It is for home use only and has a cable connection to the internet. I am EXTREMELY happy with the system, forums and documentation. My biggest problem so far has been me.

I installed Firestarter but have not been able to get it to start/run automatically using instructions provided by the forums and Firestarter Home Site. User privileges problem. Bottom line, I do not feel comfortable with it.

So, there is an "Easy firewall generator for Iptables" at the following site: [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)

It appears to cover my needs same as Firestarter but the firewall will be permanently modified and "running" all the time. A one-stop solution.

Has anyone out there had experience with the Easy Firewall Generator? Is it a reasonable solution? How do I undo it?

Thanks for your time . . .

---

### Post by mcduck on 2006-12-15
With Firestarter the firewall *is* always running. 

Firestarter GUI is just a frontend tool to change your iptables firewall's settings. There's absolutely no need to have the GUI open all the time, in fact it's better not having it open as it runs with root privileges and having unnecessary root apps open is not a good idea..

---

### Post by Wim Sturkenboom on 2006-12-15
It's not necessarily always running. It does not start on my system till I invoke pppoe.

---

### Post by steve.horsley on 2006-12-15
> **mcduck said:**
> With Firestarter the firewall *is* always running. 


I understand from other threads that firestarter is a two-part application. Apart from the GUI, there is a daemon of some sort that configures iptables when it starts (and presumably thereafter goes to sleep). I also read that there is a bug that prevents the daemon from starting at boot when it should. I remember that the fix was a one-line change to a script somewhere, but I don't remember the details. I got all this info from threads in these forums though.

---

### Post by mcduck on 2006-12-15
> **steve.horsley said:**
> I understand from other threads that firestarter is a two-part application. Apart from the GUI, there is a daemon of some sort that configures iptables when it starts (and presumably thereafter goes to sleep). I also read that there is a bug that prevents the daemon from starting at boot when it should. I remember that the fix was a one-line change to a script somewhere, but I don't remember the details. I got all this info from threads in these forums though.
well, it works just like it should on all my machines. So if there is such bug then it's only affecting some users :)

---

### Post by rich.bradshaw on 2006-12-15
Yeah, the GUI is only to change/view things. I thinkg Firestarter does change iptables, the daemon monitors traffic.

I think. lol.

It works though, if you want to test, trying sshing into your box with/without it open, then let yourself in and repeat, if you see what I mean. I doesn't have to be 'open' to work.

Rich

---

### Post by John E on 2006-12-15
> **steve.horsley said:**
> I also read that there is a bug that prevents the daemon from starting at boot when it should. I remember that the fix was a one-line change to a script somewhere, but I don't remember the details. I got all this info from threads in these forums though.

Steve - it would be really helpful if you could remember where you found that info. I also installed FireStarter (a week ago) but I still can't get it to run.... :(

---

### Post by mcduck on 2006-12-15
> **John E said:**
> Steve - it would be really helpful if you could remember where you found that info. I also installed FireStarter (a week ago) but I still can't get it to run.... :(

Are you sure that it's not running? What does 'ps aux | grep firestarter' return?

edit: sorry, that would only tell you if you have the Firestarter GUI open..

The correct way to check the firewall status is 'sudo /etc/firestarter/firestarter.sh status'

After some searching I found out that Firestarter doesn't play very well together with Network Manager, so if you are using NM to manage your connections that could be a problem. I wasn't able to find any other problems with running the actual firewall, only people struggling to get the GUI running automatically when logged in. (must be some bad habit resulted from years of using Windows ;))

---

### Post by John E on 2006-12-15
I'll have to try that later as I can no longer boot into Ubuntu.... :( 

But if I remember correctly, there's a menu option somewhere to run the Firestarter config. Once it's been configured, it gives you the option to run Firestarter - but at that stage it said it wasn't able to run for some reason which I can't remember.

---

### Post by mcduck on 2006-12-15
I suppose you are talking about Firewall/Run Wizard in the Firestarter GUI? You need to have configured some network interface to get through that (it's not possible to run a firewall without a working network interface).

---

### Post by John E on 2006-12-15
Thanks - you've just reminded me what the problem was.... FireStarter can't seem to see my ADSL modem (a USB device). It could see my network connection but not my broadband modem.

---

### Post by ityro on 2006-12-15
THANKS TO ALL. I admit I am a typical Windows firewall addict. I would not think of starting Windows without a firewall running. I keep a copy of Zone Alarm Suite on my removable HDD just in case.

Even the Boot Update Manager was no help. Under the "Running" column is a "?" at all times, and if BUM didn't know I didn't know.

However, the suggested status query did the trick. I ran it with the icon on the panel, after exiting from the icon, and immediately after restart. All 3 times a status of "Running" was returned. I am now convinced. As Chief Joseph might say: "From this day forward, I shall question Firestarter again no more".

Did anyone else notice that no one mentioned the Easy Firewall Generator? 

Thanks again to all for your input. My concerns have been laid to rest.

---

### Post by ityro on 2006-12-16
> **mcduck said:**
> Are you sure that it's not running? What does 'ps aux | grep firestarter' return?

edit: sorry, that would only tell you if you have the Firestarter GUI open..

The correct way to check the firewall status is 'sudo /etc/firestarter/firestarter.sh status'

After some searching I found out that Firestarter doesn't play very well together with Network Manager, so if you are using NM to manage your connections that could be a problem. I wasn't able to find any other problems with running the actual firewall, only people struggling to get the GUI running automatically when logged in. (must be some bad habit resulted from years of using Windows ;))

THANKS TO ALL. I admit I am a typical Windows firewall addict. I would not think of starting Windows without a firewall running. I keep a copy of Zone Alarm Suite on my removable HDD just in case.

Even the Boot Update Manager was no help. Under the "Running" column is a "?" at all times, and if BUM didn't know I didn't know.

However, the suggested status query did the trick. I ran it with the icon on the panel, after exiting from the icon, and immediately after restart. All 3 times a status of "Running" was returned. I am now convinced. As Chief Joseph might say: "From this day forward, I shall question Firestarter again no more".

Did anyone else notice that no one mentioned the Easy Firewall Generator? 

Thanks again to all for your input. My concerns have been laid to rest.

---

