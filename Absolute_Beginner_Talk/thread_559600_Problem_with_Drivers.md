---
title: "Problem with Drivers"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Robotchicken1886 on 2007-09-25
Hi,  so i recently installed ubuntu as my primary OS.  well its my only OS right now.   anyways so after the install my sound, wireless card, dvd/cdrw player will not work.   i know i need new drivers so my computer will recognize them.  but i have not been able to find them,  and all the ones i can find are for windows.    here are my specs
[URL="http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=All%20Operating%20Systems"]http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=All%20Operating%20Systems
[/URL]


Model: Gateway 7305GZ Notebook
Serial Number: N345451049732


so far i love ubuntu way more then windows and i would hate to have to switch back because of no sound/movies and wireless


oh PS my computer gets the internet if it is physically plugged into it,  if that helps

---

### Post by pay on 2007-09-25
To install the ati driver, follow this [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) guide (don't do the manual installation with 8.41.7, it's for r600 series only. For the wireless, you might need to use ndiswrapper to install windows drivers, but I've never done that before so I can't comment. I don't know about the sound though.

---

### Post by mysticmatrix on 2007-09-25
> **Robotchicken1886 said:**
> Hi,  so i recently installed ubuntu as my primary OS.  well its my only OS right now.   anyways so after the install my sound, wireless card, dvd/cdrw player will not work.   i know i need new drivers so my computer will recognize them.  but i have not been able to find them,  and all the ones i can find are for windows.    here are my specs
[URL="http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=All%20Operating%20Systems"]http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=All%20Operating%20Systems
[/URL]


Model: Gateway 7305GZ Notebook
Serial Number: N345451049732


so far i love ubuntu way more then windows and i would hate to have to switch back because of no sound/movies and wireless


oh PS my computer gets the internet if it is physically plugged into it,  if that helps

Ok lets move in steps

0) Tell us which version of ubuntu are you using.

1) Open Applications --> Accesseries --> Terminal and output command of```


lspci
```

2) If you cannot get DVD drive working, how did you install ubuntu?

3) It would be helpful if you can specify us your model of wireless card.(If you don't know, don't bother much. We'll try to figure out.

---

### Post by Robotchicken1886 on 2007-09-25
Ok so just by searching around the internet i have gotten the soundcard and wireless card to work.    the only thing i have left is to get the CD/DVD player working   i need the driver any ideas

---

### Post by ScoopJumps on 2007-09-26
> **Robotchicken1886 said:**
> Ok so just by searching around the internet i have gotten the soundcard and wireless card to work.    the only thing i have left is to get the CD/DVD player working   i need the driver any ideas

I am not sure if this will be much use to you but it resolved my problem. Ubuntu recognised my drive as a CD/DVD drive but was unable to access any information on a DVD be it a data disc or film. It however, worked fine as a normal CD drive, I did after all install Ubuntu from it. If this sounds like similar problem you are having try this.

Click **APPLICATIONS** and add/remove programs and tick all the boxes for commercial and unsupported applications. FInd a program called '**oKle**' and select that. I use this to view DVDs.

Next you need to get your drivers. Open terminal and use the following commands:

**sudo apt-get install libdvdread3**

Once that has done its thing enter this command to get the libdvdcss2 library:

**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**

.. and that should be it.

I hope this helps. I found I was subsequently able to play video DVDs and also read data DVDs after this install.

As you can tell by my lack of jargon and technospeak I'm not technically minded when it comes to software. I found this advice in another forum and am just spreading the word because it worked for me earlier today.

Good luck. I love Ubuntu now I have got everything working. Only thing is i'm waiting for a new wireless router, PCMCIA card etc... which i'm sure will be fun setting up when it arrives. NOT

:)

Sam

---

