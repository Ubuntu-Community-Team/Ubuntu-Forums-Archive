---
title: "Bodhi Linux software problem"
date: 2012-04-18
forum: Any Other OS
---

### Post by tetri on 2012-04-18
Hello

 I have a little netbuuk processor 1600, 8 GB hard, 512mb memory.
 Here's the Internet - [http://technews.bg/product.php?pid=9194](http://technews.bg/product.php?pid=9194)
 Bodhi Linux loving, stable, with some software and went well.
 But now appear problema.Ne can not install any software on the software center if they put some protections.

 Pictures.
[http://prikachi.com/images/314/4662314n.png](http://prikachi.com/images/314/4662314n.png)

---

### Post by oldos2er on 2012-04-18
Moved to Other OS/Distro Talk.

---

### Post by kc1di on 2012-04-18
try running this command in a terminal one line at a time.

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

Also what were you trying to install?

If the above does not work try this command in a terminal

```
dpkg --configure -a
```

---

### Post by tetri on 2012-04-18
Well, I'll see what I can do in the system

---

### Post by raja.genupula on 2012-04-18
> **tetri said:**
> Hello

 I have a little netbuuk processor 1600, 8 GB hard, 512mb memory.
 Here's the Internet - [http://technews.bg/product.php?pid=9194](http://technews.bg/product.php?pid=9194)
 Bodhi Linux loving, stable, with some software and went well.
 But now appear problema.Ne can not install any software on the software center if they put some protections.

 Pictures.
[http://prikachi.com/images/314/4662314n.png](http://prikachi.com/images/314/4662314n.png)

why i have got forbidden error , its saying i dont have permissions to see the image

---

### Post by tetri on 2012-04-18
Friend, I think that you can not see the photo due to the fact that I had uploaded to our server Bulgarian
 Otherwise, here's the big online community - [http://imageshack.us/photo/my-images/51/prava.png/](http://imageshack.us/photo/my-images/51/prava.png/)
 [http://img51.imageshack.us/img51/8061/prava.png](http://img51.imageshack.us/img51/8061/prava.png)
 You should already see the picture.

 So, the commands nothing changed. I can not install software, almost always leads to 3% and gives a message that:mad:

---

### Post by QIII on 2012-04-18
Are you trying to install abiword?

If not, let me know what you are trying to install.  I'll try to remember to check it out when I get home to my Bodhi machine after work.  That will be no earlier than 6:30 pm my time, which is GMT - 7.

Depending on where you are in Bulgaria, I imagine you are maybe GMT + 3?

---

### Post by raja.genupula on 2012-04-18
> **tetri said:**
> Friend, I think that you can not see the photo due to the fact that I had uploaded to our server Bulgarian
 Otherwise, here's the big online community - [http://imageshack.us/photo/my-images/51/prava.png/](http://imageshack.us/photo/my-images/51/prava.png/)
 [http://img51.imageshack.us/img51/8061/prava.png](http://img51.imageshack.us/img51/8061/prava.png)
 You should already see the picture.

 So, the commands nothing changed. I can not install software, almost always leads to 3% and gives a message that:mad:

have you enabled canonical sources in the software sources of your software center . else enable them . 

you can try from terminal , then its gonna ask you as Yes or No . by giving as Yes you can install that application .

```
sudo apt-get install abiword
```

---

### Post by tetri on 2012-04-18
I tried to install but **AbiWord** and it gives me error

my bodhi linux - [http://imageshack.us/photo/my-images/685/bodhilinux3241421.jpg/](http://imageshack.us/photo/my-images/685/bodhilinux3241421.jpg/)

---

### Post by QIII on 2012-04-18
If you actually typed AbiWord with upper case letters, it will fail.

Is that what you mean?

---

### Post by raja.genupula on 2012-04-18
> **QIII said:**
> If you actually typed AbiWord with upper case letters, it will fail.

Is that what you mean?

No one of the image is saying untrusted pkg something .

@OP , have tried the code i have given in your terminal  ?

---

### Post by tetri on 2012-04-18
I managed to install AbiWord from the command line, but the software center can not install anything.

---

### Post by QIII on 2012-04-18
> **raja.genupula said:**
> No one of the image is saying untrusted pkg something .

@OP , have tried the code i have given in your terminal  ?

Understood.  I quite got that.

However, the OP typed "AbiWord" in his post.  If he tried to use that in the terminal, it would not work.  He needs to type it in all lower case -- i.e.:  abiword

---

### Post by kc1di on 2012-04-18
> **tetri said:**
> I managed to install AbiWord from the command line, but the software center can not install anything.

I would install synaptic if it's not already install. I like it better than software center for finding and installing packages.

```
sudo apt-get install synaptic
```

---

### Post by QIII on 2012-04-18
Synaptic is included by default in Bodhi.

---

### Post by raja.genupula on 2012-04-18
> **QIII said:**
> Understood.  I quite got that.

However, the OP typed "AbiWord" in his post.  If he tried to use that in the terminal, it would not work.  He needs to type it in all lower case -- i.e.:  abiword

Yeah QIII :) . 

@OP have you enabled all check boxes in the other software tab of software sources window .

---

### Post by tetri on 2012-04-18
It seems a lot of software in the Ubuntu Software center is inconsistent and therefore have problems with addictions. However, there is everything, really everything - [http://appcenter.bodhilinux.com/](http://appcenter.bodhilinux.com/)
 Here you will find** easy to install software** for any task on your Bodhi desktop! Note that Midori or Firefox are REQUIRED for the "Install Now" method. The "Download" method will work in any browser.:p


 People recommend from there to install the programs because they are compatible with Bodhi Linux.
 I think it is best.
 I'm just not looking where they are and so gave errors

---

### Post by QIII on 2012-04-18
Setting up the "install now" option is a little bit of work, but I like the idea.  I've thought about contacting Mark to see if they can make it a default process.

And the first thing I do is install FF.  Midori is a dog.

---

### Post by tetri on 2012-04-18
Setting up the "install now" option is a little bit of work, but I like the idea. I've thought about contacting Mark to see if they can make it a default process.

 I think in the top it has **everything**.I'm just not looking where you:confused:
 It has said in [http://appcenter.bodhilinux.com/software/softbundles/1](http://appcenter.bodhilinux.com/software/softbundles/1)

 [B]* Mirage - Image Viewer
 * Adobe Pdf Reader - PDF Reader
 * Cheese - Webcam
 * Firefox - Web Browser
 * GEdit - Text Editor
 * Handbrake - Ripping
 * LibreOffice - Office Suite
 * Openshot - Video Editor
 * Qalculate - Mathematics
 * Pidgin - IM - Communication
 * Printing - Printing and Scanning
 * Rhythmbox - Media Player
 * Shotwell - Photo Manager
 * Simple Scan - Printing and Scanning
 * Thunderbird - Email
 * Transmission - P2P And Torrent Clients
 * VLC - Media Player
 * XChat - IRC - Communication
 * Filelight - System Tools
 * Xfburn - Burning[/B]

---

### Post by QIII on 2012-04-18
What I am saying is that the one-click install method itself is not set up and you have to set it up.

---

### Post by tetri on 2012-04-18
> **qiii said:**
> what i am saying is that the one-click install method itself is not set up and you have to set it up.
ok

---

