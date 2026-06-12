---
title: "Nested dependencies... how to get all needed files?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Charlie Wilkes on 2007-03-19
I am spending a few days in a situation where all I have is dialup access to the Internet, and I would like to install/configure a Ubuntu dialer.

I have used scanModem to identify my winmodem, and it seems to be a common one with a Linux driver available.  It seems the simplest way to go from here is wvdial.  I have installed software that allows Windows to read and write to my Linux partition, so I can dial up in Windows and download wvdial to a directory in my Ubuntu partition.  But wvdial is dependent on several libraries etc., and these in turn are dependent on others.  it's quite confusing.

I have two questions:

1.  Is there any source that provides a complete list of all the files needed for a given package, such as wvdial?

2.  Assuming I am successful in getting identifying and downloading all the necessary files, how then do I install them to make a functional package?

Of course it would be much simpler if I were online in Ubuntu and I could use Synaptic Package Mgr. to do all this.  But I'm not.

Any help/guidance will be much appreciated.

Charlie

---

### Post by aysiu on 2007-03-19
[http://packages.ubuntu.com](http://packages.ubuntu.com) will help you.

---

### Post by 23meg on 2007-03-19
You may also find APTonCD useful.

[http://aptoncd.sf.net](http://aptoncd.sf.net)

---

### Post by Charlie Wilkes on 2007-03-20
From Windows I downloaded wvdial and about 45 other packages that seem to be required in the hierarchy of file dependencies, and saved them in my tmp directory on my Ubuntu partition.  When I booted into Ubuntu, all of these files were gone without a trace.  I don't understand what happened, because I have successfully used this method to download other (non-program) files from Windows to save on my Ubuntu partition.

Can anyone clue me in on what might have happened here, and how I might successfully download/install a Linux dialer without being able to do it online from inside Ubuntu???

Thanks.

Charlie

---

### Post by Bachstelze on 2007-03-20
/tmp is cleared at every boot. Definitely not the right place to save files ;)

---

### Post by pistcivet on 2007-03-20
Wvdial was installed by default in Dapper.
Is this package no longer installed in Edgy/Feisty?

(Because if it isn't, this is another reason for me NOT to "upgrade")

---

### Post by 23meg on 2007-03-20
> **pistcivet said:**
> Wvdial was installed by default in Dapper.
Is this package no longer installed in Edgy/Feisty?

(Because if it isn't, this is another reason for me NOT to "upgrade")

I just checked, and it is. 

Charlie, you should be able to use wvdial straight away in Edgy; it seems to be installed by default.

---

### Post by Charlie Wilkes on 2007-03-20
> **23meg said:**
> I just checked, and it is. 

Charlie, you should be able to use wvdial straight away in Edgy; it seems to be installed by default.

Yes.  I feel like a dummy.  But I finally got the whole thing to work.  Mainly what I needed to do was install sl-modem-daemon, and then add some tweaks to my wvdial.conf file.

The whole experience took me back to the frustrating troubles I used to have with Trumpet Winsock in about 1994...

Charlie

---

