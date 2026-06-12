---
title: "Internet Connect"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by jjmu15 on 2007-04-21
Ok ill start off by explaining my situation...

I am a total noob to Ubuntu and linux in general, I have setup Ubuntu using a dual boot sytem but I cannot get my AOL connection working on Ubuntu. It is turning out to be a real pain because whenver I need the net I am having to reboot my pc in windows.

Can anyone help me please, I have been reading around and have found out 2 options of installing AOL on Ubuntu, one is pengAOL which I have found but have no idea how to get it on Ubuntu as I need to download it and i have no connection on Ubuntu. The second method is configuring the PPOE settings (or something like that) but I have no idea what they are or how I would go about doing it.

I also do not have an ethernet port on my modem is the BT Voyager 105 DSL USB connection.

Any and all help will be appreciated and thanks in advance :)

---

### Post by twisted_steel on 2007-04-21
Welcome to the forums!

There is a EciAdsl driver available for your modem.  [This page]("http://www.jarviser.co.uk/jarviser/linuxusb.html") discusses setting it up, and while it says that there isn't a package for Ubuntu, I imagine either the Debian Etch or Sid [packages]("http://eciadsl.flashtux.org/download.php?lang=en") would do the trick.  There is also a package [available]("http://packages.ubuntu.com/feisty/net/eciadsl") in the Ubuntu universe repository, but I'm not sure if it is the latest.

[This thread]("http://ubuntuforums.org/showthread.php?t=412174") discusses installing a package that fixes the driver to work with the latest kernel found in Fiesty (see the third post).

Hopefully someone who has done this before will be able to add to the discussion.

As to getting the packages without an internet connection, I'd save the links and download the packages at a friend's house, and then burn them to a CD.  Copy them onto your machine and you should be ready to install.

---

### Post by jjmu15 on 2007-04-21
Thanks, Ill just try these drivers now and give feeback, good or bad when im done.

Thanks again

---

### Post by SOULRiDER on 2007-04-21
to configure a PPPoE connection, open a console and type:

```
 sudo pppoeconf 
```

Good luck!

---

### Post by jjmu15 on 2007-04-21
Ok, unfortunatley I have had no luck at all.

I have downloaded all the links and tried to run them in Ubuntu using the terminal and have looked up numerous guides online but I keep getting error messages and never completing the installation of anything.

I then decided to try the PPPOE method but quickly realised this wouldn't work as my modem is USB and not Ethernet. I have also tried to install pengAOL but havn't gotten anywhere  So once again im stumped.

---

### Post by medad on 2007-04-21
I saw this link and wasn't sure if you had already been there.  That person seemed to have gotten theirs to work.  Good luck!!

[http://ubuntuforums.org/showthread.php?t=412174]("http://ubuntuforums.org/showthread.php?t=412174")

---

