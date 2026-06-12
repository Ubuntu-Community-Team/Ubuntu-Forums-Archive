---
title: "Problem with File Browser - Computer View"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by JoshA on 2007-07-26
Alright I am a new Ubuntu user who is trying to see if I can completely ditch Windows (well almost except for the occasional games).

Anyways I have run into a strange problem with the File Browser.  I don't really know how to describe it so I have attached a screen shot below that illustrates the problem.  Essentially when I try to access any of my drives from the File Browser I get those error messages (see picture below).  Also, it doesn't display any icons for them.  

I think this is purely a GUI issue since I can access the drives fine through other means and even in the file browser and from my desktop.  It is hardly a major issue but I find it to be a nuisance.  I am running Feisty 64.

[ATTACH]39113[/ATTACH]

**ISSUE RESOLVED SEE BELOW**

---

### Post by Rocket2DMn on 2007-07-26
See if reinstalling Nautilus (the file system browser) fixes the problem:
```
sudo apt-get --reinstall install nautilus
```

---

### Post by djchandler on 2007-07-26
> **JoshA said:**
> Alright I am a new Ubuntu user who is trying to see if I can completely ditch Windows (well almost except for the occasional games).

Anyways I have run into a strange problem with the File Browser.  I don't really know how to describe it so I have attached a screen shot below that illustrates the problem.  Essentially when I try to access any of my drives from the File Browser I get those error messages (see picture below).  Also, it doesn't display any icons for them.  

I think this is purely a GUI issue since I can access the drives fine through other means and even in the file browser and from my desktop.  It is hardly a major issue but I find it to be a nuisance.  I am running Feisty 64.

[ATTACH]39113[/ATTACH]

This could only be a problem with the 64-bit version. Cross posting is generally discouraged, but that forum may have a better answer for you. 

Were all of these resources present when you installed Feisty? The error messages are telling you the filesystem on the boot device does not have folders for the resource in each error dialog, which are necessary to mount them. What you are seeing should not occur. Looks like a bug to me unless for some reason there are two bootable filesystems visible to the kernel, which could cause a kernel panic, and stops booting.

Are you by chance running Linux through an emulator, but also have a bootable Linux partition or hard drive as well? One more question: Are you running 64-bit Windows?
:confused:
DJ

---

### Post by JoshA on 2007-07-26
> **Rocket2DMn said:**
> See if reinstalling Nautilus (the file system browser) fixes the problem:
```
sudo apt-get --reinstall install nautilus
```

Didn't fix the problem.


> **djchandler said:**
> Were all of these resources present when you installed Feisty? The error messages are telling you the filesystem on the boot device does not have folders for the resource in each error dialog, which are necessary to mount them. What you are seeing should not occur. Looks like a bug to me unless for some reason there are two bootable filesystems visible to the kernel, which could cause a kernel panic, and stops booting.

Are you by chance running Linux through an emulator, but also have a bootable Linux partition or hard drive as well? One more question: Are you running 64-bit Windows?
:confused:
DJ

I didn't have this problem after I installed Feisty.  I think I did something along the way to screw it up.  I am not running Linux through an emulator or running 64 bit Windows.  I am dual booting Windows XP Professional 32-bit and Fiesty 64.  I can access all of the drives just fine through the Places side bar on the left.

---

### Post by djchandler on 2007-07-26
What kind of a response do you get in the right pane when you click on "filesystem" in the left pane?

---

### Post by JoshA on 2007-07-26
> **djchandler said:**
> What kind of a response do you get in the right pane when you click on "filesystem" in the left pane?

It shows my filesystem in the window and everything works fine.  This is a strange bug.

---

### Post by djchandler on 2007-07-26
> **JoshA said:**
> It shows my filesystem in the window and everything works fine.  This is a strange bug.

So this only happens when you first open nautilus? What happens when you go up to "Places" on the top bar and scroll down to "Computer?"
DJ

---

### Post by JoshA on 2007-07-26
I fixed the issue.  I was actually getting a series of bugs besides teh one mentioned here.  I could not create launchers on my desktop by dragging icons there (they would just be config files) and I could not open up pdfs.  Well I reinstalled the shared-mime-info package and it corrected all three bugs for me (in fact I was only using this to fix the pdf issue but I guess they were all related).  :guitar:

---

### Post by Escipion on 2007-09-18
SOLVED... WORKED FOR ME TOO... can anyone tell me why did this happened?

thank you

---

