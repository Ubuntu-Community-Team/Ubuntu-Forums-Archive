---
title: "Installing Ubuntu on a Mac mini"
date: 2008-07-27
forum: Apple Hardware Users
---

### Post by microfox on 2008-07-27
Hi


Using a live CD, I have installed Ubuntu 8.04 on an empty partition of an external firewire Hard Drive, I was sort of hoping that when I went to "System preferences", I would see that partition in "Startup Disk", but no dice. 

I have tried pressing the "T" key at boot up but that does nothing. I suppose I will have to use Bootcamp but all the instructions I see everywhere, are for a Windows install. Can I create a 5Gb partition on my internal HD (without ruining my Leopard install) and somehow tell it to boot from my Ubuntu partiton on  my external HD ? If so, how ?

I have downloaded rEFit and burnt it on a CD but when I use it, it sees my Leopard internal HD install, both my Leopard back up partition and my Ubuntu partition on my external HD but when I select it, I end up with a "No bootable disk can be found" error message.

I really could use some help.

thanks

PS: Mac mini Intel Core2Duo with 2Gb of RAM.

---

### Post by mkvnmtr on 2008-07-27
The install disk can partition your main disk. I think I used Disk Genius the first time and then let the installer install in the largest space. If you only give it 5 Gb you will be sorry later. I gave mine about 16 Gbs but now I hardly use OXS so I wish it was the small one.

---

### Post by sg7791 on 2008-07-27
I would try holding the option key at startup. The T key boots into target mode, which basically turns your computer into an external volume for another computer connected at the firewire port.

---

### Post by microfox on 2008-07-27
> **sg7791 said:**
> I would try holding the option key at startup. The T key boots into target mode, which basically turns your computer into an external volume for another computer connected at the firewire port.

Thanks for your answer but it does not work. Holding the "T" key, I get to see my internal disk Leopard install and my external disk's Leopard Back Up partition. I don't see the Ubuntu partition that is on the same external disk.

---

### Post by cyberdork33 on 2008-07-27
> **microfox said:**
> Using a live CD, I have installed Ubuntu 8.04 on an empty partition of an external firewire Hard Drive, I was sort of hoping that when I went to "System preferences", I would see that partition in "Startup Disk", but no dice.

You will not see that partition in Startup Disk. Hold the Option key during bootup to see partitions that are bootable. You can also install rEFIt.

Second, you are going to have tons of problems trying to install to and boot from an external drive. Please see the FAQ. There is a lengthy thread about this.

> **microfox said:**
> I have downloaded rEFit and burnt it on a CD but when I use it, it sees my Leopard internal HD install, both my Leopard back up partition and my Ubuntu partition on my external HD but when I select it, I end up with a "No bootable disk can be found" error message. There is an install bug that causes this... Again see the FAQ. Even with the fix in that thread there is not guarantee that you will not get this message because you are attempting to boot from an external Hard Drive.


> **microfox said:**
> I have tried pressing the "T" key at boot up but that does nothing.

> **microfox said:**
> Thanks for your answer but it does not work. Holding the "T" key, I get to see my internal disk Leopard install and my external disk's Leopard Back Up partition. I don't see the Ubuntu partition that is on the same external disk.
I think you are misunderstanding. You should not be using the T key. That puts your mac into "target mode". This means that you Mac acts as an external hard drive for another computer to access via a firewire connection. This will not help you boot from any partition on the harddrive(s) you have connected.

---

