---
title: "[SOLVED] rt2570"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Jay Crown on 2008-01-31
I completely new to linux altogether and I'm having an issue. Basically I have installed Ubuntu 6.10 and I am trying to get my USB wireless rt2570 to work. The only catch is my computer is not connected to the internet at all so I am trying to figure out what packages I need to install so that I can get this device working.

I have downloaded the ralink driver already. When I type "$make install" it comes back saying

'cannot create directory '/lib/modules/2.6.17-10-generic/extra': Permission denied'

And it doesn't work... I have tried installing a few other packages too like ndiswrapper and linux-source-2.6.17 but couldn't get anything to install. I'm not sure what I'm doing wrong but I could use some help please!!

-Jay

---

### Post by overdrank on 2008-01-31
> **Jay Crown said:**
> I completely new to linux altogether and I'm having an issue. Basically I have installed Ubuntu 6.10 and I am trying to get my USB wireless rt2570 to work. The only catch is my computer is not connected to the internet at all so I am trying to figure out what packages I need to install so that I can get this device working.

I have downloaded the ralink driver already. When I type "$make install" it comes back saying

'cannot create directory '/lib/modules/2.6.17-10-generic/extra': Permission denied'

And it doesn't work... I have tried installing a few other packages too like ndiswrapper and linux-source-2.6.17 but couldn't get anything to install. I'm not sure what I'm doing wrong but I could use some help please!!

-Jay

HI and welcome, I am no expert on wireless ( or compiling for that matter) But I believe you will need [http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)
Can you get hard wired to the internet?

---

### Post by jleaker01z on 2008-01-31
> **Jay Crown said:**
> I completely new to linux altogether and I'm having an issue. Basically I have installed Ubuntu 6.10 and I am trying to get my USB wireless rt2570 to work. The only catch is my computer is not connected to the internet at all so I am trying to figure out what packages I need to install so that I can get this device working.

I have downloaded the ralink driver already. When I type "$make install" it comes back saying

'cannot create directory '/lib/modules/2.6.17-10-generic/extra': Permission denied'

And it doesn't work... I have tried installing a few other packages too like ndiswrapper and linux-source-2.6.17 but couldn't get anything to install. I'm not sure what I'm doing wrong but I could use some help please!!

-Jay

You have to run installation as root.  Add 'sudo' before the command. (sudo make install)

The newest version of Ubuntu has better wireless support tho.  Have you considered downloading 7.10 and burning to a cd?

---

### Post by Jay Crown on 2008-02-01
I tried installing that package and it came back with an error. I tried downloading it again and reinstalling it but failed again. Is there some other place I can dowload the 'build-essentials'?

I also tried adding 'sudo' it seemed to work but when I went I followed the step '$modprobe rt2570' nothing happened and my device still isn't working... any other ideas?

---

### Post by iris-n on 2008-02-01
It's build-essential, without s, and you can find it [_here_]("http://packages.ubuntu.com/gutsy/devel/build-essential").

I have a similar adapter, and managed o install it using  [_this_]("http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73") guide.

---

### Post by Jay Crown on 2008-02-01
Ok I downloaded those but it won't run it says it needed dpkg-dev so I downloaded dpkg_1.13 which would not run saying 'error: C compiler cannot create executalbes'... so what do I do now?

---

### Post by Jay Crown on 2008-02-02
I thank you all for your patience with me so far. I'm still having problems. Every time I go to install one of the packages I get errors either telling me the compiler can't create an executable or that some other package is needed for the package I am trying to install. Also, the build-essential that I downloaded from this link had some error unzipping it too. Any advice and help would be appreciated!!

---

### Post by iris-n on 2008-02-02
Probably you haven't the necessary dependencies, if you post the exact error message you got i could be sure. In the page i gave you, the dependencies are listed, you could download and install them manually, but i think that's too much trouble.

The easiest way to do it is by enabling the cd and fetch the package from there.

Put your cd in the drive, and type ```
sudo apt-cdrom add

```

It's added. Now, install the package; ```
sudo apt-get install build-essential
```

It should work now. Post back any error messages you get.

Best of luck!

Edit: Sorry, i didn't see you use Edgy, that page has the packages for Gutsy. [This]("http://packages.ubuntu.com/edgy/devel/build-essential") is the right page for you.

---

### Post by Jay Crown on 2008-02-02
I knew I had Edgy so I downloaded build-essential from that page but there was some error with it. Mounting the cdrom worked fine! So did installing build-essential! And so did installing the driver!... Now I have no idea how to configure it to work but at least I've conquered step one. Thanks Iris-n

-Jay

---

