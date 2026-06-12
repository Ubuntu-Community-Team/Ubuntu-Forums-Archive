---
title: "Chroot Question [ from a LiveCD ]"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by habtish on 2007-09-01
Hello,

In previous [[COLOR=Red]posts[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=318878")I had stated my keyboard problem and BIOS not being configured for Legacy USB support. This in a nutshell meant that I can not dual boot anymore and can only boot to the default OS in the Grub entry. I had accepted this and have happily been using Ubuntu for a while now

Considering limited support for web cams on Linux and the the absence of a Video chat option in Skype are forcing me to need to use windows if I am to Video conference with my family back home.

Now, if I do need to boot into  windows, my only option is to change the default OS entry in Grub (tried using a grub-reboot option which was [COLOR=Red][disastrous]("http://ubuntuforums.org/showthread.php?t=335805")[/COLOR]) Of course I would like to come back to using Ubuntu which means that I have to load a Live CD and edit my Grub entry.

My assumption is I would need to chroot to be able to make changes to the grub on my hard disk. **How can I do this correctly so I can chroot, change the default OS in Grub back to Ubuntu and save the changes from a LIve CD?**

I would appreciate any help on this as I am not even considering switching my default OS to XP without absolutely being sure I can undo it.

Hope the post wasn't too long, please follow links to see previous posts on the broken PS/2 port issue, in case anyone wants to throw out an idea that I have already tired.

TIA~~

---

### Post by SOULRiDER on 2007-09-01
Theres no need to chroot. Just mount the partition where the grub config (the menu.lst fle) is located make the changes necesary, save and reboot.

If you still think you need to chroot then in a terminal type:

```
chroot <root partition>
```
being <root partition> the partition where you have ubuntu installed.

---

### Post by habtish on 2007-09-01
How would I be able to make changes to the local Grub entry using a live cd without having to authenticate myself? I was assuming it just wouldn't let me make changes to the file and save without having write permissions to it.

---

### Post by TryMe on 2007-09-01
when you boot from a live cd you are root. 

Also if you have the cpu and memory requirements VMware server is a good option for web cams and other applications that can't be used under linux.  I think VMware would be a more flexible solution for you.

---

### Post by habtish on 2007-09-03
> **TryMe said:**
>   I think VMware would be a more flexible solution for you.

I have tried running a VMware server in the past and could not get it to work. For some reason I had trouble getting it to recognize ISO images. Tried running Kubuntu and Xubuntu as the guest OS and no luck. I was following some HowTos on VMware but could not get it to work for me :(

---

### Post by tszanon on 2007-09-03
> **TryMe said:**
> when you boot from a live cd you are root.
I don't think so. When you boot from the live cd, you are 'ubuntu'. But you don't have to type any password to use sudo.

---

### Post by dansco on 2007-09-03
> **habtish said:**
> I have tried running a VMware server in the past and could not get it to work. For some reason I had trouble getting it to recognize ISO images. Tried running Kubuntu and Xubuntu as the guest OS and no luck. I was following some HowTos on VMware but could not get it to work for me :(

virtualbox might be a better virtual machine for you to try

get it here

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by TryMe on 2007-09-03
Sorry to hear about vmware issue. Was the problem getting vmware installed or getting a vm to boot from a cd. If booting from an iso is the issue try this:
inside VMware, go to VM -> Settings and click on CD/DVD drive. Here, you will seen the "Connection" properties for this device. By default, you are  using the "physical drive". To change that and use a disk image, click on Use ISO Image and brows to the image you want.

virtualbox is also a good option but I had issues with usb devices and setting up bridged networking. It was a while ago so they probably fix those bugs by now.

---

