---
title: "Pulling my hair out - Nvidia chipset drivers still not installing"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by BIZKeT on 2006-07-11
First, my problem.

I have an Asus A8N-VM CSM mobo that uses the GeForce 6150 northbridge chipset with the nForce 430 MCP southbridge.

I have been trying to install the Linux chipset drivers (located at [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)), but am getting flumuxed at every step.

I have figured out how to get the system running outside of Gnome so that I no longer get the 'shut down X Server' message, but I then get a Kernel tree error. I found a page that was linked on someones sig file here and followed the directions on it. It was taking me through re-compiling a kernel. Problem was it seemed like it was old directions, and when I modified some of the lines to fit the kernel version I was using, I would get 'no such file' messages.

Where I am at now is that I seem to have a partially compiled kernel and no drivers installed.

I get the impression that if I could get the command line to recognize my usb connected cable modem that it wouldn't be an issue. It appears to try to connect to the internet to get an installer from the Nvidia site but it can not find eth1 (the usb modem) Sadly, I don't have a pci ethernet card to put in the system, and the onboard one needs the drivers installed to work. ](*,) I have looked in Synaptic even, but all I see in there are graphics drivers.

Can anyone give me detailed directions for installing the chipset drivers onto my system? When I get home tonight I am just going to wipe the drive and reinstall fresh with Drake. Either by telling me how to get command line at boot to recognize the usb modem or by coming over and kicking the 'puter until it finally gives ;) 

Thank you all very much for the help you have given me thus far.

BIZKeT

---

### Post by inf0c0m on 2006-07-11
> **BIZKeT said:**
> First, my problem.

I have an Asus A8N-VM CSM mobo that uses the GeForce 6150 northbridge chipset with the nForce 430 MCP southbridge.

I have been trying to install the Linux chipset drivers (located at [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)), but am getting flumuxed at every step.

I have figured out how to get the system running outside of Gnome so that I no longer get the 'shut down X Server' message, but I then get a Kernel tree error. I found a page that was linked on someones sig file here and followed the directions on it. It was taking me through re-compiling a kernel. Problem was it seemed like it was old directions, and when I modified some of the lines to fit the kernel version I was using, I would get 'no such file' messages.

Where I am at now is that I seem to have a partially compiled kernel and no drivers installed.

I get the impression that if I could get the command line to recognize my usb connected cable modem that it wouldn't be an issue. It appears to try to connect to the internet to get an installer from the Nvidia site but it can not find eth1 (the usb modem) Sadly, I don't have a pci ethernet card to put in the system, and the onboard one needs the drivers installed to work. ](*,) I have looked in Synaptic even, but all I see in there are graphics drivers.

Can anyone give me detailed directions for installing the chipset drivers onto my system? When I get home tonight I am just going to wipe the drive and reinstall fresh with Drake. Either by telling me how to get command line at boot to recognize the usb modem or by coming over and kicking the 'puter until it finally gives ;) 

Thank you all very much for the help you have given me thus far.

BIZKeT
i ran through these instructions:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

and didnt seem to have many problems? where were these instructions you pulled from?

---

### Post by andyman on 2006-07-11
Can you not install them from synaptic after installing the restricted kernel module?  that way you dont have to recompile your kernel...

---

### Post by BIZKeT on 2006-07-11
> **inf0c0m said:**
> i ran through these instructions:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

and didnt seem to have many problems? where were these instructions you pulled from?

As far as I can tell, those instructions are for the video card drivers, not the chipset drivers. Am I incorrect?

---

### Post by BIZKeT on 2006-07-11
> **andyman said:**
> Can you not install them from synaptic after installing the restricted kernel module?  that way you dont have to recompile your kernel...

Which one would I install? There were about 9 different things in Synaptic when I searched for Nvidia, and all of them seemed to be dealing with just graphics drivers. Which one would you suggest I use?

---

### Post by BIZKeT on 2006-07-11
Sorry to bump but this is driving me nuts.

---

### Post by skale on 2006-07-11
If you asked me, I'd say just reinstall ubuntu fresh and then follow the directions exactly. Of course, backup everything. Maybe then you won't lose all your hair.;)

---

### Post by BIZKeT on 2006-07-11
> **skale said:**
> If you asked me, I'd say just reinstall ubuntu fresh and then follow the directions exactly. Of course, backup everything. Maybe then you won't lose all your hair.;)

That is what I am trying to get at. Which directions? I have not found _any_ directions for installing the chipset drivers except for old ones (two kernels ago it looks like) that give error messages when I follow them exactly. All of the directions I have found other than that are for the video card drivers. I am not trying to install the video card drivers so they do no good for me.

Edit -
I may be confusing some folks. By chipset drivers I mean the drivers for the motherboard chipset, the ones that control not only the onboard video, but the onboard nic, audio, etc.

---

### Post by keith whitehouse on 2006-07-12
hi bizket,

have you tried "Google" search asus chipset drivers

best regards keith

---

### Post by brentoboy on 2006-07-12
with a fresh ubuntu install, what exactly doenst work?

---

### Post by BIZKeT on 2006-07-12
> **keith whitehouse said:**
> hi bizket,

have you tried "Google" search asus chipset drivers

best regards keith

First thing I did.

---

### Post by BIZKeT on 2006-07-12
> **brentoboy said:**
> with a fresh ubuntu install, what exactly doenst work?

The onboard network was not working.

Thankfully I got it installed _finally_. 

I tried a differnt file they had available and it worked fine.

Now to get rar functionality...

---

