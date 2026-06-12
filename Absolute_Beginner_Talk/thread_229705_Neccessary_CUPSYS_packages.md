---
title: "Neccessary CUPSYS packages"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-04
IN SYNAPTIC packages

I type search = "cupsys"

and removed all except for open office org, Because I was going through synaptic to remove package not needed.

Now no internet can connect

WHat packages are needed in cupsys results in synaptic

are needed for internet connect:?:

---

### Post by cantormath on 2006-08-04
> **neewby said:**
> IN SYNAPTIC packages

I type search = "cupsys"

and removed all except for open office org, Because I was going through synaptic to remove package not needed.

Now no internet can connect

WHat packages are needed in cupsys results in synaptic

are needed for internet connect:?:

hahahahahahahahaha.......

That is the funny post I have read this week.
Im sorry for laughing but thats rad!
Why in Gods name did you want to uninstall cups?
If you want to go backwards, open synaptic, and look at the history.
click on the day were you did this uninstalling and post what you uninstalled.  If you want to try and reverse the process, reinstall what you took out and reboot.

---

### Post by neewby on 2006-08-04
WEll for security reasons they say to dont have thing u dont know 

I was fort it was like netbios inlinux or something

cos it had print sharing in description so i just removed it

But I did ask what were the only necessary packages needed to connect to internet and view documents 

What is cupsys?

---

### Post by bikeboy on 2006-08-04
CUPS stands for Common Unix Printing System, it's the main thing Linux uses for accessing, configuring and using printers. A lot of apps also need cups so that they can print.

On the security note, don't enable "Detect LAN Printers" unless you need to, and make sure you install any patches that come along. Doing this will ensure that cups doesn't listen for incoming connections from the internet and doesn't have any known vulnerabilities.

If your internet connection problems are as a result of removing cups, you might need to use the Ubuntu CD to install the original packages you removed, hopefully your internet will come back and you can get the updates that way.

---

### Post by cantormath on 2006-08-04
yeah, generally, if its something thats installed with ubuntu install its generally not a security risk.  Anything can be a security risk, if you dont  want to take any risks with "print sharing" just turn it off.  Let us know how it goes.

---

### Post by neewby on 2006-08-05
How do I REinstall synaptic packages from cd

since synaptic packages are downloaded 

are they available on the cd

---

### Post by bikeboy on 2006-08-05
Not 100% sure but I think this should do it.
In Synaptic go to Settings > Repositories and make sure the top entry "Ubuntu CD" is selected.

Then search for cupsys, select it and go to Package > Force version, select the oldest version as this should be what came on the cd originally. Make sure the cd is in the drive :)

That should allow the old version to be installed even w/o a net connection. Still not sure how cups is related to the internet though, maybe another problem has occurred. But try that anyway and if you're still out of luck we can look into the cause of the lost internet.

---

### Post by neewby on 2006-08-05
NONE worked

this might be a downside for ubuntu 

I think remember im a newb It can only have upadte package , There must be a dvd for this WEll will have to think of new way


So to speak

If I go into synaptic
type search cupsys
the only package installed is open office 

must find way to fix

---

### Post by bikeboy on 2006-08-05
There is a DVD version but since cupsys is part of the default install it's on the CD as well.

Two things to try:
1- Temporarily disable all the other repositories leaving only the CD ticked, then click "Reload" and look for cupsys.

2- Go to Edit > Add CD-ROM, with the Ubuntu CD in the drive. You should also reload after this.

---

### Post by neewby on 2006-08-05
Yeh thats sounds responsible way

---

### Post by neewby on 2006-08-05
Need to know default repositries?
So am able to successfully sypnatic properly to download packages from

Turns out I had proxy to switch in firefox

---

### Post by bikeboy on 2006-08-05
The default ones would be the binary and source versions of:
> dapper main restricted
dapper-updates main restricted
dapper-security main restricted
The "main restricted" bits appear as smaller text under the main line.

If you run into trouble have a look at this page which also gives the extra repositories:
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

