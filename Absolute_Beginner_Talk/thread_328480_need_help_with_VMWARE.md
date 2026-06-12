---
title: "need help with VMWARE"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by saadakhtar on 2006-12-30
i need help setting up vmware on my server.
i got vmware running by following the guidelines on ubuntuguide. i have also setup remote desktop to the ubuntu server using freenx. when i login to my ubuntu server using freenx i cannot start any of my virtual machines in vmware.
at first it said that i donot have proper permissions to the virtual machine folder (in my case i.e. /var/vm). i tried to change permission by using chmod 777 but the folder seems to be locked and would not let me change permissions.
i tried adding root group to my remote desktop user secondary group so that it would give my remote desktop account the necessary vmware permissions but now i am getting a new error when i start vmware-sever-console "REMOTELY" (using FREENX).



Unable to change virtual machine power state: The process exited with an error:


VMware Server Error:
VMware Server is installed, but it has not been (correctly) configured for your running kernel. To (re-)configure it, your system administrator must find and run "vmware-config.pl". For more information, please see the VMware Server documentation.

Press "Enter" to continue...
End of error message.


if i run konsole and change user to root and then run vmware by typing in "vmware-server-console" i get the  following message:

/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Xlib: connection to "unix:1017.0" refused by server
Xlib: No protocol specified

/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server-console/bin/vmware-server-console: /usr/lib/vmware-server-console/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Xlib: connection to "unix:1017.0" refused by server
Xlib: No protocol specified



can anyone please help me with this please. any help would be appreciated.

thank you in advance.

---

### Post by saadakhtar on 2006-12-31
ok.
i found the solution to my problem after some investigation. Actually i did a kernel update on my server recently but did not update the kernel headers. Actually i messed with the vmware config and then every time i wanted to start vmware i got a message that i needed to reconfigure vmware.
the simple solution:

Command to update kernel headers

**sudo apt-get install linux-headers-`uname -r`**

additionally you need to make sure that the kernel headers update everytime you run a update. for this you will need to run a program called linux-headers-***. 
*** is the package flavor that you are using. 
please run **uname -r** to find out what flavor you are using.
 It will give you something like 2.6.15-26-**k7** or 2.6.15-26-**686**

Now that you know your linux flavor please run this command:
sudo apt-get install linux-headers-***
 Replace the *** with 386, 686, k7 or server.

Hope this helps.


If you need to install VMWARE from scratch then please check [this link]("http://www.howtoforge.com/ubuntu_vmware_server") out.

Please post if you have any questions. i think i have done enough research on this topic to answer some basic questions. Here to HELP.

---

