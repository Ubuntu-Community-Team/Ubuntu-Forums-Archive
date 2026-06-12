---
title: "How do you install VMWare??"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-03
Can anyone help me out?

I have downloaded VMWare Workstation 6 Beta but I can not find how to install it, can anyone help me out please?

Ian

---

### Post by DarthWHO on 2007-05-03
tar -xvf <filename> from the Terminal

Then follow all the prompts. For this, choosing the defaults should all be fine, worked for me...

---

### Post by stalker145 on 2007-05-03
Go to the [VMWare Help area]("http://pubs.vmware.com/server1/wwhelp/wwhimpl/js/html/wwhelp.htm"), search for "Install", "Installing VMWare Server on a Linux Host", and click "Installation Steps". This will walk you through everythiing that you need to get this done. Any other questions, I'm sure you can find answers there. It looks like a great resource that I'll be using in the future ;)

If you don't feel like clicking the link, just check below for directions. Make sure to use **sudo** (and you can ignore references to the root account) when installing so everything goes in all nice and pretty.

> • Use the tar installer—Complete the following steps: 

a  Copy the tar archive to a directory on your hard drive. For example, to /tmp.
cp VMware-server-<xxxx>.tar.gz /tmp where <xxxx> is a series of numbers representing the version and build numbers. 

b  Change to the directory to which you copied the file.
cd /tmp 

c  Unpack the archive. 
tar zxf VMware-server-<xxxx>.tar.gz  

d  Change to the installation directory.
cd vmware-server-distrib 

e  Run the installation program.
./vmware-install.pl 

f  Accept the default directories for the binary files, daemon files, library files, manual files, documentation files, init directories and init scripts. 

4  Run the configuration program.
vmware-config.pl 

• If you are installing VMware Server on a Mandrake Linux host, the configuration program asks for the location of lspci. When that prompt appears, enter the following path: 
/usr/bin/lspcidrake 

• If you use the RPM installer, you must run the configuration program separately from the command line. If you install from the tar archive, the installer offers to launch the configuration program for you. Answer Yes when you see the prompt. 

Use this program to reconfigure VMware Server whenever you upgrade your kernel. It is not necessary to reinstall VMware Server after you upgrade your kernel. 
You can also use vmware-config.pl to reconfigure the networking options for VMware Server—for example, to add or remove host-only networks.
5  Press Enter to read the end user license agreement (EULA). If the Do you accept prompt doesn’t appear, press Q to get to the next prompt.  

6  Configure networking for your virtual machines.  

• If you want to use any type of networking with virtual machines, answer Yes to this prompt: Do you want networking for your virtual machines?  

Bridged networking is always enabled if you enable networking. For more information, see Bridged Networking.
• To enable NAT, answer Yes to the following prompts: 
Do you want to be able to use NAT networking in your virtual machines? 
Do you want this script to probe for an unused private subnet?  

This allows you to connect your virtual machines to an external network when you have only one IP network address on the physical network, and that address is used by the host computer. For more information, see Network Address Translation (NAT).
• To enable host-only networking, answer Yes to the following prompts: 
Do you want to be able to use host-only networking in your virtual machines? 
Do you want this script to probe for an unused private subnet?  

Host-only networking allows for networking between the virtual machine and the host operating system. For more information, see Host-Only Networking.
7  Specify the port the VMware Server Console uses when connecting to the VMware Server host remotely. Port 902 is the default port. If your site uses this port for another application—for example, ideafarm-chat uses this port—then specify a different port for the VMware Server Console to use here. To change the port later, see Changing the Port Number for VMware Server Console Connections. 

8  Specify the directory where you want to store your virtual machine files. By default, this directory is /var/lib/vmware/Virtual Machines. Make sure this location is on a large enough file system to contain the files, as the virtual disk files for each virtual machine are usually gigabytes in size. 

9  Enter your VMware Server serial number exactly as it appears (with hyphens) in the email message you received from VMware or from the reseller from whom you purchased VMware Server. When you enter the serial number, it is saved in your license file. 

The configuration program displays a message saying the configuration completed successfully. If it does not display this message, run the configuration program again.
10  When you finish, do one of the following:  

• Log off the root account.
exit  

• Install the VMware Management Interface. Go to step 3 under Installing the VMware Management Interface on a Linux Host. 

• Install the VMware Server Console. Go to step 2 under Installing the VMware Server Console on a Linux Host. 


---

