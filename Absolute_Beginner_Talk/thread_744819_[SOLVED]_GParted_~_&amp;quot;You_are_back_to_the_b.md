---
title: "[SOLVED] GParted ~ &amp;quot;You are back to the bash!&amp;quot;"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-04-04
..."So please run Forcevideo script and you will be asked for video driver, and resolution.
VESA driver should always work, and 1024 X 768 resolution too"
This is the message I get when I boot into a freshly-burned GParted Live CD.
Distro is Gutsy 7.10.
Computer is Sony Vaio VGN S-3.

btw I got these messages when I selected first British English as default language (02) and also with the default US (just press enter).

Using the GParted GUI on the Ubuntu CD seems to work, but it tends to crash afterwards.

I am totally without a clue here.

Regards

John

---

### Post by Diabolis on 2008-04-04
Run gparted through a terminal and if you get a error that says "segmentation fault", then uninstall gparted and get a diferent version.[ I had a similar problem with gparted.]("http://ubuntuforums.org/showthread.php?t=727440")

---

### Post by Oldsoldier2003 on 2008-04-04
gparted live cd: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

gparted source: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)

---

### Post by Andavane on 2008-04-04
> **Diabolis said:**
> Run gparted through a terminal and if you get a error that says "segmentation fault", then uninstall gparted and get a diferent version.[ I had a similar problem with gparted.]("http://ubuntuforums.org/showthread.php?t=727440")
Thank you for this.
I have downloaded the iso for a later version.
Now I know how to uninstall it from the synaptic package manager.
Could you tell me how to install a later version than 0.3.3-2 into the synaptic package manager.
Or is it better to burn it onto a cd and boot from that again?

Regards, John

---

### Post by StRiFe10101 on 2008-04-04
Now, please be kinda all.  I'm a noob trying to help out, but please correct my post if I'm way off.  

I personally have used gparted by downloading the CD ISO and booting from it which works/worked great for me.   

As far as the question regarding the synaptic package manager, you need to update it or it's knowledge of what's in the repos it's aware of.  this is done by updating it through synaptic package manager or using the command line.

sudo apt-get install update
sudo apt-get install upgrade

I know that this updates your linux OS install but was also under the impression it updated your package manager's repos.

Again, I'm probably missing something there but it's a start.

---

### Post by bumanie on 2008-04-04
From my experience the one in gutsy's synaptic works fine. I don't think you need to update the version in synaptic. I also have a live cd. I can't see the harm in you having a live cd as well. It can be used on any computer (friends, family etc) if necessary. Sometimes a live cd comes in handy if you can't unmount a partition/drive that you need to use the synaptic version on.

---

### Post by Andavane on 2008-04-04
> **Diabolis said:**
> Run gparted through a terminal and if you get a error that says "segmentation fault", then uninstall gparted and get a diferent version.[ I had a similar problem with gparted.]("http://ubuntuforums.org/showthread.php?t=727440")
Thanks.
When I run through the terminal I get this message:
"Since GParted can be a weapon of mass destruction only root may run it. Root priveleges are required for GParted."
Yes I confess that, after more than a decade in Windows, I am still very green.
How do I do this i.e. log in as root?
The machine I am trying it on is a test machine which I will require later.
So there is no harm which will come.
I merely want to run it to see if I get the segmentation thread message.
Regards
John


.

---

### Post by Oldsoldier2003 on 2008-04-04
> **Andavane said:**
> Thanks.
When I run through the terminal I get this message:
"Since GParted can be a weapon of mass destruction only root may run it. Root priveleges are required for GParted."
Yes I confess that, after more than a decade in Windows, I am still very green.
How do I do this i.e. log in as root?
The machine I am trying it on is a test machine which I will require later.
So there is no harm which will come.
I merely want to run it to see if I get the segmentation thread message.
Regards
John


.

```
gksudo gparted
```

---

### Post by Oldsoldier2003 on 2008-04-04
> **bumanie said:**
> From my experience the one in gutsy's synaptic works fine. I don't think you need to update the version in synaptic. I also have a live cd. I can't see the harm in you having a live cd as well. It can be used on any computer (friends, family etc) if necessary. Sometimes a live cd comes in handy if you can't unmount a partition/drive that you need to use the synaptic version on.

+1 the livecd is an absolute must for any " survival kit"

---

### Post by StRiFe10101 on 2008-04-04
the "sudo" in front of all the commandline statement envoke root privilages....

have you setup ur root password/account?

i believe you type 

"sudo passwd root"

then add the password.

(sorry, i don't know how to make the fancy command box things everyone uses.)

---

### Post by Oldsoldier2003 on 2008-04-04
> **StRiFe10101 said:**
> the "sudo" in front of all the commandline statement envoke root privilages....

have you setup ur root password/account?

i believe you type 

"sudo passwd root"

then add the password.

(sorry, i don't know how to make the fancy command box things everyone uses.)

no need to set up root. in fact its against forum policy to give tutorials on enabling root logins:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
as for the code box you can use [noparse] ```
 foo 
``` [/noparse] or use the advanced editor , highlight the text you want in the code box and click the # symbol.

---

### Post by Andavane on 2008-04-11
> **Oldsoldier2003 said:**
> no need to set up root. in fact its against forum policy to give tutorials on enabling root logins:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
as for the code box you can use [noparse] ```
 foo 
``` [/noparse] or use the advanced editor , highlight the text you want in the code box and click the # symbol.

Understand fully, having read this link.

The gparted problem was sorted out by downing a more recent iso file and burning it

On booting I selected the "Force VESA driver" option and kept pressing enter, after which the visual menu displayed itself.

Regards

John

---

