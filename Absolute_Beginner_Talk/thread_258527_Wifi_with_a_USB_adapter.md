---
title: "Wifi with a USB adapter"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Marksman Ken on 2006-09-16
Before anyone tells me to search the forums because there are some existing topics, I have and I dont understand them one bit. 

One topic I did look at is this one:
[http://ubuntuforums.org/showthread.php?t=31926&highlight=howto+wifi+card](http://ubuntuforums.org/showthread.php?t=31926&highlight=howto+wifi+card)

I have downloaded the wrapper in windows, transfered it with my usb memory stick and then Im stuck. 

First he mentions linux headers - what are they??
Second he types a bunch of commands to install it, my question is how does it know where to find the files or am I suppose to put them in a certain place?

Plus where do I get drivers for my Belkins 54g USB adaptor, I read somewhere that you install the wrapper which allows you to run your original frivers like they where in windows, I've searched but this whole thing cnfuses me :(

Any help would be great,
Thanks

---

### Post by Marksman Ken on 2006-09-16
Another reason I cant figure this out is because I dont understand alot of linux file extensions so I dont kknow what there for.

I'm sure plenty of people havwe done this before.

---

### Post by haiku99 on 2006-09-16
there is a good howto on ndiswrapper that may help at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Marksman Ken on 2006-09-19
Thanks,
But this dosent really apply to my situation enough.

I did find however a HOWTO file on something similar that explains everything much clearer (even though not relative to what Im doing) I now understand what Im doing with the commands but for some reason Ubuntu will not recognise the 'make' or 'make install' command. Im currently in the Ndiswrapper directory but it dosent recognise either command, but I have managed to get the files into the correct place, unzipped (I think :D). Any ideas?

---

### Post by Marksman Ken on 2006-09-21
Just to make sure its clear what Im asking I am going to say the whole thing again more clearly:

I am try to install the ndiswrapper-1.23 so that I can install drivers for mty USB wifi adaptor.

I have found a HOWTO that covers what I need but when I come to installing the wrapper, as below:
Step 3: Install Ndiswrapper.
Code:
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

it dosent recognise the command make or make install, even with sudo in front of it. Can anyone explain the theory behind the command and why it might not possibly be working? All it says is that the command ncan not be found.

I have had Ubuntu for a week now and not been able to get the internet going so I've been unable to do much other than play the built in games :P
I'd love to get this going to try Ubuntu out.

Thnaks.

---

### Post by Marksman Ken on 2006-09-22
Seems like not alot of people know about this ndiswrapper, can I at least have some comments on it from people who are using it.

I truley am stuck in nuetral until someone can help me clear this problem up. Any comment s at all would be great.

---

### Post by jcrnan on 2006-09-22
I have had mostly the same problem that you have and luckily for you I kept some links in my bookmarks as I know that its a pain in the ***.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

follow those instructions. They were for the the least confusing and they actually worked. On the last stages you might just have to try and retry and reboot the pc now and then, etc. It seems to be a bit random, but when it works it actually works for good :p

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

here is a list over supported cards/adapters. It will in most cases give you the driver you need for your adapter. Sometimes you have to use a very spesific driver, or even an older driver or similar. It all says there tough.

Good luck :)

---

### Post by Marksman Ken on 2006-09-23
Thanks alot mate,
Ill try that.

:p :D :) :-P

---

### Post by Jose Catre-Vandis on 2006-09-23
To use ndiswrapper you need to install ndiswrapper-utils, wihc you will find in Synaptic (you may need to add more repositories?)

Then once installed (synaptic takes care of all the dependencies and make/instal etc), open up a terminal and insert your drivers cd/floppy.

cd to the drivers directory and then:
```
ndiswrapper -i "name of your driver.inf"
```
Check this worked, the following code should tell you the driver is installed
```
ndiswrapper -l
```
Next open up modules and add "ndiswrapper" to the end of the file
```
sudo gedit /etc/ modules
```
Then:
```
ndiswrapper -m
```
Then load the module:
```
sudo modprobe ndiswrapper
```
You now need to configure the module, something like this:
```
iwconfig wlan0 essid yourworkgroup mode managed
```
it gets more complicated if you have WEP or WPA, I just use MAC address controls on my router

---

### Post by jcrnan on 2006-09-23
Jose: Thats basicly whats in the guide I gave him :P and it also has a good wep/wpa guide that I managed to use sucsessfully ;)

---

### Post by Jose Catre-Vandis on 2006-09-24
> **jcrnan said:**
> Jose: Thats basicly whats in the guide I gave him :P and it also has a good wep/wpa guide that I managed to use sucsessfully ;)

Yep, but in response to the OP's suggestion that not many people know about ndiswrapper, perhaps this helps to show that there are at least two of us! :D

---

### Post by az on 2006-09-24
ndiswrapper-utils is on the install disk.  While at the Ubuntu desktop, pop in the cd and the package manager will start up.  Install ndiswrapper-utils.

There are very very few devices that require you compile the most recent version of ndiswrapper from source.

You will need the most recent version of the windows driver (the inf file).

---

### Post by jcrnan on 2006-09-24
azz: not true. Some cards require older drivers or drivers for other cards as the list I linked to shows. For example I set it up on my little sis's pc and  I had to use a driver for completely different card and from 2003 :p

---

