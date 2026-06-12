---
title: "Clarification on a Tablet PC"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by bddubai on 2006-11-09
[FONT="Tahoma"][FONT="Tahoma"][SIZE="2"]Thanks for taking the time to read this.

I have a Fujitsu-Siemens T4010 Tablet PC notebook computer. It's a great machine, and I use it for teaching quite a lot. Hence, I need to get it configured for class. I need to get the Wacom tablet capability to work. I have done a clean install of the latest Ubuntu Edgy from a DVD that I downloaded. It's configured and working well on my destop PC.

I have been doing some research in the forums and have found a useful URL: [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D?highlight=%28fujitsu%29](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D?highlight=%28fujitsu%29). It's perfect for my situation; however, as a newbie, I'm afraid I require some additional help.

I was able to follow the first required action to install the setserial – I think. I did that with the Terminal Editor. *Thanks to those who explained that in previous threads!* 
[B]
Here's my result:[/B]

david@david-laptop:~$ sudo apt-get install setserial
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package setserial

Does this mean the it installed correctly?!

Regarding how to enter the /dev/ttyS0 (COM0) settings in /etc/serial.conf. The page says that I'll need to add a file: /dev/ttyS0 port 0x220 irq 4 autoconfig. How do I do that exactly?! Think “new-guy!” Would I continue to use the Terminal Editor? I'm overwhelmed by this.

Pretty much everything else that follows on the page is, VROOOM!, straight over my head.

Any help is greatly appreciated – especially as I will be able to “snub” a few high-school students with my new Ubuntu!

Thanks again.

David.[/SIZE][/FONT][/FONT]

---

### Post by Ecthelion on 2006-11-09
> david@david-laptop:~$ sudo apt-get install setserial
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package setserial

Does this mean the it installed correctly?!

No this means nothing happened.

Maybe it's easier for you to use the synaptic package manager...
System > Administration > Synaptic Package Manager
Just use the search function to find 'setserial' and try installing it that way...


If you still don't find it you can download it [here]("http://packages.ubuntu.com/edgy/base/setserial") and doing
```
sudo dpkg-i <path to the deb file you downloaded
```
If this doesn't work either it probably means you lack a dependencie...
Which you will have to install the same way.

Conclusion: use Synaptic Package Manager

---

### Post by Ecthelion on 2006-11-09
> Regarding how to enter the /dev/ttyS0 (COM0) settings in /etc/serial.conf. The page says that I'll need to add a file: /dev/ttyS0 port 0x220 irq 4 autoconfig. How do I do that exactly?! Think &#8220;new-guy!&#8221; Would I continue to use the Terminal Editor? I'm overwhelmed by this.

First open the file in a texteditor with root rights:
```
sudo gedit /etc/serial.conf
```
then just copy paste the line
> /dev/ttyS0 port 0x220 irq 4 autoconfig
in the document...

In terminal indeed

---

### Post by Ecthelion on 2006-11-09
> Pretty much everything else that follows on the page is, VROOOM!, straight over my head.

Just do literally what they say:
```
sudo /etc/init.d/setserial reload
```

To be sure do:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```
to backup your xorg.conf file...
If you mess up you can always go back to the original by doing:
```
sudo cp /etc/X11/xorg.conf_back /ect/X11/xorg.conf
```


Then
```
sudo gedit /etc/X11/xorg.conf
```

And do as they say...

---

### Post by bddubai on 2006-11-10
Thanks so much for the reply. I have the weekend to set this up.

  There are many things I shall try to figure out (e.g. the fan, hybernation, flipping the screen to name a few!) More than likely, I will have many more questions.

  That said, I will endeavor to do this on my own. The support here is AMAZING.

  Thank you so much for your expertise.

  David

---

### Post by abies on 2006-12-27
David:  Did these instructions work for you?  I had great success with them under Breezy, but with Edgy, it does not work.

All:  Any suggestions?  When I add the following to my /etc/X11/xorg.conf, I cannot start X.
> 
Section "Module"
...
        Load    "wacom"                 # add this line
EndSection


I'm sure something has changed since Breezy, since I didn't have an /etc/serial.conf file until I created one.

(this is all in reference to the stuff from [here]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D?highlight=%28fujitsu%29"))

---

### Post by Ecthelion on 2006-12-27
Can you post how your xorg.conf looks after you add the lines like they say?

---

