---
title: "Annoyed with Ubuntu..."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by alstroph on 2008-02-08
I'd always heard that Linux was the dream operating system. I'd seen videos referencing times when windows crashed during a presentation by Bill Gates as to mock the instability of the Windows operating system compared to Linux.

I installed Ubuntu last night pretty later. About 10 minutes after I got it up and running the whole system froze. I rebooted thinking that it was  fluke. Today it's locked up twice for no apparent reason. The most recent time (5 minutes ago) is when I clicked Places>Home Folder. Complete lock down... no response from the keyboard or the mouse. When I rebooted I got some message about my computer running in low Graphics. I clicked configure and looked for my video card (which I know it had correct before). When I couldn't find it I just clicked okay. Now my resolution is 800x600 not stretched. What's going on? I have a Geforce Go 7400 series card and a wide screen monitor.

My computer is a Sony Vaio SZ330P. My Ubuntu build is 7.10.

Listen, I'm not bashing Ubuntu. So far I've had a good experience with it. It's very complex and I have a lot to learn... but why is it so unstable for me? Where is this dream OS?

---

### Post by taurus on 2008-02-08
Open a terminal and reconfigure your X server again.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X with <Ctrl><Alt>Backspace.

Now, go into System -> Administration -> Restricted Drivers Manager and install nvidia driver for your graphic card.

---

### Post by alstroph on 2008-02-08
Thanks. My graphics are working great now. I'm able to use Beryl now. It wasn't working before.

---

### Post by taurus on 2008-02-08
If you are running Gutsy, then compiz-fusion is already installed on your machine.  You just need to install a driver for your graphic card an enable it.

Look in system -> Administration -> Restricted Drivers Manager for a driver for your graphic card.

---

### Post by Nythain on 2008-02-08
lol... i wouldnt be surprised if like the graphics drivers dont fix a lot of your locking and freezing... its funny that way :)

---

### Post by alstroph on 2008-02-08
Yeah everything is running smoother now of course. Hopefully the system doesn't lock up any more. Can someone send me to a nice guide for the transition from Windows to Ubuntu?

---

### Post by jrusso2 on 2008-02-08
This is a good website for the new user.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by nynoah on 2008-02-08
just as a word.  Ubuntu is great.  But like everything in life, it is going to have its hicups.  Nothing is perfect.  I do have to say that Gutsy has been the best install of Ubuntu so far.  It is light years better to me than the previous ones.   One thing to remember with Ubuntu.  You may get some headaches.  But just remember that all the programs that you use on it are free.  To me that more than makes up for the small headaches that come around from time to time.   Once you get past the hurdle of the first install, it gets real easy and real stable.  My Ubuntu systems is FAR more stable than my windows one ever was.  It just has its own unique quirks too.

and psychocats is a GREAT site for both a newbie and expert alike.

---

### Post by alstroph on 2008-02-08
Thanks. I appreciate it.

---

### Post by Thirsteh on 2008-02-08
Hey Alstroph.

There is a known issue with the Nvidia drivers currently in the Ubuntu package repositories and the FX generation of cards. I had similar freezes (mostly while running compiz-fusion), where every input (even sysrq) was disabled but things kept running, the only remedy being holding down the power button to shut off the machine. Nvidia has acknowledged that there is a problem and released new beta drivers, however these are not yet in the Ubuntu repositories. Hence this isn't really Ubuntu's fault.

What I did:

Installed latest version of 'Envy New' from this page: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Applications->System Tools->Envy (or just 'envy' in a terminal)
Accept all dependency installation requests
'Install Nvidia drivers'

Envy manually downloads the newest drivers from Nvidia's website and builds them to match your kernel. This isn't the recommended method, but in a case like this it's just... well, necessary. As far as I can tell, Envy doesn't 'break' stuff, meaning, you can re-open it at any time, select "Uninstall Nvidia drivers" (or "sudo envy --uninstall-all") and go back to using the ones in the Ubuntu Restricted Drivers  (sudo apt-get install nvidia-glx-new) when they get fixed.

Hope you get it worked out, and don't let this little mishap spoil your experience!

---

### Post by alstroph on 2008-02-08
My touch pad is being very sensitive. While moving my finger around I often accidentally tap. This was not an issue before switching to Ubuntu so I know it's something to do with the settings. Is there a way to turn down the tap sensitivity?

@Thirsteh

Thanks a lot for the response. I might try that since my screen is still flickering every now and then.

---

### Post by sammydadams on 2008-02-09
i had this same issue 
go to menu>system>preferences>mouse and set the double click timeout, but this might not help if you are like me and tend to be typing and accidentally single-click somewhere and it randomly starts typing there...if using touchclick i set it to 200ms for a double-click, but mostly i just turn tap to click off under touchpad since i have a separate mouse as well...hope that helps

---

### Post by alstroph on 2008-02-09
Thanks. I'd turned off tap clicking since it was more annoying than helpful... but maybe this will help things out. :)

---

### Post by ugm6hr on 2008-02-09
This gives you all the info to fully configure your touchpad:
[http://ubuntuforums.org/showthread.php?p=3105368#post3105368](http://ubuntuforums.org/showthread.php?p=3105368#post3105368)

---

