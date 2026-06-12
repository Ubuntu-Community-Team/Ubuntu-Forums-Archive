---
title: "Ndiswrapper problems..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by toast_recon on 2008-02-28
I have been fiddling with ndiswrapper for the past month, on and off (mostly off) and the install file has been less than helpful. Searching the internet I have found many things that the install file left out, which would not have been a problem had it been spelled out clearly. What if I had not had the internet, which this program is supposed to help me attain?
But I digress.
I have a dell truemobile 1300 card, and have slowly, but surely, been able to obtain the following message:
bcmwl6: driver installed
              device (413c:8102) present
I think you should know that out of frustration caused by my futile efforts with ndiswrapper -i, I used -a.
I have done next to nothing in the terminal outside ndiswrapper, so nothing in the system is far from the default.
I finally thought I had victory when I got this message, and typed in modprobe ndiswrapper.
Nothing.
No, really, ABSOLUTELY nothing. It just went to the next line and nothing changed. I did a little searching and tried modprobe -v ndiswrapper. Still nothing.
modprobe -m yields a vast amounts of what looks like the same thing, and some look like pci id's.

I realize this is probably not nearly enough information, so please tell me if more would help.

I am not familiar with linux commands, so could you please tell me exactly what to type in.

I think ubuntu will be easier to handle once I get internet on it, easier access to info and whatnot.
Awaiting the day when my internet finally works,
toast.

---

### Post by Crooksey on 2008-02-28
If it looks like this....

```

$ sudo modprobe ndiswrapper
$
```

Then it worked, however if it looked like...

```

$ sudo modprobe ndiswrapper
*FATAL module "ndiswapper" not found
$
```

Then you have an error, modprobe is not meant to return any information.

---

### Post by S15_88 on 2008-02-28
Hey there i had a huge struggle with ndiswrapper on my old laptop 'd be glad to give you a hand as i know how frustrating it can be!

you can check out the old [thread]("http://ubuntuforums.org/showthread.php?t=492399") for my wifi struggle 

what exactly is your issue with your card?

---

### Post by S15_88 on 2008-02-28
try sudo depmod -a then modprobe

---

### Post by toast_recon on 2008-02-28
Actually, my problem is I don't know what to do next.
I have it installed (hopefully correctly) now what?
My card is just sitting there...staring at me...

---

### Post by Crooksey on 2008-02-28
The module loaded fine, please dont dobule post, there is a perfectly good edit button for ammedning posts.

---

### Post by toast_recon on 2008-02-28
Ok, if the module loaded fine, what do I do to get my internet up and running?
The light on my adapter has not gone on yet.

---

### Post by Crooksey on 2008-02-28
Using ndiswrapper dosent always make the led work, after modprobing run...

```

$ iwconfig
```

And see if a wireless device is listed

---

### Post by toast_recon on 2008-02-28
lo            no wireless extensions
eth0       no wireless extensions

---

### Post by Crooksey on 2008-02-28
Its been years since i used Ndiswrapper, but isnt there a stage where you assign the driver to a hardware location..

```

$ ndiswrapper -d #cant remember what goes here
```

---

### Post by toast_recon on 2008-02-28
I don't believe -d is used, at least it doesn't come up when I type ndiswrapper.
do you mean ```
ndiswrapper -a [device id] [driver]
```?
I did that to get it installed...

---

### Post by Crooksey on 2008-02-28
yea, must have changed, said it was a while :P

If it says driver present and hardware present then a modrpobe should solve it, hmm try rebooting?

---

### Post by S15_88 on 2008-02-28
have you tried System>Administration>network    is there a wireless option for you?

can you post the output for: lspci    and   lshw -C network

Thanks, ALain

---

### Post by toast_recon on 2008-02-28
reboot.
No change.
EDIT: Clicked Windows wireless drivers (under administration): Failed to execute child process "su-to-root" (no such file or directory)
I got "invalid option" for both lspci and lshw -c network...

---

### Post by Crooksey on 2008-02-28
Is the power switch for the wifi card turned off or anything?

---

### Post by toast_recon on 2008-02-28
no power switch.

---

### Post by S15_88 on 2008-02-28
what driver are you using?

---

### Post by toast_recon on 2008-02-28
bcmwl6...
that is what it is listed as under ndiswrapper -l
the exe is called r164287.
EDIT: Er...I looked up r164287...
that is the dell true mobile 1430, not the 1300...
I can see now why the driver may not be working.
*blushes*
Frustrating that I spent 24 hours collectively on the wrong driver.

---

### Post by S15_88 on 2008-02-28
find the exact windoze xp driver for your card and install it, let me know how it goes.

Thanks, ALain

---

### Post by toast_recon on 2008-02-28
Normally I would fiddle for a while, but while you are here...
when I do ndiswrapper -i dellomci.inf
I am getting the message: could not open dellomci: no such file or directory at usr/sbin/ndiswrapper
any suggestions?

---

### Post by anewguy on 2008-02-28
When you find the correct Windows driver, copy the .sys and .inf files to your desktop, then do the following in a terminal window:

(assuming in these examples your driver is dddd.inf)

sudo ndiswrapper -l   (that's a lower case "L")

if anything is returned, it must be removed via:

sudo ndiswrapper -e  xxxxxxxx  (where xxxxxxxx is the name returned above)

repeat the above until nothing is returned from ndiswrapper.  This is important, as you must have a clean slate in ndiswrapper.

Now, if I remember correctly, the Dell 1300 is a Broadcom 43xx series card, so the first thing you will need to do is blacklist the existing dummy module as follows:

cd /etc/modprobe.d

sudo gedit blacklist

at the end of that file add the following line:

blacklist bcm43xx

then save the file and exit

Now to load your good driver:

cd ~/Desktop

sudo ndiswrapper -i dddd.inf (it may be something like bcmwl5a.inf)

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Then finally, to ensure ndiswrapper starts when you reboot:

cd /etc

sudo gedit modules

add the following line to the end of that file:

ndiswrapper

then save the file, exit, and REBOOT.

When your system comes back up, you should be able to click on the network icon on the bar and see wireless networks listed. 

Post back if you have any questions or problems!  :)

---

### Post by myddewji13 on 2008-02-28
try this... [http://ubuntuforums.org/showthread.php?t=709447](http://ubuntuforums.org/showthread.php?t=709447) 

also bcmwl6 is probably the vista driver...you need the bcmwl5 driver...

---

### Post by S15_88 on 2008-02-28
when you do ndiswrapper -i are you in the directory that the inf is in?

ex. if your inf is on the desktop then your directory should be desktop:

name@comp_name:~/**Desktop**$ ndiswrapper -i

also i remember i installed the .sys file too, you need that one aswell


Thanks, ALain

---

### Post by toast_recon on 2008-02-28
when I do ndiswrapper -i dellomci.inf
I am getting the message: could not open dellomci: no such file or directory at usr/sbin/ndiswrapper

yes I am in the same directory, so I don't know what could be wrong there. Thanks anewguy, I didn't know the preparatory steps.
I am still stuck on ndiswrapper -i, however.
EDIT: I have the .inf and two .sys all in the same directory.

---

### Post by S15_88 on 2008-02-28
my guess is that you did not install ndiswrapper correctly?  how did you do the install for ndiswrapper?

---

### Post by toast_recon on 2008-02-28
Gosh...It was so long ago...
I don't really remember. I remember struggling for a few days and then it worked...
Do you think it is really that I installed it wrong?

---

### Post by S15_88 on 2008-02-28
yes i believe it is as usr/sbin is a subdirectory of /usr, which is used to store many application programs.  in your case it can't find ndiswrapper executable.  try a fresh [install]("http://ndiswrapper.sourceforge.net/joomla/") of ndiswrapper use make, and make install

---

### Post by Papa-san on 2008-02-28
Out of curiosity, where did you get the name 'dellomci.inf' from?

It doesn't sound like a broadcom driver name...

And, to answer that question about the ndiswrapper install: Yes, it messes up VERY easily. To eliminate that variable, it is relatively easy to replace it... Just get your drivers on your desktop delete ndiswrapper and install it again. Then I suggest a program called "ndisgtk"

Open a terminal and type:```
 sudo aptitude install ndisgtk 
```

---

### Post by toast_recon on 2008-02-28
Tried make and make install. I got countless errors.
"Incorrect use of of function "printf" "
sounds like java; Why would it be confused?
EDIT:ndisgtk used.
It is the same thing, only gui, no?
found out I was in the wrong folder of the driver, there were two inf files in two separate directories.
Now it just says hardware not present. I'll fiddle some more.

---

### Post by S15_88 on 2008-02-28
printf is C, you should install build-essential:

sudo apt-get install build-essential

then try again

Thanks, ALain

---

### Post by Papa-san on 2008-02-28
yes, ndisgtk is pretty much a gui for installing the drivers...
 The ndiswrapper link in my signature line has a pretty good walkthrough... You'll need to look specifically for your version though.

---

### Post by toast_recon on 2008-02-28
got build essential.
Tried everything again.
Now I have the driver installed, but it says hardware not present.
EDIT: Why is it that I always get different drivers?
I searched the PCID on the ndiswrapper website, linked to a different driver... loading now.

---

### Post by Papa-san on 2008-02-28
> **toast_recon said:**
> when I do ndiswrapper -i dellomci.inf
I am getting the message: could not open dellomci: no such file or directory at usr/sbin/ndiswrapper

yes I am in the same directory, so I don't know what could be wrong there. Thanks anewguy, I didn't know the preparatory steps.
I am still stuck on ndiswrapper -i, however.
EDIT: I have the .inf and two .sys all in the same directory.

Did you correct this yet?
You only need one .sys file. The second one may be messing you up.
Also, could you actually post the results from your terminal for us please? just put a [*code] (Data) [/*code] Copy and paste from terminal. (You'll have to remove the '*'s to make it work...)I'd like to see what you get when you try 'iwconfig'

EDIT: There will only be one driver for your card, Getting it based on the pciid is the only sure way to know which one it is supposed to be. Plus, make sure that the names are identical except that one should be *****.sys and the other *****.inf.

I pulled my hair out for weeks once because I was using bcmwl5.sys and bcmwl5a.inf

If you get a '.exe' file, do you know how to extract it properly?

---

### Post by toast_recon on 2008-02-28
er...I just did extract here.
Sorry about not posting everything exactly; It is hard when you are working two separate computers.
I did find the inf and the sys that were identical, so I brought them to a separate directory.
at this point I try to install, and it is successful.
```
ndiswrapper -l
``` yields
```
bcmwl5: Driver installed
```
iwconfig yields```
lo        no wireless extensions
etha0     no wireless extensions
```

EDIT: Not that it was more successful than usual. Just no errors.

---

### Post by S15_88 on 2008-02-28
first do:
sudo depmod -a
sudo modprobe ndiswrapper

then change directories to /etc(cd /etc):
sudo gedit modules

add to the file:
ndiswrapper

 save and reboot

let us know what happens after that

---

### Post by toast_recon on 2008-02-28
I am not sure "what" you are exactly looking for.
ndiswrapper still yields the same...
as does iwconfig...

---

### Post by S15_88 on 2008-02-28
you have to add the word: ndiswrapper

to the modules file so when ubuntu boots up it knows to start ndiswraper

---

### Post by toast_recon on 2008-02-28
I did enter the word ndiswrapper.
How would I have known if it booted up, anyway?
Ndiswrapper isn't GUI, right?

---

### Post by Papa-san on 2008-02-28
No ndiswrapper is background.
OK.does 'ifconfig' now show your wireless card? It should give you something if the driver is installed properly through ndiswrapper. 

Also, if it does show, see if 'iwlist scan' gives you anything.
Working through two computers is tough. It's not practical to type everything in. 
Can you get a cat 5 wire to connect the laptop to your router? Then you can work through the ethernet connection instead of going from one system to the other.

If it loaded, you will see this result when you reboot and type 'ndiswrapper -l' (That's a lower case L)
```
john@john-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
john@john-laptop:~$
```

---

