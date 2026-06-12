---
title: "iMac 24@ - Do I need to install ATI Drivers?"
date: 2009-04-30
forum: Apple Hardware Users
---

### Post by tintin_uk on 2009-04-30
Hi, I'm a total noob using 9.04 on an iMac 24". When I went to terminal and typed: glxinfo |grep direct

I got the message: uknown chip id 0x9583, can't guess

Does that mean I have to install ATI drivers. I'm confused in the documentation on here as to whether support is out of the box or not.

Thanks for your help,

TT.

---

### Post by khelben1979 on 2009-04-30
Try this instead:
```
sudo lspci | grep VGA
```
it will give the output on what videocard/chip you have in it.

---

### Post by noice742 on 2009-05-02
I get this when i type that

> ellinor@iMac:~$ sudo lspci | grep VGA
[sudo] password for ellinor: 
02:00.0 VGA compatible controller: nVidia Corporation Device 062e (rev a1)
ellinor@iMac:~$ 


The problem is i dont know how to install it. :confused:
Can anyone be nice and help me?
Step by step :KS
Thanks

---

### Post by pastalavista on 2009-05-02
One way to install is with envy
```
sudo apt-get install envyng-core
```
and when it's installed
```
envyng -t
```
but don't install anything unless it is recommended for your specific card. Some open source drivers are being used but they aren't the best, I know, with my ATI drivers. I'm still waiting for a fix from Ubuntu.

---

### Post by noice742 on 2009-05-02
And what should i do that have nvidia? :confused:

---

### Post by pastalavista on 2009-05-02
> **noice742 said:**
> And what should i do that have nvidia? :confused:Evny installs ATI AND NVidia drivers

---

### Post by noice742 on 2009-05-02
> **pastalavista said:**
> Evny installs ATI AND NVidia drivers


Okay. Sorry I didnt know.

---

### Post by khelben1979 on 2009-05-02
Since it's now clear that you need drivers from nVidia in this case, go [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us") to fetch them.

Since we don't know what specific model you have, you can try the **option 2**. And if that fails, then we need to know more about your graphic chip in order to know exactly what driver you are going to download.

When you have downloaded the file, you do this (from a text console):
```
sudo sh [name of the downloaded file]
``` Use ```
ctrl + alt + f1
``` to get to the first one. Make sure that the x-server isn't running, so it needs to get killed first.

```
sudo top
```
and then look up the GDM process number from the list and then use ```
ctrl + c
``` to quit it.
```
sudo kill -9 [process number of the GDM process]
```
to kill off the GDM process so that the graphics server can't get in the way of you installing the nVidia graphics driver.

---

### Post by noice742 on 2009-05-02
It did the trick with what i first got help with.
I now have nvidia working here. With desktop effects. :D thanks!
Now if only i could get the iMac's sound to work I would have everything working on here.
Could someone be nice enough to help me? Thanks Elin

Oh, and btw. I have the newest "top of the line" iMac 24" alu, that you can buy on apple right now.

---

### Post by khelben1979 on 2009-05-02
> **pastalavista said:**
> One way to install is with envy
```
sudo apt-get install envyng-core
```
and when it's installed
```
envyng -t
```
but don't install anything unless it is recommended for your specific card. Some open source drivers are being used but they aren't the best, I know, with my ATI drivers. I'm still waiting for a fix from Ubuntu.

When it's done in this way, does it mean that he/she wíll get the accelerated native graphics drivers? (Since I know that nVidia provides open source drivers wíth 3D support)

---

### Post by noice742 on 2009-05-02
I dont know what ive done, as far as i know - nothing. it wont work anymore with desktop effects. :( any ideas?

it says that the driver is installed, and i can even see that it says "is in use" and there is a green dot there too. 
i am so confused. :(

---

