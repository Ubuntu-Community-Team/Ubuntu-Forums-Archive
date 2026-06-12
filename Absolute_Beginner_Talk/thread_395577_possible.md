---
title: "possible?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by aran384 on 2007-03-28
I was wondering whether it is possible to install ubuntu onto a 3rd partition of a drive and then access my windows partition and run it through VMWare?

If this is it would be great for me and would love anyone who can help me out :D

If there are any guides on doing this it would be a big help...

---

### Post by charles.g.moore on 2007-03-28
If you want to install ubuntu through VMWare you can.
Then all you have to do is set up samba in order to talk to each other.  You don't however need to install the third OS into a 3rd partition, vmware keeps the OS in a .vmx file

For instance in my machine I:

run dapper as my 'host' OS
vmware is installed into dapper
within vmware I have XP, and FC5
I can fire up XP within my Ubuntu and they can both talk, transfer files, etc...

---

### Post by aran384 on 2007-03-28
I meant that I have two partitions on my main hard drive... 

Which is a 250Gb and am going to make a 3rd which is going to be around 20gb and then am going to install Ubuntu onto it... 

Its just I was wondering if I can access the Windows install of the 1st partition...

---

### Post by tcrroadie on 2007-03-28
If you are talking about running your Windows installation that is currently installed on a hard disk partition in a Linux hosted virtual machine, I don't see how this is possible.  

You can however, install Ubuntu on an extra partition on your machine, install Vmplayer or Vmserver and install Windows in a virtual machine hosted on your Ubuntu system.  This effectively creates a Windows virtual machine that you can run on both a Linux host and Windows hosted virtual machine.  I have done this myself and it is very easy to do.  

If you install Vmplayer, you can visit [EasyVMX ]("http://www.easyvmx.com/") and use the Easyvmx tool to create a bare virtual machine for the installation of any pc operating system (Windows, Linux, BSD). 

Then you would start Vmplayer, open the .vmx file you created using EasyVMX, and begin installing Windows in a virtual machine using your Windows installation cd.  You can also configure EasyVMX to enable booting of .iso images, this will allow you to boot and install Linux cd images without the need to first burn the image to a cd.  

Hope this helps.  :)

---

### Post by tcrroadie on 2007-03-28
> **aran384 said:**
> I meant that I have two partitions on my main hard drive... 

Which is a 250Gb and am going to make a 3rd which is going to be around 20gb and then am going to install Ubuntu onto it... 

Its just I was wondering if I can access the Windows install of the 1st partition...

After installation of Ubuntu onto your pc, you will be able to accesss (view) your Windows partition with any filebrowser.

---

### Post by NikoC on 2007-03-28
> **aran384 said:**
> I meant that I have two partitions on my main hard drive... 

Which is a 250Gb and am going to make a 3rd which is going to be around 20gb and then am going to install Ubuntu onto it... 

Its just I was wondering if I can access the Windows install of the 1st partition...

I myself have 3 partitions:
- one with XP Pro (still need it for certain lab applications, as soon as I find acceptable solution it will be deleted though ;) )
- one with Ubuntu
- linux swap

From Ubuntu I can access the media that are on the XP Pro drive... all my documents, articles, etc. that I need for my work I copied to my ubuntu partition by accessing the XP Pro partition via Ubuntu, just drag and drop! Also at home I can access my shared folders on my desktop XP machine (mom likes XP :lolflag: ) from my ubuntu laptop over the wired or wireless network. To conclude reading and copying from an XP (ntfs) partition via Ubuntu works flawlessly, copying to an XP partition from Ubuntu needs extra software (still think it is beta, but you can always do a search on this forum).

Does this answer you question?

---

### Post by aran384 on 2007-03-28
ah OK :( I wanted to be able to leave it as it was on the hard drive... 

Maybe for my next install I will do that... but for now I guess it is just either going to be a dual boot or just Windows. 

Is it true that Windows runs faster under VMware? Some people have said it is a little faster

---

### Post by tcrroadie on 2007-03-28
> **aran384 said:**
> 
Is it true that Windows runs faster under VMware? Some people have said it is a little faster

In the short time that I played with Windows Xp running on a Linux hosted virtual machine, I did not notice any performace difference (faster or slower).  I do have 1.5 gb of ram though.  

Question for you.  What exactly are you looking to do with Ubuntu, in that you need access to your Windows partition?  Run Windows programs, just view files stored on your Windows partition?

---

### Post by lamalex on 2007-03-28
you could use VMware converter, it will wrap your entire winxp partition into a vmx file which you can then open in either vmware player or server. then you take take the partition off of your harddrive and give that space to ubuntu. as for running them both simultaneously off of different partitions, not possible. plus even if you could, your performance would be very low.

---

### Post by aran384 on 2007-03-28
> **Iamalex said:**
> you could use VMware converter, it will wrap your entire winxp partition into a vmx file which you can then open in either vmware player or server. then you take take the partition off of your harddrive and give that space to ubuntu. as for running them both simultaneously off of different partitions, not possible. plus even if you could, your performance would be very low.

I only needed it to be able to access Windows Applications that I may of needed also... to increase the amount of things I could do at once... With XP my performance is slowed due to lack of desktops and I hate XP desktop mods that increase the amount you have... Its just too crappy for me like that...

---

### Post by lamalex on 2007-03-28
then I would say use vmware converter and put your XP into a VM. no reason not to imo.

---

### Post by aran384 on 2007-03-28
Thing is my XP install it huge ... lol Its about 40 something gig...

---

