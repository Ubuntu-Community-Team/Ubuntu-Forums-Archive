---
title: "ubuntu 7.04"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-12
hi,

I'm basically a newbie to ubuntu linux and I'm using ubuntu 7.04. I am not very satisfied by its performance though. Like beryl doesn't run well. I have difficulty downloading and running the downloaded software. And many softwares do not run well. So how can i get rid of this problem.
Will gusty have these problems too? Or is gusty going to be better?

Thnx

---

### Post by llamakc on 2007-10-12
You can learn to explain your problems better. Beryl (and Compiz-Fusion) performance depends on YOUR hardware. You mention issues with downloading and running downloaded software but don't provide any details. How can anybody help you without more information?

Gutsy won't read your mind. Please be specific with your issues so those forum members who are helping can do so.

---

### Post by limac on 2007-10-12
hi,

i mean like if I download a file and then try to run it, it either shows a message saying "character code can't be verified" or it just wouldn't respond to me when when I double click it. Like blender just doesn't start if I double-click it and wait. It just doesn't respond. 

my hardware config is :
1.5gb ram
58gb hd free 
1.6ghz celeron M
Intel Graphics Media Accelerator 950 224mb

for more info on config use this link:

[http://cgi.ebay.com/NEW-Toshiba-A135-S4656-Notebook-Laptop-15-4-DVRW-Vista_W0QQitemZ200159691254QQihZ010QQcategoryZ140085QQcmdZViewItem](http://cgi.ebay.com/NEW-Toshiba-A135-S4656-Notebook-Laptop-15-4-DVRW-Vista_W0QQitemZ200159691254QQihZ010QQcategoryZ140085QQcmdZViewItem)

is this good enough for beryl?

thnx

---

### Post by llamakc on 2007-10-12
I'd ask a Beryl hardware question over in the Desktop Effects forum. 

Once more, you didn't give an example of what piece of software you are trying to install & run. Until you're specific it is going to be difficult to help.

---

### Post by lH)4~mK0e on 2007-10-12
Beryl really needs a better video card than that.  Something in the ATI Radeon or Nvidia Geforce family.  Intel graphics adapters are not even T & L capable.  Since it's a laptop, you are kinda stuck Beryl-less.

---

### Post by steveneddy on 2007-10-12
First of all, you need to either run software from Synaptic Package Manager.

Go to System -->Administration -->Synaptic Package Manager

All the software you probably need is in there.

Look around on the forums and look for software that fits your needs.

All you have to do is click the package you want to install and go to the top and click "Apply"

You can install software through the terminal, also. 

You can get spftware that is ready to run on your system at [getdeb.net]("http://www.getdeb.net/")

but most of the stuff there is already in synaptic.

You can't run Windows software without specific alternate Linux software install, also (Wine)

So ask the forums, of just search the forums for an answer and you will find what you need.

Beryl and Compiz will only run on hardware that as good graphics cards.

nVidia or ATI cards need to be used here, preferable nVidia.

Questions? Ask on the forums so someone else can benefit from the answer, also.

Read the forums. They are invaluable to a new user.

Also look [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

Good luck.

:popcorn:

---

### Post by steveneddy on 2007-10-12
> **limac said:**
>  Like blender just doesn't start if I double-click it and wait. It just doesn't respond. 




```
sudo apt-get install blender
```

will install blender

copy and paste this in terminal

---

### Post by defrex on 2007-10-12
Actually, I'm pretty sure Compiz will run with that Intel graphics chip. It's a little buggy though, and thus disabled by default in gutsy. It's got video playback issues.

---

### Post by LowSky on 2007-10-13
I don't recommend running beryl or fusion on integrated graphics. It is not designed for it. Also a laptop doesn't have  the same mouse functionality as a desktop mouse. 
What you should also know is your graphics chip runs on your system's memory, stealing memory away from  the processor, which in turn slows down your computer more. So if you want it to run more smoothly I suggest more RAM.

---

### Post by limac on 2007-10-13
hi,

I downloaded nvidia from envy manually. And then it said to restart the computer and I did so. When it restarted it said don't boot the computer until X driver is set up correctly. Then it went into the command prompt, and  I didin't really know what command i should use to get out of it.
Many people tried to help me out with the command but couldn't really succeed. And then somehow using the live cd of 7.04 and ran Ubuntu thru it And thought of redownloading it but didn't. Then without any hope,I reopened the downloaded Ubuntu 7.04, and surprisingly it worked. Why is that? And now if I open the nvidia setting it says: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." So what should I do? And **_any_** download from the internet, I either don't know how to run, or I doesn't run. Anyways, I like to ask how the download things form the internet and run it? It could be anything. So therefore I don't know how to run NVIDIA on my lappy. 

And about Blender, it's saying that it's already installed. But I cant really run it now (I ran blender on this computer on this os before). So any suggestions on how that can be fixed?

thnx

---

### Post by Samhain13 on 2007-10-13
Your issue with Blender might have something to do with your graphics card, although I am not sure how exactly. But when I installed Blender in Edgy (where setting-up the Nvidia driver was a bit different) it didn't run until I was able to get the Nvidia drivers and edit my xorg.conf-- specifically, replace "nv" with "nvidia".

Again that was in Edgy. In Feisty, I just enable Restricted Drivers and that's about it, then Blender works fine.

I'm just wondering now why you installed Nvidia if your graphics card is different. Could this be causing you more trouble?

---

