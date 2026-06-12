---
title: "Progress and personal preferences!"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2008-03-17
Hello and Greetings from Sunny Hedon UK
I have successfully installed Ubuntu version 7.1
However as a relative newcomer I amm finding this version a little difficult to configure to my personal preferences.
I have a HP Deskjet 720C printer but the system doesnt appear to recognise it.
Al least it shows in the config setup but when I try a test page nothing happens?
I also have a USB scanner Mustek 1248UB but this isnt recognised either?
I have two screens here and would like to configure the Twin-View setup in order to use both screen
How do I do this  with the latest Nvidia drivers (where are they?)
Why cant I choose the browser and email client I prefer as well
Opera browser and Thunderbird Email client?????
I am enjoying learning all about Ubuntu linux but would like it to be able to do all the above things 
Any advice will be very much appreciated
Cheers and beers
Geoff 
[www.jeffinhedon.karoo.net](www.jeffinhedon.karoo.net)
:)

---

### Post by anathema415 on 2008-03-17
The only things I can help you with are Opera and Thunderbird. Both are available through either add/remove programs (Under the applications menu), Synaptic Package Manager (System>Administration>Synaptic Package Manager), or the command line 

> sudo apt-get <APPLICATIONS>

I'm sure others can help you with the rest.

Have fun!

---

### Post by Sef on 2008-03-17
1) First it is best to post one problem per thread.  Otherwise, one of your problems could get lost.

2) The current version is 7.10 because it was released in October 2007.

3) Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

4) Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

5) Install Opera and Thunderbird:  Applications > Add/Remove > Search Thunderbird > click on box > repeat process from search for Opera.  The current version of stable version of Opera does not work with flash.  If you need it, then download the beta version, 9.50 from the [Opera Web site]("http://opera.com").

6) There are NVidia restricted drivers available from the repositories: System > Administration > Restricted Drivers Management.

7) The [HP 720c]("http://hplip.sourceforge.net/supported_devices/unsupported.html") is unsupported by HPLIP.  However, [OpenPrinting]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_720C") has directions how to get it working.

8) If you have the 1248 CU, it can work.  Either see if someone has an idea of what to do or check out the [sane-project Mustek's page]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Mustek&model=&bus=any&v=&p=").

---

### Post by Sef on 2008-03-17
> sudo apt-get <APPLICATIONS>

If you use the terminal, you should do it this way to make sure your system is set for the latest repositories:

```
sudo apt-get update
```

```
sudo apt-get install application_name
```

---

### Post by ajgreeny on 2008-03-17
Sef's link above to Restricted formats mentions **medibuntu** and I suggest this should be one of the first things you enable by going to that linked page and following the instructions.  **Medibuntu** has many programs and utilities that I find invaluable for the smooth working of Ubuntu's multimedia.  They are not included by default because they are proprietary, but in the time I've been using ubuntu (3 years) there's never been a problem with any of the **medibuntu** packages.

---

### Post by jeffinhedon on 2008-03-20
Hello again
I have been working hard since my original note!!!!!
I now have as much software as I will ever need 
Ihave also configured Twin view as well
and I got most of the answers from this Forum
I am delighted with the results 
Who needs Windows XP !!!!!!:)

---

