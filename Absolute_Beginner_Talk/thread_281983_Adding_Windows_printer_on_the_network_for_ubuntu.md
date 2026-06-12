---
title: "Adding Windows printer on the network for ubuntu?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2006-10-21
Someone help with adding a windows network printer? it's an Lexmark Optra E312L. Thanks for reading my question

---

### Post by jordanmthomas on 2006-10-21
Have you tried adding it through System --> Administration --> Printing ?

---

### Post by LookTJ on 2006-10-21
> **jordanmthomas said:**
> Have you tried adding it through System --> Administration --> Printing ?yes but E312L isn't listed.

---

### Post by jordanmthomas on 2006-10-21
Ah, I see.  You could maybe install the deb listed at this site:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:141:0:0&searchLang=en&os_group=Debian%20GNU&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:141:0:0&searchLang=en&os_group=Debian%20GNU&target=)

Download it to your Desktop
Then, open a terminal and
```
cd ~/Desktop
sudo dpkg -i print*.deb
```
It may / may not require a reboot
Then try again and see if it is listed.

---

### Post by LookTJ on 2006-10-21
I tried downloading but it shows werid text at the download now link :S

---

### Post by jordanmthomas on 2006-10-21
After clicking the first link, you should maybe right click on the link to the actual deb and click Save As

To save you time, here's the link you should right click:
[http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.deb](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.deb)

**BTW, that is a huge file!

---

### Post by LookTJ on 2006-10-22
still wasn't listed. :(

---

### Post by jordanmthomas on 2006-10-22
[COLOR="Gray"]If you have already rebooted, don't bother with this, but you may need to restart your printing services.

```
sudo /etc/init.d/cupsd force-reload
sudo /etc/init.d/cupsd restart
```[/COLOR]

nevermind, that obviously doesn't work

---

### Post by jordanmthomas on 2006-10-22
okay, I installed the package for myself and it suggested I run
/usr/local/lexmark/setup.lexprint

Did you do this?  It seemed like it was all I needed to do to get everything working:
```
sudo /usr/local/lexmark/setup.lexprint
```

---

### Post by LookTJ on 2006-10-22
> **jordanmthomas said:**
> okay, I installed the package for myself and it suggested I run
/usr/local/lexmark/setup.lexprint

Did you do this?  It seemed like it was all I needed to do to get everything working:
```
sudo /usr/local/lexmark/setup.lexprint
```
I did that. the printer is on a windows computer though, what i am trying to do is add that printer

---

### Post by dannyboy79 on 2006-10-22
i have a hp printer setup thru samba. this is what my url looks like, smb://192.168.0.4/HPOfficeJet (obviously you'll need to adapt your ip and your printer name to be what your's are). i also have the guest account enabled in winblows xp. and i added a windows component, i think it's something like linux printing or somthing or other. i added it thru the cups system. i use xubuntu so I didn't use the gnome-cups-manager, i just used cups default config. you have to enable cups administration abilities first and i forgot how to do this, you need to gogle, enable cups admin. then you'll do [http://localhost:631/printers](http://localhost:631/printers)   i seee you're saying that your printer isn't shown, have you tried selecting one that is CLOSE to yours? you have nothing ti lose, give it a shot. if all else fails, hook it up to your ubuntu machine first to see if you can get it work tht way, then when you know which model and driver to chose then do the smb way. good luck

---

### Post by louistan3 on 2006-10-22
well if the previous post works.. then dont mind this.. but i have an hp printer(may/may not be significant) and i just set a static ip on the windows box.. then i go to system > administration > printing > new printer.. then i just click network printer.. then i put the ip on the address bar.. then pick out my printer.. and thats it.. works straight away..  

hope this helps :D

---

### Post by dannyboy79 on 2006-10-22
> **louistan3 said:**
> well if the previous post works.. then dont mind this.. but i have an hp printer(may/may not be significant) and i just set a static ip on the windows box.. then i go to system > administration > printing > new printer.. then i just click network printer.. then i put the ip on the address bar.. then pick out my printer.. and thats it.. works straight away..  

hope this helps :D

you simply repeated exactly what I wrote right before you?

---

### Post by jordanmthomas on 2006-10-22
Taylor, here's the steps I am guessing you have followed.  If you haven't, please try them.

0)  Enabled file and print sharing in Windows
1)  downloaded and installed drivers
2)  Gone to System --> Administration --> Printing
3)  Gone to the add printer section
4)  Clicked Netwrok Printer under Printer Type
5)  Changed the type in the dropdown box to be Windows Printer
6)  Found your Windows machine in Hosts and then your Printer in Printer
7)  You can probably use guest for username and no password.
8)  Clicked next
9)  Chose Lexmark as manufacturer and E321 as the model
10) named it whatever you choose
11) click apply

This should be enough to get it working.

---

### Post by louistan3 on 2006-10-22
lol.. sorry dannyboy.. ddnt read it that well.. :P

---

