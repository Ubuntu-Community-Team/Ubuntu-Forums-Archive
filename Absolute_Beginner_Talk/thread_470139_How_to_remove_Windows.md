---
title: "How to remove Windows?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-06-10
Okay, now I'm ready to remove my Windows installation, and marry myself to Ubuntu :p
Today I am dual-booting Ubuntu and Vista. I consider installing VirtualBox or VMWare, and I have one question regarding this.
How do I uninstall Vista properly, without destroying my Linux installation? I also need to be able to install Vista on the virtual machine, and I wonder whether unproper uninstallation will obstruct the new installation (on the virtual machine... Product validation, unlock or something microsoft-alike. :p)
Can anyone give me some hints?

Thanks!
Joakim

---

### Post by LollYouSuckZor on 2007-06-10
I wouldn't suggest that.  Try not to spell micro$oft with the 's'..

---

### Post by ajeffreys on 2007-06-10
all i did was accidently format my windows partition and then I was just left with ubuntu, which was what i intended but oh well it is probably a good thing :)

---

### Post by christhemonkey on 2007-06-10
Try installing a virtualised Vista first maybe?
[http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/](http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/)

Then if it works go on to delete your old partitions  and expand your linux partitions with gparted.
And also, there is nothing wrong with writing Microsoft.

---

### Post by mortenkjeldgaard on 2007-06-10
Assuming you have Vista on a separate partition, you can use any program that allows you to edit the partition table (fdisk, cfdisk, parted) to wipe it and reformat it as ext3.

The only thing is, you probably can't edit the partition table on the disk you are booting from. So you probably need to boot from a livecd (Knoppix works well) and do it from there.

Good luck,
Morten

---

### Post by Joakim Stokland on 2007-06-11
Thanks for replies! :)

Okay, but will I be able to install it again on a virtual machine (as I was planning to) after wiping it like that? Microsoft only let you install Windows at one computer per licence, you know. So I figured maybe a virtual machine will be considered as a completely new computer by the server where you activate windows, subsequently obstructing the installation. Is there an activation feature in Vista like in XP anyway?

It won't be a huge loss if I can't install Vista, but if there is a way, it would be great! I need Windows for sonic stage, Sony's software, and thought a virtual machine would be a better alternative than dual booting.

I have the Ubuntu cd, so I can format from there :)

Thanks again!
Joakim

P.S. Please don't make this to a Linux versus Windows thread. :)

---

### Post by bodhi.zazen on 2007-06-11
> **Joakim Stokland said:**
> Thanks for replies! :)

Okay, but will I be able to install it again on a virtual machine (as I was planning to) after wiping it like that? Microsoft only let you install Windows at one computer per licence, you know. So I figured maybe a virtual machine will be considered as a completely new computer by the server where you activate windows, subsequently obstructing the installation. Is there an activation feature in Vista like in XP anyway?

As has been suggested, you should get vista up and running with either VMWare or VirtualBox first.

VMWare : [http://doc.gwos.org/index.php/VMWare_WindowsXP](http://doc.gwos.org/index.php/VMWare_WindowsXP)

VirtualBox : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

I like VirtualBox very much, but it is under heavy development and is not as "mature" as VMWare.  With VMWare you can convert your current vista install to a virtual machine

convert : [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

Here is a related product : [http://www.vmwarez.com/2006/02/livecd-player-virtual-machine.html](http://www.vmwarez.com/2006/02/livecd-player-virtual-machine.html)

===========

At any rate, yes if you install Vista into a virtual machine you will need to contact M$ . This is because M$ license allows you to run on 1 machine. If the machine changes, including hardware upgrades (like a new HD) you need a new validation #. MS$ is happy to spell out terms and conditions in the [M$ EULA](http://64.233.167.104/search?q=cache:Jd3loaT8YrUJ:download.microsoft.com/documents/useterms/Windows%2520Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf+vista+EULA&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a)

~ bodhi thinks if reading through the EULA does not make a convert of you, nothing will.

> It won't be a huge loss if I can't install Vista, but if there is a way, it would be great! I need Windows for sonic stage, Sony's software, and thought a virtual machine would be a better alternative than dual booting.

I have the Ubuntu cd, so I can format from there :)

Thanks again!
Joakim

P.S. Please don't make this to a Linux versus Windows thread. :)

Once vista is up and running, you can delete reformat the vista partition and use it as a data partition.

---

### Post by Joakim Stokland on 2007-06-12
Thanks! I'll check it out! :)
I'm also considering to install XP or some older version of windows instead of vista, as I have experienced that vista is REALLY unstable. I don't wanna make music transfer into a nightmare! :p

Are there any specific reasons why you like VirtualBox? I am not sure yet which application I'll go for, see...

Oh, and when you mention being converted.... Most companies offer free support for their customers. Microsoft's e-mail support service costs over 600 NOK here in Norway. That's approx 75 EUR!! (You've got two free support inquiries though..........)

Joakim

---

### Post by bodhi.zazen on 2007-06-12
VirtuaBox is easy to install, easy to use, and easy to configure. It is very fast, almost as fast as running native.

VMWare is more mature and more stable. For what you want, I advise VMWare server at the moment.

---

### Post by AndyCooll on 2007-06-12
Just a thought before you go rushing off installing Vista on VirtualBox or VMware. You should check your Vista licence. I'm sure I read somewhere that Microsoft have changed their licence agreements such that only the Vista Premium licence allows for it to be installed in virtual environment. 

Of course, I'm happy for someone to correct me if I'm wrong.

:cool:

---

### Post by bodhi.zazen on 2007-06-12
> **AndyCooll said:**
> Just a thought before you go rushing off installing Vista on VirtualBox or VMware. You should check your Vista licence. I'm sure I read somewhere that Microsoft have changed their licence agreements such that only the Vista Premium licence allows for it to be installed in virtual environment. 

Of course, I'm happy for someone to correct me if I'm wrong.

:cool:

LOL ~ I posted a link to the Microsoft EULA ^^

You do not expect me to actually *cough* *read* *cough* that thing do you ? You masochist :twisted:

I am sure it is a violation of previous EULA. I have no need for the current EULA.

I agree if you plan to install virtual you had better read the EULA.

+10 Linux/BSD

---

### Post by Joakim Stokland on 2007-06-13
Thanks guys :)
EULA says that only Vista Home Ultimate may be installed in a virtual hardware system. I've got Vista Home Premium, preinstalled, so I ain't allowed to. Well... :p

Anyway, thanks for all answers! Would you say it is _difficult_ to install, configure and use VMWare, or is VirtualBox just exceptionally easy to use?

Joakim

---

### Post by Joakim Stokland on 2007-06-17
Okay, so now I'm about to remove my Windows installation, but as I logged on to the live cd and started gparted,  I noticed that the Windows partition was flagged as boot. Will I destroy grub if I delete this?
How do I create a new boot loader?

Joakim

---

### Post by Joakim Stokland on 2007-06-24
I simply tried to remove the partition anyway, because I suddenly remembered that Grub lies within /boot!
So now I have deleted the entire Windows partition, and I have installed VirtualBox. It works great with Vista installed!
But the internet connection within the virtual Vista is dead slow! Why? How can I speed it up? It is very fast in Linux...

Thanks, Joakim :)

---

