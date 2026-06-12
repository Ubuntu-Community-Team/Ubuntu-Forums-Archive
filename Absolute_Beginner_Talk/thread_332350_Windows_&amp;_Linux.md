---
title: "Windows &amp; Linux"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Fireware on 2007-01-05
How exactly do I install Ubuntu on my laptop, but keep Windows as my main OS? 

Will it slow down my computer a lot? Is there risks of losing my Windows, or corruting it and losing saved files, like songs and what not?

And if I don't like it can I remove Linux without having to re-install Windows and lose all my windows data and saved files, etc...

---

### Post by Bachstelze on 2007-01-05
Just resize the Windows partiton, install UBuntu in the freed space, voilà :)

The risks of losing data are small but not equal to zero so better save your files first. Also, doing a defrag of the partiton in Windows before will lower the risks to get problems during resizing.

---

### Post by ajmorris on 2007-01-05
when installing ubuntu, just assure you install it on different partition to you windows one. If you keep Windows as a primary partition and linux as a logical then windows is the default still. Your only dilema is that when you install linux you grub or lilo will write to the MBR meaning it won't boot into windows but will instead boot grub or lilo. So to boot into windows you will have to edit the grub and lilo config file to add windows to the list. (it's not very hard)

If u re-install windows after linux it will ovewrite the MBR and you will lose grub or lilo, so i suggest getting yourself a boot loader such as Acronis to avoid all the hassle.

---

### Post by Fireware on 2007-01-05
How do I partition ? 

What do I save my files to? A resotre point? CD? Jumpdrive?

---

### Post by aysiu on 2007-01-05
Here are a couple of dual boot guides with screenshots:
Desktop CD - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Alternate CD - [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

In answer to your questions, yes, you can keep Windows as your main OS. No, it won't slow down your computer at all--only one OS can run at a time. There is a risk of losing Windows if you don't know what you're doing. Ask a **lot** of questions and back up **everything**. You can remove Ubuntu without reinstalling Windows, but you might need a Windows CD in order to use the *fixmbr* function.

I would advise playing with the Desktop CD (it's a live CD that runs off the CD itself and your computer's RAM--it doesn't affect your hard drive unless you click the *Install* icon) for a week or two before installing anything on your hard drive.

---

### Post by ajmorris on 2007-01-05
To partition run the ubuntu installer and select advanced partition table. Resize your windows one and it will show "free space" (the amount after resize) click install and install it into the free space.

---

### Post by pissedoffdude on 2007-01-05
> **Fireware said:**
> How exactly do I install Ubuntu on my laptop, but keep Windows as my main OS? 

Will it slow down my computer a lot? Is there risks of losing my Windows, or corruting it and losing saved files, like songs and what not?

And if I don't like it can I remove Linux without having to re-install Windows and lose all my windows data and saved files, etc...

You will be able to dual boot as ubuntu will install the grub bootloader which lets you decide which operating system you want to use.  It will not slow down your computer but it will take up space.  If you decide to remove ubuntu, you can delete and reformat ur linux partitions and with your windows cd u can go into the recovery console and type "FIXMBR" to get rid of grub.  Make sure to defrag ur drive before installing ubuntu.

---

### Post by Fireware on 2007-01-05
How do I back everything up and save it to a jump drive, would that work? 

Also, can I get on the internet with the live CD?

---

### Post by aysiu on 2007-01-05
> **Fireware said:**
> How do I back everything up and save it to a jump drive, would that work? 

Also, can I get on the internet with the live CD?
How big is your jump drive?

And, yes, if you're not using wireless or dial-up, you'll probably be on the internet with the live CD automatically.

---

### Post by Fireware on 2007-01-05
I have wireless! :( 

I've tried installing Ubuntu on my desktop, but it always seemed to freeze on a brown screen or one of the menu bars would come up or one will only come up and it'd be white with nothing or sometimes it seems to freeze when it says Window Manger, and 2 other things in a little Ubuntu box or something.... should I just wait and see for a few hours? 

My computer has an AMB processor or something with only 128 MB of RAM.


Can I install Ubuntu on a jump drive and use that lol instead of installing it on my computer? I hope that isn't a stuipd question?

---

### Post by ajmorris on 2007-01-05
Ubuntu is too big for a jump drive. However there are linux versions for Flash disks such as "Damn Small Linux"

---

### Post by Fireware on 2007-01-05
And you could run Damn Small Linux on a jump drive like a normal computer?

---

### Post by ajmorris on 2007-01-05
I am not sure on the finer details but i assume it would require access to your computer as well. But don't take my word for it. it saves the most important information such as user accounts and boot information the flash disk. How big is your flash disk?

---

### Post by Fireware on 2007-01-05
Oh, I don't have one at the moment.

---

### Post by aysiu on 2007-01-05
128 MB of RAM is too little to run the live CD.

You would need to use the Alternate CD to install Ubuntu.

Wireless can work, depending on what kind of wireless card you have, but even if it works, you'll still have to do some configuring to get it working right.

---

### Post by Fireware on 2007-01-05
Can I get the Alternate CD shipped like the other one?

Could I install Kubuntu with the alternate CD like ubuntu instead...I don't know which to use.. :(

---

### Post by aysiu on 2007-01-05
> **Fireware said:**
> Can I get the Alternate CD shipped like the other one?

Could I install Kubuntu with the alternate CD like ubuntu instead...I don't know which to use.. :(
No.

You can, however, purchase a DVD from Amazon for US$10. There are also Ubuntu CDs available on eBay. If you ask nicely, other forum members are usually willing to mail you copies, too, if they live in your country.

Be sure to install Xubuntu, though. Ubuntu or Kubuntu won't run very well on 128 MB of RAM, even after installation.

---

### Post by Fireware on 2007-01-05
Can I burn the Xubuntu download (if I download it) with RealOne Player? If not, what program and I will download it and burn it myself.

---

### Post by ajmorris on 2007-01-06
If ur in windows just use nero. It is the easiest.

---

### Post by 23meg on 2007-01-06
> **Fireware said:**
> Can I burn the Xubuntu download (if I download it) with RealOne Player? If not, what program and I will download it and burn it myself.[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Fireware on 2007-01-06
Do I do those same steps with the Xubuntu alternate CD to download and burn it?

---

### Post by aysiu on 2007-01-06
> **Fireware said:**
> Do I do those same steps with the Xubuntu alternate CD to download and burn it?
Yes. Those instructions will work for *any* Linux ISO.

---

