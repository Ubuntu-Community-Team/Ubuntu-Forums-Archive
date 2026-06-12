---
title: "Virtual Machine"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by oryxgazella on 2007-08-21
I am trying to create a Virtual Machine (VM) /WinXP Pro on Ubuntu) using VMware Player and VMX Builder. I followed the instructions at [http://www.linux.com/articles/58176](http://www.linux.com/articles/58176) , but no VM was created. Everything seemed OK til "Launch VMX Builder and press the Create New Virtual Machine button. Select the folder you've just created and give your virtual machine a name. VMX Builder then creates a new VM and opens it in the main window.". A new VM never opened. Instead there was an error message: Run-time error '429': ActiveX component can't create object.

Please help,

Oryxgazella

---

### Post by swoll1980 on 2007-08-21
I had problems with VirtualBox creating vm because I didn't have headers installed for the kernel. Could this be the problem?

---

### Post by oryxgazella on 2007-08-21
Thanx bloor75,

for a rapid response.

Hmm, as a true beginner and non-native in English I am not sure I get what you mean by: "I didn't have headers installed for the kernel. Could this be the problem?" . When I get the error message I can see VMX Builder actually starting to create a new VM in the background. It looks like a version of this pic ([http://www.linux.com/var/slashimages/81b86cdb63a97348cbe8e639c6956bb1.png](http://www.linux.com/var/slashimages/81b86cdb63a97348cbe8e639c6956bb1.png)), but is greyed out. As soon as I click OK on the error message, VMX Builder closes and I cannot proceed. Guess it&#347; something with the graphics causing the problem, but as I said, I am novice to these things. 

The reasons I choose the guidelines at [http://www.linux.com/articles/58176](http://www.linux.com/articles/58176) were that they seemed fairly updated and very user friendly. Furthermore, other forums seem to prefer the VM Player/VMX Builder solution to create a VM.

Please, I need step-by-step instructions to overcome these problems. 

/Oryxgazella

---

### Post by AndyCooll on 2007-08-21
Far easier way to build a vmx image (i.e. a VMware one) is to use VMware server. That's free to download and use too.

Do you have any specific purpose for the VM image, or is it purely to create an XP virtual environment?

:cool:

---

### Post by oryxgazella on 2007-08-21
Hi Andy,

the reason is I'm sick and tired of MS and I think the best way to learn Linux is to jump right at it while keeping a back door open with WinXP if I fail miserably. Furthermore, next week I'm starting a course and I found out we need to install a program that must be run on Windows.

Yeah, I saw the option of creating a VM through VMware Server, but then I went for the VMX Builder option since the guidelines stated: "You could use VMware's free VMware Server software, but it's overkill if you only need a quick-and-dirty way to build a VM. Instead, consider VMX Builder, an easy-to-use desktop tool for creating VMware virtual machines." .

I'll try to create a VM with VMware Server.

Thanks,

Oryxgazella

---

### Post by buzzmandt on 2007-08-21
you might try virtualbox, i think it's much easier to install and use (opinion of course)

have linux on my laptop, virtual box w/ winxp for MS streets and trips and it works flawlessly

---

### Post by dustrho on 2007-08-21
> **buzzmandt said:**
> you might try virtualbox, i think it's much easier to install and use (opinion of course)

have linux on my laptop, virtual box w/ winxp for MS streets and trips and it works flawlessly

How did you get VirtualBox to work? I have it installed on my laptop, created a WinXP machine inside of it, start it and I get the following error message:

*"FATAL: No bootable medium found! System halted."*

I'm not a virtual expert by any means, but what needs to be done to get this thing working? Do I have to have a full copy of Windows XP or something?

Thanks!

---

### Post by dustrho on 2007-08-26
Bump.

---

### Post by stimpack on 2007-08-26
You created a Hard Drive and installed Windows on to it?

VirtualBox is very simple to use, very nice application, I love the fact the Linux version has the same GUI as other platforms, really linux-friendly app.

---

### Post by stevebakerj on 2007-08-26
> **dustrho said:**
> How did you get VirtualBox to work? I have it installed on my laptop, created a WinXP machine inside of it, start it and I get the following error message:

*"FATAL: No bootable medium found! System halted."*

I'm not a virtual expert by any means, but what needs to be done to get this thing working? Do I have to have a full copy of Windows XP or something?

Thanks!
Hi Chris,

Looks like you have the boot order wrong in VirtualBox

Start VirtualBox
Highlight the your XP or whatever install
Click on 'Settings'
Click on the 'Advanced' Tab
Highlight 'Hard Disk'
and just to the right you will see to little blue arrows click on the ^ arrow until the 'Hard Disk' is at the top of the list.
Click OK
Click Start

---

### Post by stevebakerj on 2007-08-26
> **stimpack said:**
> You created a Hard Drive and installed Windows on to it?

VirtualBox is very simple to use, very nice application, I love the fact the Linux version has the same GUI as other platforms, really linux-friendly app.

I agree I've tried most VM Ware and I feel VirtualBox is the best to use especially now that the Win and Linux interface is almost identical

---

### Post by dustrho on 2007-08-26
Steve, I did just as you mentioned, and the hard disk is at the very top of the list. It's also the only one that has a check box in it in the boot order. 

As to the other question from stimpack, am I supposed to actually install Windows XP on my computer? I thought that wasn't necessary. I did dedicate over 5gb of space to create this virtual Windows XP. I must not be doing something right or I must have forgotten to do something.

---

### Post by stevebakerj on 2007-08-27
> **dustrho said:**
> Steve, I did just as you mentioned, and the hard disk is at the very top of the list. It's also the only one that has a check box in it in the boot order. 

As to the other question from stimpack, am I supposed to actually install Windows XP on my computer? I thought that wasn't necessary. I did dedicate over 5gb of space to create this virtual Windows XP. I must not be doing something right or I must have forgotten to do something.

Seems like there might be a misunderstanding here. 

So you have created a virtual disk "somename.vdi" but you haven't yet installed XP on it?

---

### Post by Beggar on 2007-09-11
Just solved this for myself, you need to go to the settings tab for your OS, choose CD/Rom and then click the checkbox to enable it. Then boot into virtualbox, and use F12 to boot from CD.

---

