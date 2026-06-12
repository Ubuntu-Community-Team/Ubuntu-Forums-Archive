---
title: "How do I install my printer?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by frayalejandro on 2007-07-26
Hi!
I am 2 days old in UBUNTU. I am trying to install my Epson 5900L printer. It is not a local but network printer, installed on Windows 2000 Server. 
Windows usually detects it automatically. Haow do I detect my printer now?

---

### Post by chamberlain2006 on 2007-07-26
Try going into System>Administration>Printing, Add Printer, and type in the information for it and see if it works.  I'm not sure if there is a Linux driver for it or not.

---

### Post by frayalejandro on 2007-07-26
I am absolutlly new to ubuntu. I need my computer to recognize my epson 5900L printer, wich is attached to a Windows server 2000 network.

Can smeone help me out?

---

### Post by Ek0nomik on 2007-07-26
I don't know much about printers, much less printers in Linux systems, but I found something that *might* help:

[http://ubuntuforums.org/showthread.php?t=288349](http://ubuntuforums.org/showthread.php?t=288349)

---

### Post by frayalejandro on 2007-07-26
Thanks.

I´ve been trying in system/adm/printer, but I am stiil having trouble. Ubuntu shows me the driver in the list... the thing is i dont even know how write the network address! 
I´ve been using DOS and Windows for almost 18 years...and ubuntu just for 2 days!!

---

### Post by bodhi.zazen on 2007-07-26
Welcome to Ubuntu we will try to help.

Please refrain from starting multiple threads on the same topic as it leads to duplication of effort and confusion.

---

### Post by frayalejandro on 2007-07-26
Thanks bodhi.zazen. I sent 2 threads on the same topic because i got lost on this forum page.

Look. I downloaded a driver for my epson 5900L. Now, how do I install thet driver?

---

### Post by frayalejandro on 2007-07-26
I allready installed the printer driver.

now, how do i connect it to the windows 2000 server?

---

### Post by bodhi.zazen on 2007-07-26
NP

What driver did you install ?

You need this one :

[http://downloads.sourceforge.net/epsonepl/epsoneplijs-0.4.0.tgz?modtime=1095379200&big_mirror=0](http://downloads.sourceforge.net/epsonepl/epsoneplijs-0.4.0.tgz?modtime=1095379200&big_mirror=0)

Then you need to install some stuff. Open a terminal and type :

```
sudo apt-get install build-essential checkinstall
```

Next extract that archive.

In a terminal cd into the archive and :

```
./configure --prefix=/usr
make
sudo checkinstall
```

This will (hopefully) make a .deb

Then :

```
sudo dpkg -i *.deb
```

See here for details on those commands: [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by bodhi.zazen on 2007-07-26
> **frayalejandro said:**
> I allready installed the printer driver.

now, how do i connect it to the windows 2000 server?

?? windows 2000 server

I guess I have no idea what you are doing with that or how that has to do with Ubuntu.

---

### Post by frayalejandro on 2007-07-27
Thanks for the details. But, just at the begining, terminal gave me this message:
Couldn't find package checkinstall

Well, Windows 2000 Advanced Server is installed as domain. The printer is connected to the server.

---

### Post by frayalejandro on 2007-07-27
My printer is connected to a Windows 2000 Advanced Server box. That´s why i´m trying to print from my Ubunto 6.06 box through the local network. 

I dont´ know why  System.Adiministration.Printing.Global Settings doesn´t detect it automaticaly. 

I allready installed the driver. Everything is  fine in the files and internet sharing area, but I can not make my printer work.

---

### Post by bodhi.zazen on 2007-07-27
OIC

I thought you were connecting the printer to Ubuntu, how silly of me :lolflag:

You share the windows printer via samba.

Here is a how-to : [http://doc.gwos.org/index.php/Print_Windows_XP_machine](http://doc.gwos.org/index.php/Print_Windows_XP_machine)

Yea, it is written for windows XP, but it should be similar with Server 2003 ...

I hope ...

---

### Post by frayalejandro on 2007-07-28
Thanks!

Your page is really helping me out. My connection with the windows server is OK. I can read and open my files. 

I just realized i was installing the wrong ppd (sorry!)

The thing is: NOW i downloaded the CORRECT driver (epsoneplijs 0.4.0), but when i look for the epson 5900l.ppd, it gives me this message:
[COLOR="Red"]Line longer than the maximum allowed (255 characters) at 206:'/home/alejandro/Desktop/epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l.ppd'[/COLOR]

I took a look to the README file... I´m confused :confused: 
I think i´m supposed to run Ghostscript, but i really dont know what to do.

I really appreciate your help. I´ve never recieved this kind of help while in windows.

---

### Post by bodhi.zazen on 2007-07-28
Well, first I am not all that knowledgeable ...

First, I am not sure you need to install epsoneplijs-0.4.0 Did you try just connecting through ?

Second, that error message is indication the line in question is longer then 255 characters ...

You you *might* be able to shorten it.

You can list the line with :

```
grep -n 296 /home/alejandro/Desktop/epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l.ppd
```

grep is a filter, -n numbers the lines of a file, and your error message is with line 296, so I hope that will print the offending line ...

You can the edit the line (hopefully it is a comment, a line starting with a #. You can then break the line into 2 or 3 lines as needed. I hope ...

```
gedit /home/alejandro/Desktop/epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l.ppd
```

Like this :

# Long line of comments

# Long line
# of comments 

HTH

---

### Post by frayalejandro on 2007-07-28
Thanks for the information.

Unfourtunatley, Ill be back in my office till monday. See you then...

---

### Post by frayalejandro on 2007-07-31
Well, Im back.

I made the corrections to line 206 with the gedit command. It originally said:
[COLOR="Green"]*% COMDATA #  'cmd' => 'gs -q -dBATCH -dSAFER -dNOPAUSE -sProcessColorModel=DeviceGray -dBitsPerSample=1 -sDEVICE=ijs %A %Z -sIjsServer=ijs_server_epsonepl -dIjsUseOutputFD -sDeviceManufacturer=Epson -sDeviceModel=EPL5900L -sIjsParams="%B" -sOutputFile=- -',[/COLOR]

I re-wrote it this way:

[COLOR="Blue"]*% COMDATA #  'cmd' => 'gs -q -dBATCH -dSAFER -dNOPAUSE -sProcessColorModel=DeviceGray -dBitsPerSample=1 -sDEVICE=ijs %A %Z -sIjsServer=ijs_server_epsonepl -dIjsUseOutputFD -
*% COMDATA #  'sDeviceManufacturer=Epson -sDeviceModel=EPL5900L -sIjsParams="%B" -sOutputFile=- -',
[/COLOR]





I dont know if that&#347; ok, but anyway, the driver installation now went OK. Unfourtunately,  I am still not able to print. 

What could I do know?

---

### Post by frayalejandro on 2007-07-31
This is the last thing Ive done:

I Installed the printer in my Ubuntu box, just to find out if it was a printer or network problem.
Ubuntu automatically detected the epson 5900L, but it still gave me the "foomatic-rip failed" message,

---

### Post by bodhi.zazen on 2007-07-31
Sorry, but if you can not share the printer over samba I am not sure how to fix it.

What did you do through samba ?

---

### Post by frayalejandro on 2007-07-31
Hi, Bodhi.Zazen

Please dont forget I´m new with Ubuntu AND linux. 
I just went to System>Administration>Synaptic Package Manager and installed Samba, but i dint do anything with it, cause... I dont know what to do with it! #-o

But I dont think its a net problem, but something with Ubuntu trying to recognize the printer.  I installed the printer directly to my Ubuntu desktop, and it automatically detected the printer. But it still continued to give me the same message. And I was not connected to the local network.

Its the same message:.../foomatic-rip failed... printer stopped.
I´ve benn chekcing out other threads tryingo to find out how other people solved their problem.

---

### Post by bodhi.zazen on 2007-08-01
I do not think you need to install the printer drivers on Ubuntu  ....

Follow step 4 of this how to (assuming the first 3 steps are working):

[http://doc.gwos.org/index.php/Print_Windows_XP_machine](http://doc.gwos.org/index.php/Print_Windows_XP_machine)

---

### Post by frayalejandro on 2007-08-01
I´ve done that allready. I am just about to give up... until I learn how to use this system.
What url, site or book would you recommend me to start learning linux?

---

### Post by bodhi.zazen on 2007-08-02
Well, to be honest, the best way to learn is to use. There are many sites available via google.

You can start with the links in my sig ;)

If you would like a book, [http://www.apress.com/book/bookDisplay.html?bID=10259](http://www.apress.com/book/bookDisplay.html?bID=10259)

---

### Post by Frak on 2007-08-02
I don't mean to sound bad, but are you sure you went to System->Administration->Printers, add new printer, then browse your network for UPnP Printer Device?
Don't mean to sound technical either.

---

### Post by frayalejandro on 2007-08-02
> **Frak said:**
> I don't mean to sound bad, but are you sure you went to System->Administration->Printers, add new printer, then browse your network for UPnP Printer Device?
Don't mean to sound technical either.

Yes, I allready did that. When I write the IPP address, the system finds the printer by name, it gets installed.

---

### Post by frayalejandro on 2007-08-02
> **bodhi.zazen said:**
> Well, to be honest, the best way to learn is to use. There are many sites available via google.

You can start with the links in my sig ;)

If you would like a book, [http://www.apress.com/book/bookDisplay.html?bID=10259](http://www.apress.com/book/bookDisplay.html?bID=10259)

I´m sorry if I dont get it, :lolflag:but, what do you mean by "your links in my sig"? Do you have an address or something like that?

---

### Post by Frak on 2007-08-02
> **frayalejandro said:**
> I´m sorry if I dont get it, :lolflag:but, what do you mean by "your links in my sig"? Do you have an address or something like that?
A signature is what is at the bottom of our posts, like mine says.

> [center]*All my advise comes with the Texas Warranty: If it breaks you get to keep both pieces.*
REGISTERED LINUX USER: #432608|REGISTERED UBUNTU USER: #8604
[http://ubuntuforums.org/showthread.p...32#post3081432](http://ubuntuforums.org/showthread.p...32#post3081432)[/center]

---

### Post by frayalejandro on 2007-08-02
> **Frak said:**
> A signature is what is at the bottom of our posts, like mine says.

Thanks! (english is my second language).

---

