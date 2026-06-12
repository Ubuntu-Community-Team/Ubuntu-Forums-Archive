---
title: "virtualbox"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-13
Hello forum people,

I have installed virtualbox on my new ubuntu here.

so the machine is fresh.

how can i copy my machine as it stands...into a new virtualbox?..an exact copy of it..... as it stands...

It is a fresh linux ubuntu machine...with just virtualbox installed...

i want to make copies of this machine..into new virtualbox's...

what is the command(s) to use?

thanks

Vince.

---

### Post by Tom--d on 2008-04-13
You need to install the OS in VirtualBox.

---

### Post by vinceUUUU on 2008-04-13
Hello

so VBox does not have a feature for quikly making clones of the system it is sitting on?

can it not load up....IMAGE files that are copies of my Linux partition maybe?

thanks

also..do you know of any tool that can do quik clones of an OS?....putting them in seperate new virtual machines?

i know hyperOS can do it in seconds.....up to 20 operating systems co-exist

thanks

Vince.

---

### Post by ryanhaigh on 2008-04-13
You could use one of the norton ghost alternative apps like ghost-for-linux to create an image of your current install which you could then 'restore' to your virtual machine.

Alternatively you could use something like remastersys which can create livecds which can (but don't have to) include personal data: [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by vinceUUUU on 2008-04-13
Hello

thanks for replying again

the GHOST idea sounds very reasonable...

i presume restoring the image file using virtualbox...would mean starting the virtual machine.... and then pointing it to the image file?

or is the restore command an option of G4L itself?....does it ask you where you want to restore the image to?

do you know it works?....restoring image files to virtual machines using G4L?

thanks

Vince.

---

### Post by vinceUUUU on 2008-04-13
Hello

yes....

don't want to labour this point too much...but are you saying that any virtual machine must firstly always have an OS installed?

or is it possible to give a virtual machine an image file of a partition of an OS...and it will thus create the machine...os

thanks

Vince.

---

### Post by ryanhaigh on 2008-04-13
I haven't used G4L specifically but did the same thing with acronis true image and it worked fine, There was some reconfiguring to do regarding x and the networking but it was quite straight forward. If you want to avoid these remastersys might be the way to go. Alternately you could install to the vm and then see if there is some easy way of replicating a vm.

---

### Post by ryanhaigh on 2008-04-13
You don't need an os installed but you will need to create the virual machine, boot from the (for me) acronis livecd, restore the image to the virtual machine hard drive and you should be good to go.

There may be a method to simply copy existing virtual machines to create new instances but I have never looked into this.

---

### Post by vinceUUUU on 2008-04-13
Hello,

yes, thanks

as i read, it appears to be simple to do what we discussed here...

Virtualbox also has a feature called snapshot....so you can snapshot a Virtual machine before you start messing around with it....if any s/w tool install goes poorly and compromises your virtual machine...you just go back to the previuos snapshot you made....(these are quik)

what i want to run is my true linux...with a copy of it...inside a virtual machine...

whenever i want to install a tool...i use the virtual machine first to try things....and before i try.....i snapshot the Vbox...

if all goes well..i then repeat the tasks inside my real linux....

but if things go poorly then i dump that Vbox session and go back to the last snapshot....and then i don't do anything else to my real linux system....

this is a good method for me...when using linux...

Vince.

---

### Post by Jose Catre-Vandis on 2008-04-13
To create replicas of existing VMs you use the clonevdi command. Assuming you have all files in the default locatrions, and say a VM called XP and you will create a replica called 2ndXP, the command line syntax is as follows:```
VBoxManage clonevdi XP 2ndXP
``` You can't do this from within the GUI. The VBoxManage command set is extensive and very useful. Have a good read of the help file :)

---

