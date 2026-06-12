---
title: "Install OSX Tiger on VMware Player"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by gr8dane on 2008-02-22
Hello all!  I had a quick question, I am running Kubuntu Gusty on a Compaq Laptop with a Celeron 2.4Ghz cpu and 1GB of ram.  I currently have XP Pro up and running fine in  VMware Player, I am wondering if it is possible to add OS X Tiger to VM?  I have done many many searches on Google and Kubuntu forums and it was suggested that I check here.

Has anyone done it and if so how?  Thanks in advance.

---

### Post by stchman on 2008-02-22
> **gr8dane said:**
> Hello all!  I had a quick question, I am running Kubuntu Gusty on a Compaq Laptop with a Celeron 2.4Ghz cpu and 1GB of ram.  I currently have XP Pro up and running fine in  VMware Player, I am wondering if it is possible to add OS X Tiger to VM?  I have done many many searches on Google and Kubuntu forums and it was suggested that I check here.

Has anyone done it and if so how?  Thanks in advance.

From what I understand of OS X is that it can only be run on Apple hardware.  If you have an Apple laptop or desktop then it may work.

---

### Post by PeterJS on 2008-02-22
It's technical possible, but from what I hear pretty difficult to get Tiger to run on a VM, and to make matter worse, not legal by any stretch of the imagination.

---

### Post by gr8dane on 2008-02-22
Not legal as in pirated copy of OSX?  I am more that willing to purchase the OS at the apple store.  So I am not clear on the illegal part, could you explain?

---

### Post by LukeCarrier on 2008-02-22
As far as I know, it's illegal in the US to violate an EULA, and Apple's EULA on the Mac OS X operating system states that the software is only authorised to run on Apple hardware.

---

### Post by gr8dane on 2008-02-22
I just got off the phone with Apple and the question I asked them is it legal to purchase and install a OSX on a Windows or Linux based system.  He said yes if you purchase a legal copy of OSX, however, he did not believe it was possible because of the architecture of a Windows system vs and Mac system.

I am not sure that is at all entirely true.  From my understanding the system is recognized by the OS, Mac uses all the same components as Windows from the CPU to the ram to the PCI cards, etc.  What I am not sure about is the motherboard.  I am not familiar with a Mac enough to know what type of motherboard is used.  More research for me I guess.

Here is the part that has me really scratching my head, he said that it I could purchase a Mac, partition the drive and install Windows on it for a dual boot system.  I know he was thinking why on earth would someone do that but it can and has been done.  SO if the architecture is so different, why can mac do it but now Windows?  

So I am back to the start again, How do I do it?

---

### Post by jrharvey on 2008-02-22
I have OSX running on vmware player right now. Unfortunately it is still very slow. Even on an Intel core2 2.0Ghz 3G ram it is sstill useless for anything other than basic stuff. I use it to connect to my schools OSX file server. I still have not found a way to do this with ubuntu yet.

---

### Post by jrharvey on 2008-02-22
> **gr8dane said:**
> I just got off the phone with Apple and the question I asked them is it legal to purchase and install a OSX on a Windows or Linux based system.  He said yes if you purchase a legal copy of OSX, however, he did not believe it was possible because of the architecture of a Windows system vs and Mac system.

I am not sure that is at all entirely true.  From my understanding the system is recognized by the OS, Mac uses all the same components as Windows from the CPU to the ram to the PCI cards, etc.  What I am not sure about is the motherboard.  I am not familiar with a Mac enough to know what type of motherboard is used.  More research for me I guess.

Here is the part that has me really scratching my head, he said that it I could purchase a Mac, partition the drive and install Windows on it for a dual boot system.  I know he was thinking why on earth would someone do that but it can and has been done.  SO if the architecture is so different, why can mac do it but now Windows?  

So I am back to the start again, How do I do it?

Windows will run on most computers that are x86 based. Unfortunately OSX Restricts their hardware to a select few, therefore its easy to put windows on a mac but unlikely you can put OSX on a PC because of hardware matches. Even if you have the exact same hardware as in an iMac, there are still slight differences. Its werid to explain but it just doesnt work the other way around.

---

### Post by gr8dane on 2008-02-22
> **jrharvey said:**
> I have OSX running on vmware player right now.

> **jrharvey said:**
> Unfortunately OSX Restricts their hardware to a select few, therefore its easy to put windows on a mac but unlikely you can put OSX on a PC because of hardware matches. Even if you have the exact same hardware as in an iMac, there are still slight differences. Its werid to explain but it just doesnt work the other way around.

Wow do you have a career as a politician.  So are you running a Mac or Windows?  If it is a windows based system it is more than likely it can be done since your doing it.  Now if your running  a Mac with Windows on it I have to ask why?  Then how does your Linux fit in to that equation?  You have my interest peaked.

I am sold on Linux but my wife teaches on Macs at the University yet we don't own one.  Not in the budget yet so I was looking to do a short cut and add OSX on VMware Player.  If your running slow with all that then It will be a standstill for me on my laptop.    


Thanks for the info

---

### Post by jrharvey on 2008-02-22
My machine is a windows based machine. No, i am not a polititian. I am a 23 year old archtiecture student. I use all three OS's daily for all different reasons. Windows is great because it will run almost any application you can imagine. I use OSX "sometimes" because my school is apple based. The only thing i really use if for is connecting to a server. Most importantly I use Linux because it safe, secure, virus free, fully customizable (looks and programs), completely free and I loooove the way it feels. Also (unlike OSX) it will run on most any computer. To me, ubuntu/gnome is the most natural feeling OS there is right now. I would recomend running OSX in Virtualbox if you can. I havt tried it yet but it is WAAAAAAY faster than vmware player and there are alot more options. Virtualbox should be in the repository (add/remove programs).

---

### Post by jrharvey on 2008-02-22
THere are some people that claim to run OSX natively and perfectly but I havnt personally seen any good examples of this. Im not sure about the Legal issues of this project but you could take a look at the OSx86 project. You may be able to tripple boot OSX, Windows and linux although it may be less trouble to just buy a mac.

---

### Post by gr8dane on 2008-02-22
I would like to have a max and run Linux on it and totally cut out Windows all together but that is not a reality for me right now.  I haven't tried Virtual Box yet but I think I might, my windows xp pro is slow on VMware Player.  Now I am running this all on a Companq (ugh why did I buy it?) with a Celeron 2.4Ghz CPU with 1gb ram.  Linux has slowed a bit since installing VMware Player but overall I am happy with it.  I'll give Virtual Box a shot.

Can you give me a play by play of how you installed OSX on to your VMware Player?

---

### Post by jrharvey on 2008-02-22
Well i actually didnt install it. I got a virtual disk image (.VDI) from a buddy of mine. This is basically a file that holds the whole pre-installed OS, its what VMware uses to run your virtual machine. Now before everyone screams about how this is illegal, keep in mind I own a mac and 2 copies of OSX (10.3 and 10.5). I have not tried actually installing it yet. Check out the OSx86 forums and see what the install instructions are. I assume that it works with virtualbox the same as VMware.

---

### Post by maduranga on 2008-02-22
if you want to install apple os on the intell machine legally, get a apple mac and uninstall the os. or get a new licean. or become an apple developer :)

 i assume you are using it legally. the os x need to be patched to install on intel hardware. i tried it with virtual machines and didn't work. But a patched version of a Leopard works perfectly for me. yes it is possible. google will help you. search for uphuck tutorials. 

 I assume you are using the apple mac os installation legally.

---

### Post by gr8dane on 2008-02-22
Yes I totally intend on doing it legally but I am not going to spend the money if it not possible.  I would prefer to have a mac but spending 129.00 for Leopard is much less expensive than 1100 for a laptop.  Which runs OSX better Virtual Box or VMware Player?

---

### Post by jrharvey on 2008-02-22
Virtualbox runs windows better, just as fast as natively for me. Im not sure about OSX.

---

### Post by wirelessmonkey on 2008-02-22
> **gr8dane said:**
> I just got off the phone with Apple and the question I asked them is it legal to purchase and install a OSX on a Windows or Linux based system.  He said yes if you purchase a legal copy of OSX, however, he did not believe it was possible because of the architecture of a Windows system vs and Mac system.

I am not sure that is at all entirely true.  From my understanding the system is recognized by the OS, Mac uses all the same components as Windows from the CPU to the ram to the PCI cards, etc.  What I am not sure about is the motherboard.  I am not familiar with a Mac enough to know what type of motherboard is used.  More research for me I guess.

Here is the part that has me really scratching my head, he said that it I could purchase a Mac, partition the drive and install Windows on it for a dual boot system.  I know he was thinking why on earth would someone do that but it can and has been done.  SO if the architecture is so different, why can mac do it but now Windows?  

So I am back to the start again, How do I do it?


You can install OSX 10.4 SERVER in  a virtualized environment, no other legally.  If this Apple rep said otherwise, I have a bevy of OS X administrators who'd love to talk to them.

---

### Post by p_quarles on 2008-02-22
> **wirelessmonkey said:**
> You can install OSX 10.4 SERVER in  a virtualized environment, no other legally.  If this Apple rep said otherwise, I have a bevy of OS X administrators who'd love to talk to them.
Correct. It is a well-known fact that Apple's licensing terms do not allow virtualization. Thread closed.

---

