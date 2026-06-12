---
title: "Create iso cd"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by UbuEmmen on 2008-01-10
Hi,

I want to explore the Ubuntu Live-CD. I  have downloaded it from the website but every time I burn it on a CD it does not start. I simply get a wizard. I use CDBurnerXP Pro3. Is this program not suitable? :confused:

I don't understand what I might be doing wrong. Can anyone help?

Thanks.

Ronald

---

### Post by Crumpets and Jam on 2008-01-10
> **UbuEmmen said:**
> Hi,

I want to explore the Ubuntu Live-CD. I  have downloaded it from the website but every time I burn it on a CD it does not start. I simply get a wizard. I use CDBurnerXP Pro3. Is this program not suitable? :confused:

I don't understand what I might be doing wrong. Can anyone help?

Thanks.

Ronald

It will work. Open CDBurnerXP and when the window pops up that says "Select new project" hit the "Create Data CD/DVD button.

[[IMG]http://img512.imageshack.us/img512/2289/52125976rk2.th.png[/IMG]](http://img512.imageshack.us/img512/2289/52125976rk2.png)

Make sure you have a blank CD in your disk drive and go to File --> Burn disk from ISO file.

[[IMG]http://img242.imageshack.us/img242/4586/47904804vq6.th.png[/IMG]](http://img242.imageshack.us/img242/4586/47904804vq6.png)

A smaller window will appear. Browse to the ISO file that you want to burn which in this case will be Ubuntu.

Underneath that will be a box labeled Burning Speed. SET THIS AS LOW AS POSSIBLE. It is very important that you set this to the lowest number that you can. It will ensure that you don't corrupt the file while burning it.

Under Burn Method select Disc at Once. This is very important too. This will close the disk and make it bookable and readable to all disk drives.

Leave the check boxes under Burn Options on their defaults.

[[IMG]http://img170.imageshack.us/img170/2111/20280500mx3.th.png[/IMG]](http://img170.imageshack.us/img170/2111/20280500mx3.png)

Hit Burn Disk. The process will take about 10 minutes. Try not to do any demanding tasks on your PC while the burning is taking place. This will ensure the best possible result.

---

### Post by arochester on 2008-01-10
Have a look at "Burning a Linux ISO image on CD" on [http://polishlinux.org/installation/burning-a-linux-iso-image-on-cd/](http://polishlinux.org/installation/burning-a-linux-iso-image-on-cd/). A common mistake among newcomers is to simply copy the iso to a CD. What they need to do is "burn an iso" which creates a special bootable disk.

What wizard do you get?

You also need to check that the bootup order is CD-Rom first.

---

### Post by Ex-windows on 2008-01-10
Hi,
 Did you burn as an iso?  Thats the first thing You also want to burn the cd at a Very low speed like 2x or 4x. Another biggy is the md5sum. It's a way of checking the cd after download to insure that it matches the actual contents from the download server.. As for the Burning program I used infra record which is a freebie but real nice software. Let me know if I can help further.
Good luck


WOW These post come in fast lol

---

### Post by wolfen69 on 2008-01-10
download K3b (from synaptic) it is very easy to use. when it starts, select "burn cd image", and navigate to where image is.

---

### Post by Crumpets and Jam on 2008-01-10
> **wolfen69 said:**
> download K3b (from synaptic) it is very easy to use. when it starts, select "burn cd image", and navigate to where image is.

He isn't on Linux yet. He is trying to burn from a Windows machine.

---

### Post by UbuEmmen on 2008-01-10
Thanks you all for your input.

I have burned the iso as described in the first reply. It works now.

I am near to switching to Linux.

Thanks again.

---

### Post by Crumpets and Jam on 2008-01-10
> **UbuEmmen said:**
> Thanks you all for your input.

I have burned the iso as described in the first reply. It works now.

I am near to switching to Linux.

Thanks again.

Glad you got it to work.

---

### Post by Ex-windows on 2008-01-10
Great to hear  u got it done. Once you get used to linux you're gonna love it..

---

