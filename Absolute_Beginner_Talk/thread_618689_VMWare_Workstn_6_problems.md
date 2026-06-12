---
title: "VMWare Workstn 6 problems"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by malty on 2007-11-20
Installed trial version of  VMWare workstation 6.
Installed suse 10.2.
Workstation 6 would make a first rate hospital isolation ward, nothing gets in or out.
No internet..."/dev/vmnet8: no such file" I have tried all available options...NAT, etc...no luck
Unable to contact any file on gutsy host.
I set up workstation as per VM installation instructions for Suse 10.2.
Today I set up another virtual machine (after trying and failing to delete the first ("you cannot delete a template") and attempted to install susie 10.3 (using the disc from linux magazine) using both the disc and then the iso (I know the disc is ok) no luck, got as far as selecting language, in text installer, and then tried again, got as far as installation screen...lockup again.
Obviously I joined VM forum but with 29 members......
Do you think it is worth the aggro or is there a better alternative, I very much doubt that I would buy this product now, my reason for trying it is that the free version will not support a distro that supports Maya 8 (Red Hat) If VM Workstation had worked I would have bought this.
                                                              Malty

---

### Post by schorsch on 2007-11-20
What about trying virtualbox available from [here]("http://www.virtualbox.org")? The OSE Edition is available in the Gutsy repos but lacks USB support so you should use the binaries from the official website. And I installed OpenSuSE 10.3 in virtualbox a few days before ....

---

### Post by AlanRogers on 2007-11-20
Why are you using VMWare Workstation? Do you need it's additional functionality? It's a pay-for product, so far as I can see, and VMWare Server, which is free, will I suspect give you what you're looking for, without the complications. 
 
I'm been using Linux for less than a year, installed VMWare Server this afternoon and have successfully set Windows XP and Linux Mint 2.2 virtual machines plus run gOS from a Live CD, all with full internet and network access.
 
It may be fair and more complete to advise that I'm using a DSL router running DHCP and the virtual machines are all running in Bridged mode. It takes a great deal of configuration out of the equation.

---

### Post by malty on 2007-11-21
Thanks for response. The reasons for trying workstation were explained in my post. I did first try the free server and could not install Susie 10.2. When I checked into the VM documentation I found the list of distros that would run on each product, the Red Hat distro I need, they declare, will not run on the free server, hence my trial of the workstation (on the distros I had to hand.)
       I do not have an issue with buying software if it is what will do the job.
I will try Virtualbox 1.5.2 but looking at their installation info I suspect  that is not straightforward, I am at the bottom of the Linux learning curve, my previous experience is of Unix from the early nineties and that was as an end user of the engineering applications that ran on Unix, not the operating system.
                                                             Regards and thanks again , Malty

---

