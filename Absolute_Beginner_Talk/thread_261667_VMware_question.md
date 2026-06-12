---
title: "VMware question"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by dkline on 2006-09-20
Hello Ubuntu,
I'm new here of course and I am excited to to start discovering ubuntu OS. My first question is will ubuntu run as a VMware virtual machine on VMwares Workstaion or ESX platform?

---

### Post by NetworkGuy on 2006-09-20
Yes it will work on the latest version of Workstation.  It's not certified to work on ESX, and I don't believe it is certified to work on VI3 either.

Visit the VMTN portion and you can download several different premade virtual machines that will work on either Workstation 5.X or VMware Player.

---

### Post by dkline on 2006-09-20
Ahhh brilliant. Of course people have made VM's and you just plug them in.  Good to know.  I think I will try both. Once I get workstation going I want to do the install from CD to learn about Ubuntu, and also checkout the VM's to what people are doing with them.  I guess I do have a security question.  With a VM I guess it would be possible for people to put malicious code on them, and once it's up and running the "evil" process can kickoff.  Just a thought about the pre-made VM or is there some sort of QA before the VM is distributed?

---

### Post by andypaxo on 2006-09-20
As with any software, you have to download the image from somewhere that you think is trustworthy.
If you are really worried, it shouldn't be too hard, to make your own VM if you feel up to it by using the Ubuntu ISO and an empty disk image.

Having said that, VMWare is very secure in regards to the host computer. It should be impossible for anything you do in a virtual machine to interfere with the system it is running on.

---

### Post by dkline on 2006-09-20
I agree that the VM will not affect the host system directly. I was thinking about malicious code that would go out on a LAN. Like you said I guess it has to be trustworthy source.  Thanks all for your help. I'm going to give the CD ISO a shot.

---

