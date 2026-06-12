---
title: "OS Virtualization Software"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by svk on 2007-08-26
Hello,

I have a couple quick general questions about virtualization software (such as VMWare and VirtualBox). I am currently dual-booting Vista and Ubuntu, and I wish to be able to go both ways: access Ubuntu from within Vista and the other way around.

When I tried to set up VirtualBox in Ubuntu (with Vista as guest), it asked me to insert the Vista installation media (the bootable recovery disk). Does this imply that I will not be using the *existing* Vista installation on my hard drive, but rather a *new* installation of Vista? And does this mean that every time I shut VirtualBox off, I will lose everything I installed while running Vista as guest?

Thanks in advance for the help.

---

### Post by anewguy on 2007-08-26
I don't know if it works when using Vista, but you can set up both VirtualBox and VMWare Server to access a physical partition - i.e., an existing installation of Windows.  However, these methods come with risks of physical corruption of you partition, among others.  As you've probably seen if you've searched this forum, don't expect to be playing many games in a VM as the virtual video is not up to most games yet.

Another thing that I had problems with was the activation of Windows.  Once I had it activated in the VM, each time I went back and just booted Windows I had to reactivate - then the same again when I started Windows in a VM in Linux again.  It got to be a deadly embrace, with Microsoft in the middle wanting to know what the heck I was doing and why I needed to reactivate my Windows so often.  I eventually just got rid of my stand-alone Windows installation and went with running Windows in a VM on a virtual disk in Ubuntu.  With my processor and in particularly memory, speed isn't the same, but I can live with it for what I need to do.  Many people have posted noticing no significant decrease in performance when running Windows in a VM.

You should search this forum for posts on VMWare and VirtualBox and VMs in general, read through them, then make a decision.:)

---

### Post by Gary.M on 2007-08-26
Generally you would be running a separate installation of Windows (or Linux) in your VM. You can access data from within it via networking shares etc, and anything you save externally will be there for the other OS when you boot it normally. If you save stuff within the VM it goes onto the virtual drive and will still be there next time you run the VM...

---

### Post by Dark Star on 2007-08-26
Virtudal Box works with Vista :p

---

### Post by svk on 2007-08-26
Thank you very much for the help and advice. I'll consider very carefully, then, how I want to play the virtualization game with Windows. I guess I don't *really* need to use the existing Vista installation

I'll probably need the other direction more often -- running Ubuntu in a virtual machine while running Vista locally. Hopefully, that shouldn't be as tricky -- right?

---

### Post by swoll1980 on 2007-08-26
oppisite from my experiance vms' run way smoother on linux  than on windows. I not a fan boy either I could give a crap about linux or windows as long as there doing what I want them to do windows does somethings better, Linux does somethings better and running vms' is one of them

---

