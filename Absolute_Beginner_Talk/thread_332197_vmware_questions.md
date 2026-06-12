---
title: "vmware questions"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by fix3r on 2007-01-05
I recently installed vmware on my machine but I have been having some problems

**Problem 1**
Is there anyway to install vmware with a different internal IP like 192.168.0.* instead of 192.168.*.*? I need to be able to open a port for my machine on my router but to do that I need to have an internal ip of 192.168.0.*.

**Problem 2**
How do I get my vmware to find my external hardrive and printer drivers and such that are in my USB drives on my computer?

---

### Post by jd65pl on 2007-01-05
What vmWare are you using, are you aware there is a difference between player and server?

I'm using edgy and have followed these instructions [http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

The worked perfectly for me.

On vmserver to start connect a usb device 
[LIST=1]
[*]Edit the VM settings to include your usb controller
[*]start the virtual machine
[*]Click on "VM" on the tool bar of the window
[*]Check the box next to your usb decive
[*]It should now mount in the guest OS[/LIST]For screenshots of vm server and images of what you should be clicking you may find this link useful --> [http://jamie.dumbill.googlepages.com/ubuntuscreenshots](http://jamie.dumbill.googlepages.com/ubuntuscreenshots)

---

### Post by fix3r on 2007-01-05
Thanks for that, yes I know there is a difference. I use vmware-server.

Thanks for clearing that up, is there a way to make your internal IP what ever you want, like I posted above?

---

### Post by jd65pl on 2007-01-05
I'm not sure exactly what you mean. How did you set up your network decive in the guest OS install? Are you trying to change the IP of the host or the guest?

---

### Post by jd65pl on 2007-01-05
Assuming you are trying to change the IP address of your windows XP vmware install see this link

[http://www.microsoft.com/windowsxp/using/networking/expert/russel_02june17.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/russel_02june17.mspx)

---

### Post by techstop on 2007-01-05
> **fix3r said:**
> Thanks for that, yes I know there is a difference. I use vmware-server.

Thanks for clearing that up, is there a way to make your internal IP what ever you want, like I posted above?

OK. Start vmware server, select the guest os of choice, then click the "VM" menu in the vmware-server window. Then click settings, choose your network device, and then you can choose from;

-bridged
-NAT
-host-only
-custom

I use bridged for my VM's. This means that the network interface uses your existing network setup. ie. my home network uses the 192.168.0.0 network, meaning that my VM's do as well.

So, choose the setup that suits you best, then set your network preferences appropriately from within the guest OS. I have a Windows XP VM, so I set it to "use the following ip address" within the network connections properties rather than "obtain an IP address automatically", but it's up to you and your network how you configure yours.

---

### Post by fix3r on 2007-01-05
Thanks everyone for their help. When I go to download the vmware server i'll try those out.

---

### Post by techstop on 2007-01-05
> **fix3r said:**
> Thanks everyone for their help. When I go to download the vmware server i'll try those out.

I thought you said you were already using it?

[http://ubuntuforums.org/showpost.php?p=1972832&postcount=3](http://ubuntuforums.org/showpost.php?p=1972832&postcount=3)

---

### Post by fix3r on 2007-01-05
> **techstop said:**
> I thought you said you were already using it?

[http://ubuntuforums.org/showpost.php?p=1972832&postcount=3](http://ubuntuforums.org/showpost.php?p=1972832&postcount=3)

Well, I just reformatted to xubuntu so now I have to try it again.

---

