---
title: "Installation fails"
date: 2012-01-11
forum: Any Other OS
---

### Post by Lizzaran on 2012-01-11
Hey,

i got a new graphic card and tried to do a fresh install from Linux Mint (also tried with OpenSuse and Ubuntu).

This is what i tried:

New Card:
Insert Linux Mint CD
Boot it
Come to the instalation menu
Click Install
DOS Mode apears (the installation gets instalized?)
Error apears after few seconds until a hard reset:
udevd[137]: timeout: killing '/sbin/modprobe -bv pci:v000010DEd00001244sv00003842sd00001556bc03sc00i00


Old Card:
Same as above, only without error and works.

Old & New Card:
Install Linux successfully with the old card.
Switch graphic cards.
Linux wont start.

Any idea?

---

### Post by Perfect Storm on 2012-01-11
Moved to Other OS/Distro Talk.

---

### Post by Double.J on 2012-01-11
> **Lizzaran said:**
> Hey,

i got a new graphic card and tried to do a fresh install from Linux Mint (also tried with OpenSuse and Ubuntu).

This is what i tried:

New Card:
Insert Linux Mint CD
Boot it
Come to the instalation menu
Click Install
DOS Mode apears (the installation gets instalized?)
Error apears after few seconds until a hard reset:
udevd[137]: timeout: killing '/sbin/modprobe -bv pci:v000010DEd00001244sv00003842sd00001556bc03sc00i00


Old Card:
Same as above, only without error and works.

Old & New Card:
Install Linux successfully with the old card.
Switch graphic cards.
Linux wont start.

Any idea?

Hi there and welcome to the forums, Which graphics card is this? Also have you got another system such as windows that you can confirm that the card is working normally?
All the best!

Edit:
 
Does the graphics card require it's own power supply? if so is it properly connected?

Sorry if this sounds like I'm talking down - Idon't mean to!, but it's quite a common mistake when installing a graphics card that requires power, replacing a card that didn't to forget to connect it. Also have you checked that your PSU is powerful enough?

---

### Post by IWantFroyo on 2012-01-11
It doesn't seem to be an issue with compatibility, or at least it would have to be a very rare one. A search for that error message turns up nothing.

Try gnu/mirow's suggestion and do some research on the graphics card type. Make sure it's getting enough power.

---

### Post by Lizzaran on 2012-01-12
Hey, the new graphic card is called  [EVGA NVIDIA GeForce GTX550 TI]("http://www.amazon.de/EVGA-GeForce-Grafikkarte-Speicher-Mini-HDMI/dp/B004S5CCP4/ref=sr_1_15?ie=UTF8&qid=1326275433&sr=8-15").
And yes, it has it's own power supply, but it is properly connected.
This card worked also very fine on windows 7 without any problems.

I also did some research about the error and the graphic card, but didn't find something useful. :\

---

### Post by Double.J on 2012-01-12
> **Lizzaran said:**
> 
...This card worked also very fine on windows 7 without any problems...

Hi there, Gotta admit this has me a bit stumped; When you said you'd tried it with Ubuntu and OpenSUSE I thought it had to be hardware because they are very different distros (unlike mint and ubuntu). That said, you say Windows boots fine with it installed on the same machine, So hardware's pretty much out.

SUSE and Ubuntu are so different by default, that the only area of similarity I can see is that may be relevant is they both use the 3.1.x kernel. 

As you've already installed ubuntu on the machine, see if installing all the latest updates and relevant nvidia driver then adding the card.

You could also try using ubuntu 11.04 (mint 11) or the lts release 10.04 (mint 9). Attempting to use a 3.2 kernel may also help, but is obviously a more advanced route, and with 12.04 including the 3.2 patched version in around 3 months it's upto whether you'd wait or not, but that's all if it even is the problem!

If updates and driver don't do it, Burn a live version of the above distros and see if they'll boot - should answer the kernel debate, or at least narrow the field!

---

### Post by Lizzaran on 2012-01-12
Thank you for your answer.
I will try your suggestions.

How can i install the nvidia driver, because my old card is from ati?

I also will try it with a older version of ubuntu / mint.

---

### Post by Double.J on 2012-01-12
> **Lizzaran said:**
> Thank you for your answer.
I will try your suggestions.

Can you link me to a tutorial where is explained how to update the kernel?
And how can i install the nvidia driver, because my old card is from ati?

I also will try it with a older version of ubuntu / mint.

Hi there, To update + get a driver on the go try

```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidea-current

```

See if that helps the situation? Also check the other versions of ubuntu/mint as suggested if all this suggests it is  the kernel, the easiest way to do it, is over [here]("http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-1-rc2-oneiric-in-ubuntu-11-04-10-10-and-10-04/")

Note the comments at the bottom - as Manivannan says make sure any nvidea driver is disabled in additional drivers before starting, and as Ike comments the command could be shortened and simplified. If you followed his suggestion make sure the only files starting in "linx-" and ending in ".deb" in Downloads are the thee advised by the tutorial.

All the best!

---

### Post by Lizzaran on 2012-01-12
YOU ARE MY HERO!

Updated the kernel to 3.2, installed the nvida driver and it magicaly worked!

Thank you so much :)

---

### Post by Double.J on 2012-01-12
> **Lizzaran said:**
> YOU ARE MY HERO!

Updated the kernel to 3.2, installed the nvida driver and it magicaly worked!

Thank you so much :)

Glad to hear it's working :D enjoy Ubuntu!

---

### Post by Lizzaran on 2012-01-12
Hey,

after the updates FileZilla isn't working anymore.
Tried to reinstall it but that didn't fixed the problem.
A other ftp client worked, but that one is crap :\

---

### Post by Double.J on 2012-01-12
> **Lizzaran said:**
> Hey,

after the updates FileZilla isn't working anymore.
Tried to reinstall it but that didn't fixed the problem.
A other ftp client worked, but that one is crap :\

Hi there,

Have you tried full remove/re-install?

```
sudo apt-get purge filezilla && sudo apt-get install filezilla
```

you could also try purging and downloading the latest source from their site [filezilla-project]("http://filezilla-project.org/download.php?type=client")

---

